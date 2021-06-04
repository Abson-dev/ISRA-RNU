RNU data wrangling
==================

``` r
library(readxl)
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
library(reticulate) #for python
```

    ## Warning: package 'reticulate' was built under R version 4.0.4

``` python
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd 
import seaborn as sns
```

``` r
RNU_DAGANA_LINGUERE <- read_excel("C:/Users/DELLDRAMOMO/Desktop/ISRA-RNU/Project datasets/data/RNU datasets/Donnee_etude_inclusion_populations_pastorales_dept_DAGANA-LINGUERE.xlsx") %>% 
  dplyr::distinct()
```

    ## Warning in strptime(x, format, tz = tz): unable to identify current timezone 'T':
    ## please set environment variable 'TZ'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in I2983 / R2983C9: got 'C'EST UN CHEMINO'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K4595 / R4595C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in Z4650 / R4650C26: got 'PIUT'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K5115 / R5115C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in P5262 / R5262C16: got 'VIDE'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K6384 / R6384C11: got 'NE SAIT PAS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K6394 / R6394C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL6396 / R6396C64: got '34 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K6460 / R6460C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K6519 / R6519C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K6567 / R6567C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in T6578 / R6578C20: got 'CHANDELLE'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL6590 / R6590C64: got '237 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL6596 / R6596C64: got '2 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL6597 / R6597C64: got '23 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL6611 / R6611C64: got '23 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL6613 / R6613C64: got '2 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL6631 / R6631C64: got '7 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in T6635 / R6635C20: got 'ELLE ALLUME RIEN'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL6672 / R6672C64: got '247 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K6905 / R6905C11: got 'R'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in P6905 / R6905C16: got 'NON'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in T6905 / R6905C20: got 'R'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in V6905 / R6905C22: got 'R'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in X6905 / R6905C24: got 'R'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in Z6905 / R6905C26: got 'R'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in P6927 / R6927C16: got 'BARAQUE'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL6996 / R6996C64: got '2 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K7052 / R7052C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K7082 / R7082C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K7166 / R7166C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K7172 / R7172C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL7188 / R7188C64: got '3 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K7203 / R7203C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K7241 / R7241C11: got 'NE SAIT PAS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K7268 / R7268C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL7270 / R7270C64: got '2 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL7279 / R7279C64: got '7 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL7289 / R7289C64: got '7 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL7290 / R7290C64: got '236 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL7291 / R7291C64: got '237 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in I7419 / R7419C9: got 'NEANT'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K7419 / R7419C11: got 'NON'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in P7419 / R7419C16: got 'N'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in T7419 / R7419C20: got 'N'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in V7419 / R7419C22: got 'N'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in X7419 / R7419C24: got 'NTR'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in Z7419 / R7419C26: got 'NTR'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL7488 / R7488C64: got '36 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in P7536 / R7536C16: got 'BARAQUE'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in Z7646 / R7646C26: got 'AL'USINE'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in I7690 / R7690C9: got 'CHAMBRE DETRUIS PAR'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in P8064 / R8064C16: got 'BARAQUE'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in CK8117 / R8117C89: got '5 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8144 / R8144C11: got 'NON LOTISSE'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8226 / R8226C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in CK8290 / R8290C89: got '7 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8355 / R8355C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8367 / R8367C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8383 / R8383C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8391 / R8391C11: got 'NE SAIT PAS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8398 / R8398C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in V8455 / R8455C22: got 'AUCUNE'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8463 / R8463C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8497 / R8497C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in V8500 / R8500C22: got 'MENAGE ISOLE'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8516 / R8516C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8531 / R8531C11: got 'NE SAIT PAS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8537 / R8537C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8602 / R8602C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8608 / R8608C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8611 / R8611C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8691 / R8691C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8703 / R8703C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8751 / R8751C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8820 / R8820C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8847 / R8847C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8892 / R8892C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8906 / R8906C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in V8917 / R8917C22: got 'PRIVEE'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8944 / R8944C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8960 / R8960C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8962 / R8962C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8987 / R8987C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K8998 / R8998C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9036 / R9036C11: got 'NE SAIT PAS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL9050 / R9050C64: got '2347 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in V9052 / R9052C22: got 'MANGE CHEZ SA MERE'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9056 / R9056C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9068 / R9068C11: got 'NE SAIT PAS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9077 / R9077C11: got 'NE SAIT PAS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9103 / R9103C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9140 / R9140C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9146 / R9146C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9157 / R9157C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9247 / R9247C11: got 'NE SAIT PAS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9327 / R9327C11: got 'NE SAIT PAS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9344 / R9344C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9384 / R9384C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9407 / R9407C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9469 / R9469C11: got 'NE SAIT PAS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9475 / R9475C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9483 / R9483C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9513 / R9513C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9519 / R9519C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9568 / R9568C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9571 / R9571C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in V9586 / R9586C22: got 'DON'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K9705 / R9705C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL9754 / R9754C64: got '2 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL9851 / R9851C64: got '2 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL10472 / R10472C64: got '24 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL10473 / R10473C64: got '23 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL10705 / R10705C64: got '234 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K10706 / R10706C11: got 'NE SAIT PAS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K10965 / R10965C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL11034 / R11034C64: got '2 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K11332 / R11332C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K11368 / R11368C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in T11386 / R11386C20: got 'COMASEL'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K11516 / R11516C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K11537 / R11537C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL11605 / R11605C64: got '237 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K11722 / R11722C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL11804 / R11804C64: got '23 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K11898 / R11898C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K11909 / R11909C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL11931 / R11931C64: got '234 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12000 / R12000C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12076 / R12076C11: got 'NE SAIT PAS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL12117 / R12117C64: got '23 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12187 / R12187C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12204 / R12204C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12224 / R12224C11: got 'NE SAIT PAS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL12226 / R12226C64: got '23 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12350 / R12350C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12372 / R12372C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12520 / R12520C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12521 / R12521C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12522 / R12522C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL12613 / R12613C64: got '2 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in X12626 / R12626C24: got 'PAS DE LATRINE'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL12636 / R12636C64: got '3 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12647 / R12647C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL12648 / R12648C64: got '23 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12667 / R12667C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12698 / R12698C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12794 / R12794C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12863 / R12863C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12906 / R12906C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12913 / R12913C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12929 / R12929C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12941 / R12941C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12969 / R12969C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K12987 / R12987C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K13025 / R13025C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K13062 / R13062C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K13122 / R13122C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K13138 / R13138C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K13182 / R13182C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K13250 / R13250C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K13252 / R13252C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K13273 / R13273C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K13286 / R13286C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K13287 / R13287C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K13386 / R13386C11: got 'NE SAIT PAS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K13447 / R13447C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL13466 / R13466C64: got '3 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL13475 / R13475C64: got '23 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL13506 / R13506C64: got '2 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL13549 / R13549C64: got '24 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K13553 / R13553C11: got 'NE SAIT PAS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL13566 / R13566C64: got '2 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL13580 / R13580C64: got '3 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K13611 / R13611C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL13635 / R13635C64: got '27 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL13636 / R13636C64: got '2348 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL13637 / R13637C64: got '27 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in X13641 / R13641C24: got 'PAS DE LATRINE'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K13649 / R13649C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL13656 / R13656C64: got '23 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K13665 / R13665C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL13676 / R13676C64: got '23 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL13697 / R13697C64: got '3 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K13738 / R13738C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL13745 / R13745C64: got '3 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL13769 / R13769C64: got '237 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in I13968 / R13968C9: got 'SANS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in P13968 / R13968C16: got 'N'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in T13968 / R13968C20: got 'N'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in V13968 / R13968C22: got 'N'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in X13968 / R13968C24: got 'N'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in Z13968 / R13968C26: got 'N'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL14023 / R14023C64: got '2 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL14051 / R14051C64: got '2 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in X14060 / R14060C24: got 'PAS DE TOILETTES'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL14061 / R14061C64: got '7 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL14064 / R14064C64: got '2 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL14079 / R14079C64: got '3 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL14142 / R14142C64: got '23 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL14244 / R14244C64: got '36 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL14406 / R14406C64: got '3 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in P14438 / R14438C16: got 'SANS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL14446 / R14446C64: got '2 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in T14547 / R14547C20: got 'NATTE'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL14604 / R14604C64: got '23 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in T14798 / R14798C20: got 'COMASEL'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in Z14920 / R14920C26: got 'CANAL'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in V14930 / R14930C22: got 'EMPREUNTE UN GAZ'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in I14937 / R14937C9: got 'ON VU'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K14937 / R14937C11: got 'DD'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in P14937 / R14937C16: got 'D'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in T14937 / R14937C20: got 'D'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in V14937 / R14937C22: got 'D'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in X14937 / R14937C24: got 'D'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in Z14937 / R14937C26: got 'D'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in V14958 / R14958C22: got 'AUCUNE'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K15242 / R15242C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K15256 / R15256C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K15260 / R15260C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K15494 / R15494C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K15516 / R15516C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K15519 / R15519C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K15526 / R15526C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K15596 / R15596C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in V15598 / R15598C22: got 'PAS DE CUISSON'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K15624 / R15624C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in V15639 / R15639C22: got 'DON DES VOISINS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL15690 / R15690C64: got '23467 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL15758 / R15758C64: got '2 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in T15796 / R15796C20: got 'COMASEL'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K15934 / R15934C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K15940 / R15940C11: got 'NE SAIT PAS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K15952 / R15952C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K15953 / R15953C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K15962 / R15962C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K15963 / R15963C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K15972 / R15972C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K15976 / R15976C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL16009 / R16009C64: got '3 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL16010 / R16010C64: got '2 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL16012 / R16012C64: got '3 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL16018 / R16018C64: got '24 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K16073 / R16073C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K16111 / R16111C11: got 'NE SAIT PAS'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K16146 / R16146C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K16151 / R16151C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in K16155 / R16155C11: got 'NSP'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting numeric in BL16226 / R16226C64: got '234 0'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in I16347 / R16347C9: got 'PAS DE CHAMBRE'

``` r
RNU_RANEROU <- read_excel("C:/Users/DELLDRAMOMO/Desktop/ISRA-RNU/Project datasets/data/RNU datasets/Donnee_etude_inclusion_populations_pastorales_dept_RANEROU.xlsx")%>% 
  dplyr::distinct()
```

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in IO1480 / R1480C249: got 'FAFD'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in HE1640 / R1640C213: got 'PROBLEME DE FAMILLE'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in IO1731 / R1731C249: got 'CECI'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in IO1769 / R1769C249: got 'MISSA'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in IO2035 / R2035C249: got 'MISSA'

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Expecting logical in N2088 / R2088C14: got 'BASSE'

``` r
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
