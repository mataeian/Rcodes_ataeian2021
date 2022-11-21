# Heatmap for presence of orthologous genes among Phormidium and Nodosilinea

Saved the excel file as .csv with genomes as columns and genes as rows and called it Orthologue_image5.csv

### Set working directory and loaded libraries
```
setwd("/Maryam/papers/R_scripts_for_Figures")
library(ggplot2)
library(reshape2)
```
### Uploaded my data to R

```
orthologues <- read.csv("Orthologue_image5.csv", header = TRUE)
```
I saw this character "ï.." before gene column and code was not working. To fix this issue I Open the CSV file in NotePad++, click "Encoding" and select "Encode in UTF-8" and save the file. It removes the BOM, and the original code should work.

### Convert data frame from a "wide" format to a "long" format
```
xx = melt(orthologues, id = c("Gene", "Category"))
```