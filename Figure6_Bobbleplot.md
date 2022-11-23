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
### Set orders for axis 

```       
name_order <- c("Nitrogenase", "urt", "Urease", "nirA", "nrtA", "Ferredoxin--NADP reductase", "ndhH", "ndhK", "RuBisCo", "psaE", "Carbonic anhydrase", "Bicarbonate transporter BicA", "ccmM", "ccmK", "chpXY", "Orange carotenoid", "Phycoerythrocyanin", "Phycoerythrin", "Phycocyanin", "Allophycocyanin")

Condition_order <- c("C", "T1", "T2", "T10", "G")

```
### Plot the data
```

plot<- ggplot(Protein_long_nozero, aes(x=Condition , y=Subsystem))

plot + geom_point(aes(size= Abundance, colour= Condition)) +
  scale_y_discrete(limits = name_order) +
  scale_x_discrete(limits = Condition_order) +
  scale_size(limits = c(0.0001, 2),range = c(7,30), breaks = c(0.0001, 0.001, 0.01, 0.1, 1), labels = c("0.0001", "0.001", "0.01", "0.1", "1")) +  
  #facet_grid(.~Bin_Protein)+
  scale_fill_manual(values = c("dodgerblue4", "firebrick4", "aquamarine4", "darkgoldenrod4", "darkorchid4", "deeppink4", "darkseagreen4", "darkorange4", "yellow","red")) +
  theme(text = element_text(size = 14), panel.background = element_rect(fill = "white"), panel.grid.major = element_line(colour = "grey90")) 


```

Editing of colors and text was done with Inkscape
