Sampling analysis
=================

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
```

``` r
df_sta<-Population_Pastorale %>% 
  dplyr::select(`1@REGION`,`2@DEPARTEMENT`,`3@COMMUNE`,`6@MENAGES`)%>% 
  dplyr::group_by(`1@REGION`,`2@DEPARTEMENT`,`3@COMMUNE`) %>% 
  dplyr::mutate(Total=sum(`6@MENAGES`,na.rm = T)) %>% 
  select(`1@REGION`,`2@DEPARTEMENT`,`3@COMMUNE`,Total) %>% distinct()

df_sta<-df_sta %>% 
  dplyr::mutate(prop=round(Total*100/6999,0),
                Echantillon=502,
                MENAGES=round(prop*Echantillon/100,0))
```

| REGION      | DEPARTEMENT |     COMMUNE     | MENAGES |
|:------------|:-----------:|:---------------:|--------:|
| SAINT-LOUIS |   DAGANA    |      MBANE      |     181 |
| MATAM       |   RANEROU   |    VELINGARA    |     141 |
| LOUGA       |  LINGUERE   |      THIEL      |      95 |
| LOUGA       |  LINGUERE   | TESSEKRE FORAGE |      85 |

``` python
s = pd.Series(data=[85,95,141,181], 
 index =  ['TESSEKRE FORAGE', 'THIEL', 'VELINGARA','MBANE']) 
ax = s.plot.pie(autopct='%.1f') 
# followed by the standard plot output ... 
ax.set_title('Proportion de ménages à tirer par commune') 
ax.set_aspect(1) # make it round 
ax.set_ylabel('') # remove default 
fig = ax.figure 
fig.set_size_inches(8, 8) 
#fig.savefig('filename.png', dpi=125) 
#plt.close(fig)
plt.show()
```

<p align="center">
  <img src="sampling_files/figure-markdown_github/echantillon-1.png" width="500" />
</p>


``` r
Echantillon_Population_Pastorale<-Population_Pastorale %>% 
  dplyr::mutate(Proba=ifelse(`3@COMMUNE`=="MBANE",`6@MENAGES`/2543,
                             ifelse(`3@COMMUNE`=="TESSEKRE FORAGE",`6@MENAGES`/1177,
                                    ifelse(`3@COMMUNE`=="THIEL",`6@MENAGES`/1315,
                                           ifelse(`3@COMMUNE`=="VELINGARA",`6@MENAGES`/1964,`6@MENAGES`))))
  )
```

``` r
Echantillon_Population_Pastorale<-Echantillon_Population_Pastorale %>% 
  dplyr::mutate(n=ifelse(`3@COMMUNE`=="MBANE",Proba *181,
                             ifelse(`3@COMMUNE`=="TESSEKRE FORAGE",Proba *85,
                                    ifelse(`3@COMMUNE`=="THIEL",Proba *95,
                                           ifelse(`3@COMMUNE`=="VELINGARA",Proba *141,`6@MENAGES`))))
  ) %>% 
  dplyr::mutate(n=round(n,0)) %>% 
  dplyr::filter(n>0)

# write.csv2(Echantillon_Population_Pastorale,"EchantillonVillage.csv",row.names = F)
```

``` r
df<-Echantillon_Population_Pastorale %>% 
  dplyr::select(`1@REGION`,`2@DEPARTEMENT`,`3@COMMUNE`,`7@QUARTIERS-VILLAGES`)%>% 
  dplyr::group_by(`1@REGION`,`2@DEPARTEMENT`,`3@COMMUNE`,`7@QUARTIERS-VILLAGES`) %>% 
  dplyr::mutate(Village=n()) %>% dplyr::distinct() %>% 
  dplyr::group_by(`1@REGION`,`2@DEPARTEMENT`,`3@COMMUNE`) %>% dplyr::mutate(Village=sum(Village,na.rm = T))  %>% 
  dplyr::select(`1@REGION`,`2@DEPARTEMENT`,`3@COMMUNE`,Village) %>% dplyr::distinct()
```

| REGION      | DEPARTEMENT |     COMMUNE     | VILLAGES |
|:------------|:-----------:|:---------------:|---------:|
| MATAM       |   RANEROU   |    VELINGARA    |       69 |
| LOUGA       |  LINGUERE   | TESSEKRE FORAGE |       56 |
| LOUGA       |  LINGUERE   |      THIEL      |       52 |
| SAINT-LOUIS |   DAGANA    |      MBANE      |       43 |

``` python
s = pd.Series(data=[56,52,69,43], 
 index =  ['TESSEKRE FORAGE', 'THIEL', 'VELINGARA','MBANE']) 
ax = s.plot.pie(autopct='%.1f') 
# followed by the standard plot output ... 
ax.set_title('Proportion de villages tirés par commune') 
ax.set_aspect(1) # make it round 
ax.set_ylabel('') # remove default 
fig = ax.figure 
fig.set_size_inches(8, 8) 
#fig.savefig('filename.png', dpi=125) 
#plt.close(fig)
plt.show()
```

<p align="center">
  <img src="sampling_files/figure-markdown_github/village-1.png" width="500" />
</p>


``` r
ggplot(data=df_sta,aes(x = `3@COMMUNE`, y = MENAGES)) +
 geom_bar(stat="identity",position = "dodge", fill = "#0d0887") +
  geom_text(aes(label=MENAGES), position=position_dodge(width=0.9), hjust=-0.25)+
 labs(x = "Commune", y = "Nombre de ménages", title = "Nombre de ménages à tirer par commune") +
 coord_flip() +
 ggthemes::theme_igray()+
 ylim(0L, 200L)
```

<p align="center">
  <img src="sampling_files/figure-markdown_github/commune-1.png" width="500" />
</p>


``` r
  ggplot(data=df_sta %>% 
  dplyr::group_by(`2@DEPARTEMENT`) %>% 
  dplyr::mutate(MENAGES=sum(MENAGES)) %>% 
  dplyr::select(`2@DEPARTEMENT`,MENAGES) %>% 
  dplyr::distinct(),aes(x = `2@DEPARTEMENT`, y = MENAGES)) +
 geom_bar(stat="identity",position = "dodge", fill = "#0d0887") +
  geom_text(aes(label=MENAGES), position=position_dodge(width=0.9), hjust=-0.25)+labs(x = "Département", y = "Nombre de ménages", title = "Nombre de ménages à tirer par département") +
 coord_flip() +
 ggthemes::theme_par()+
 ylim(0L, 200L)
```

<p align="center">
  <img src="sampling_files/figure-markdown_github/departement-1.png" width="500" />
</p>


``` r
ggplot(data=df_sta %>% 
  dplyr::group_by(`1@REGION`) %>% 
  dplyr::mutate(MENAGES=sum(MENAGES)) %>% 
  dplyr::select(`1@REGION`,MENAGES) %>% 
  dplyr::distinct(),aes(x = `1@REGION`, y = MENAGES)) +
 geom_bar(stat="identity",position = "dodge", fill = "#0d0887") +
  geom_text(aes(label=MENAGES), position=position_dodge(width=0.9), hjust=-0.25) +
 labs(x = "Région", y = "Nombre de ménages", title = "Nombre de ménages à tirer par région") +
 coord_flip() +
 ggthemes::theme_stata()
```

<p align="center">
  <img src="sampling_files/figure-markdown_github/region-1.png" width="500" />
</p>

