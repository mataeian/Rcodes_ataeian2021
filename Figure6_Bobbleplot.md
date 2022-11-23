# Bubble Plot for comparing protein expression

Saved the excel file as .csv with conditions as columns and proteins as rows and called it Cyano_proteins.csv


### Set working directory and loaded libraries 

```
setwd("/Maryam/papers/R_scripts_for_Figures")
library(dplyr)
library(tidyr)
library(ggplot2)
```

### Uploaded my data to R
```
Protein <- read.table("Cyano_proteins.csv", header = TRUE, sep = ",")
```


### Changed my data structure from wide to long format
```
Protein_long <- gather(Protein , Condition , Abundance, 2:6)
```
### Removed zero

```
Protein_long_nozero <- filter(Protein_long, Abundance > 0)
```
