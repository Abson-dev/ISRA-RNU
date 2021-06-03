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
```
