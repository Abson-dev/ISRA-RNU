RGPH 2013 Analysis
------------------

``` r
library(readr)
library(dplyr)
library(ggplot2)
library(reticulate) #for python
```

``` python
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd 
import seaborn as sns
```

``` r
POP_RGPH_2013_ANSD_LING_RAR_DAGANA <- read_delim("C:/Users/DELLDRAMOMO/Desktop/ISRA-RNU/Project datasets/data/RGPH 2013 ANSD/POP(RGPH 2013 ANSD)_LING_RAR_DAGANA.csv", 
    ";", escape_double = FALSE, trim_ws = TRUE) %>% dplyr::distinct()
```

``` r
Population_Pastorale<-POP_RGPH_2013_ANSD_LING_RAR_DAGANA %>% 
  dplyr::filter(`3@COMMUNE` %in% c("VELINGARA","TESSEKRE FORAGE","MBANE","THIEL"))

write.csv2(Population_Pastorale,"Population_Pastorale.csv",row.names = F)
```

``` r
Population_Pastorale %>%
 filter(!(`11@OBSERVATIONS` %in% "Non habit<e9>")) %>%
 ggplot() +
 aes(x = `1@REGION`, weight = `6@MENAGES`) +
 geom_bar(fill = "#08306b") +
 # geom_label(data=Population_Pastorale,aes(x=`1@REGION`,y=`6@MENAGES`, label=paste0(round(`6@MENAGES`,0),"")),size=2)+
 labs(x = "Régions", y = "Nombre de ménages", title = "Nombre de ménage par Région", caption = "Source: ANSD,RGPH 2013") +
 ggthemes::theme_stata()
```

![](analysis_files/figure-markdown_github/region-1.png)

``` r
#esquisser(Population_Pastorale)



Population_Pastorale %>%
 filter(!(`11@OBSERVATIONS` %in% "Non habit<e9>")) %>%
 ggplot() +
 aes(x = `2@DEPARTEMENT`, weight = `6@MENAGES`) +
 geom_bar(fill = "#35b779") +
 labs(x = "Départements", y = "Nombre de ménages", title = "Nombre de ménages par départements", caption = "Source: ANSD, RGPH 2013") +
 ggthemes::theme_economist()
```

![](analysis_files/figure-markdown_github/departement-1.png)

``` r
Population_Pastorale %>%
 filter(!(`11@OBSERVATIONS` %in% "Non habit<e9>")) %>%
 ggplot() +
 aes(x = `3@COMMUNE`, weight = `6@MENAGES`) +
 geom_bar(fill = "#006d2c") +
 labs(x = "Communes", y = "Nombre de ménages (RGPH 2013)", title = "Nombre de ménage par communes", caption = "Source :ANSD, RGPH 2013") +
 ggthemes::theme_stata()
```

![](analysis_files/figure-markdown_github/commune-1.png)

``` r
menage<-Population_Pastorale %>% 
  dplyr::select(`1@REGION`,`2@DEPARTEMENT`,`3@COMMUNE`,`6@MENAGES`)%>% 
  dplyr::group_by(`1@REGION`,`2@DEPARTEMENT`,`3@COMMUNE`) %>% 
  dplyr::mutate(Total=sum(`6@MENAGES`,na.rm = T)) %>% 
  dplyr::select(`1@REGION`,`2@DEPARTEMENT`,`3@COMMUNE`,Total) %>% dplyr::arrange(Total) %>% dplyr:: distinct()

names(menage)<-c("REGION","DEPARTEMENT","COMMUNE","MENAGES")
```

| REGION      | DEPARTEMENT |     COMMUNE     | MENAGES |
|:------------|:-----------:|:---------------:|--------:|
| SAINT-LOUIS |   DAGANA    |      MBANE      |    2543 |
| MATAM       |   RANEROU   |    VELINGARA    |    1964 |
| LOUGA       |  LINGUERE   |      THIEL      |    1315 |
| LOUGA       |  LINGUERE   | TESSEKRE FORAGE |    1177 |

``` python
#data=r.menage
# data["COMMUNE"].value_counts().plot(kind = 'pie', autopct='%1.2f%%', figsize=(10, 10))
# plt.show()

s = pd.Series(data=[1177,1315,1964,2543], 
 index =  ['TESSEKRE FORAGE', 'THIEL', 'VELINGARA','MBANE']) 
ax = s.plot.pie(autopct='%.1f') 
# followed by the standard plot output ... 
ax.set_title('Proportion de ménages par commune') 
ax.set_aspect(1) # make it round 
ax.set_ylabel('') # remove default 
fig = ax.figure 
fig.set_size_inches(8, 8) 
#fig.savefig('filename.png', dpi=125) 
#plt.close(fig)
plt.show()
```

<img src="analysis_files/figure-markdown_github/pie-1.png" width="768" />

``` r
df<-Population_Pastorale %>% 
  dplyr::select(`1@REGION`,`2@DEPARTEMENT`,`3@COMMUNE`,`7@QUARTIERS-VILLAGES`)%>% 
  dplyr::group_by(`1@REGION`,`2@DEPARTEMENT`,`3@COMMUNE`,`7@QUARTIERS-VILLAGES`) %>% 
  dplyr::mutate(Village=n()) %>% dplyr::distinct() %>% 
  dplyr::group_by(`1@REGION`,`2@DEPARTEMENT`,`3@COMMUNE`) %>% dplyr::mutate(Village=sum(Village,na.rm = T))  %>% 
  dplyr::select(`1@REGION`,`2@DEPARTEMENT`,`3@COMMUNE`,Village) %>% dplyr::distinct()
```

| REGION      | DEPARTEMENT |     COMMUNE     | VILLAGES |
|:------------|:-----------:|:---------------:|---------:|
| MATAM       |   RANEROU   |    VELINGARA    |       81 |
| LOUGA       |  LINGUERE   | TESSEKRE FORAGE |       74 |
| LOUGA       |  LINGUERE   |      THIEL      |       65 |
| SAINT-LOUIS |   DAGANA    |      MBANE      |       47 |

``` python
s = pd.Series(data=[74,65,81,47], 
 index =  ['TESSEKRE FORAGE', 'THIEL', 'VELINGARA','MBANE']) 
ax = s.plot.pie(autopct='%.1f') 
# followed by the standard plot output ... 
ax.set_title('Proportion de villages par commune') 
ax.set_aspect(1) # make it round 
ax.set_ylabel('') # remove default 
fig = ax.figure 
fig.set_size_inches(8, 8) 
#fig.savefig('filename.png', dpi=125) 
#plt.close(fig)
plt.show()
```

<img src="analysis_files/figure-markdown_github/pievillage-1.png" width="768" />
