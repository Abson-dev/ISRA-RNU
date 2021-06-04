RNU data wrangling
==================

``` r
library(readxl)
library(dplyr)
library(reticulate) #for python
```

``` python
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd 
import seaborn as sns
```

``` r
RNU_DAGANA_LINGUERE <- read_excel("C:/Users/DELLDRAMOMO/Desktop/ISRA-RNU/Project datasets/data/RNU datasets/Donnee_etude_inclusion_populations_pastorales_dept_DAGANA-LINGUERE.xlsx") %>% 
  dplyr::distinct()

RNU_RANEROU <- read_excel("C:/Users/DELLDRAMOMO/Desktop/ISRA-RNU/Project datasets/data/RNU datasets/Donnee_etude_inclusion_populations_pastorales_dept_RANEROU.xlsx")%>% 
  dplyr::distinct()



possession <- function(x) (ifelse(x==0,"Non","Oui"))
df_RNU_DAGANA_LINGUERE <-RNU_DAGANA_LINGUERE %>% 
  dplyr::filter(nom_commune_men %in% c("VELINGARA","TESSEKRE FORAGE","MBANE","THIEL")) %>% 
  dplyr::select(nom_region_men,nom_departement_men,nom_commune_men,milieu_de_residence,dplyr::starts_with("m14")) %>% 
  dplyr::mutate_at(vars(dplyr::starts_with("m14_")),as.factor) %>% 
  dplyr::mutate_at(vars(dplyr::starts_with("m14_")),possession) %>% 
  dplyr::mutate(animaux=purrr::pmap(list(m14a,m14b,m14c,m14d,m14e,m14f,m14g,m14h),sum,na.rm=T))

possession <- function(x) (ifelse(x==1,"Non","Oui"))
df_RNU_RANEROU<-RNU_RANEROU %>% 
  dplyr::filter(nom_commune_men %in% c("VELINGARA","TESSEKRE FORAGE","MBANE","THIEL")) %>% 
  dplyr::select(nom_region_men,nom_departement_men,nom_commune_men,milieu_de_residence,dplyr::starts_with("m14")) %>% 
  dplyr::select(nom_region_men,nom_departement_men,nom_commune_men,milieu_de_residence,dplyr::starts_with("m14")) %>% 
  dplyr::mutate_at(vars(dplyr::starts_with("m14_")),as.factor) %>% 
  dplyr::mutate_at(vars(dplyr::starts_with("m14_")),possession) %>% 
  dplyr::mutate(animaux=purrr::pmap(list(m14a,m14b,m14c,m14d,m14e,m14f,m14g,m14h),sum,na.rm=T))

df<-rbind(df_RNU_DAGANA_LINGUERE,df_RNU_RANEROU)

df <- df %>% 
  dplyr::mutate(possession = ifelse(animaux>0,"Oui","Non"))
```

``` python
data=r.df
ax=data["possession"].value_counts().plot(kind = 'pie', autopct='%1.2f%%', figsize=(10, 10))
ax.set_title('Proportion de ménages possèdant des animaux')
ax.set_aspect(1) # make it round 
ax.set_ylabel('') # remove default 
fig = ax.figure 
fig.set_size_inches(8, 8)
plt.show()
```

<img src="RNU-data-wrangling_files/figure-markdown_github/animaux-1.png" width="768" />

``` python
data=r.df
ax=data["m14_1"].value_counts().plot(kind = 'pie', autopct='%1.2f%%', figsize=(10, 10))
ax.set_title('Proportion de ménages possèdant des bovins (Bœufs, Vaches)')
ax.set_aspect(1) # make it round 
ax.set_ylabel('') # remove default 
fig = ax.figure 
fig.set_size_inches(8, 8)
plt.show()
```

<img src="RNU-data-wrangling_files/figure-markdown_github/bovins-1.png" width="768" />

``` python
data=r.df
ax=data["m14_2"].value_counts().plot(kind = 'pie', autopct='%1.2f%%', figsize=(10, 10))
ax.set_title('Proportion de ménages possèdant des caprins')
ax.set_aspect(1) # make it round 
ax.set_ylabel('') # remove default 
fig = ax.figure 
fig.set_size_inches(8, 8)
plt.show()
```

<img src="RNU-data-wrangling_files/figure-markdown_github/caprins-1.png" width="768" />

``` python
data=r.df
ax=data["m14_3"].value_counts().plot(kind = 'pie', autopct='%1.2f%%', figsize=(10, 10))
ax.set_title('Proportion de ménages possèdant des ovins')
ax.set_aspect(1) # make it round 
ax.set_ylabel('') # remove default 
fig = ax.figure 
fig.set_size_inches(8, 8)
plt.show()
```

<img src="RNU-data-wrangling_files/figure-markdown_github/ovins-1.png" width="768" />

``` python
data=r.df
ax=data["m14_4"].value_counts().plot(kind = 'pie', autopct='%1.2f%%', figsize=(10, 10))
ax.set_title('Proportion de ménages possèdant des volailles')
ax.set_aspect(1) # make it round 
ax.set_ylabel('') # remove default 
fig = ax.figure 
fig.set_size_inches(8, 8)
plt.show()
```

<img src="RNU-data-wrangling_files/figure-markdown_github/volailles-1.png" width="768" />

``` python
data=r.df
ax=data["m14_5"].value_counts().plot(kind = 'pie', autopct='%1.2f%%', figsize=(10, 10))
ax.set_title('Proportion de ménages possèdant des porcins')
ax.set_aspect(1) # make it round 
ax.set_ylabel('') # remove default 
fig = ax.figure 
fig.set_size_inches(8, 8)
plt.show()
```

<img src="RNU-data-wrangling_files/figure-markdown_github/porcins-1.png" width="768" />

``` python
data=r.df
ax=data["m14_6"].value_counts().plot(kind = 'pie', autopct='%1.2f%%', figsize=(10, 10))
ax.set_title('Proportion de ménages possèdant des chevaux/juments')
ax.set_aspect(1) # make it round 
ax.set_ylabel('') # remove default 
fig = ax.figure 
fig.set_size_inches(8, 8)
plt.show()
```

<img src="RNU-data-wrangling_files/figure-markdown_github/chevaux-1.png" width="768" />

``` python
data=r.df
ax=data["m14_7"].value_counts().plot(kind = 'pie', autopct='%1.2f%%', figsize=(10, 10))
ax.set_title('Proportion de ménages possèdant des ânes')
ax.set_aspect(1) # make it round 
ax.set_ylabel('') # remove default 
fig = ax.figure 
fig.set_size_inches(8, 8)
plt.show()
```

<img src="RNU-data-wrangling_files/figure-markdown_github/anes-1.png" width="768" />
