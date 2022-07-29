# PalmerPenguins-R

I used PalmerPenguins Dataset in RStudio to analyze interesting findings about their species, bill lengths, body mass.
#Penguins Analysis by Ashuma Kalia
##Setting up my R environment
Notes: loading the 'tidyverse' and 'palmerpenguins' packages:
```{r}
install.packages("palmerpenguins")
library(palmerpenguins)
library(tidyverse)

##sort data by bill length
penguins %>% arrange(bill_length_mm)

##save sorted data to penguins2 variable

penguins2 <- penguins %>% arrange(bill_length_mm)

##view data in clean dataframe to save it in script 
View (penguins2)

## Group by function and mean of bill lengths in islands 
penguins %>% group_by(island) %>% drop_na() %>% summarize(mean_bill_length_mm = mean(bill_length_mm))

## find max bill length
penguins %>% group_by(island) %>% drop_na() %>% summarize(max_bill_length_mm = max(bill_length_mm))

##group by species and island, drop na, and find max and mean bill length
penguins %>% group_by(species,island) %>% drop_na() %>% summarize(max_bl=max(bill_length_mm), mean_bl=mean(bill_length_mm))

##filter by species
penguins %>% filter(species == "Adelie") %>% drop_na

##convert penguins body mass from kg to g
penguins%>%
  mutate(body_mass_kg=body_mass_g/1000)
## install and load ggplot2
install.packages("ggplot2")
library(ggplot2)

data("penguins")
View(penguins)

##Plot a scatter plot
ggplot(data=penguins)+
  geom_point(mapping=aes(x=flipper_length_mm, y=body_mass_g,color=species))

##save the plot
ggsave("Three Penguin Species.png")

##install rmarkdown package 
install.packages("rmarkdown")
