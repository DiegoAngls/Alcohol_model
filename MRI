 Example BrkRAW
setwd("~/Desktop/brkraw_example")
rm(list=ls())
date <- Sys.Date() 

# Angeles-Valdez Diego 

# packages ----------------------------------------------------------------
pacman::p_load(readxl,tidyverse)

data <- read_xlsx("/home/dangeles/Desktop/brkraw_example/Data/Modelo.xlsx")
#data$SessID <- str_sub(data$SessID, 21,29)
#data$fecha <- str_sub(data$RawData,0,8)
data <- data %>% separate(SubjID , into =  c("SubjID2 ","SubjID"), sep = "B03-GARZA-SUDMEX-") 


dataset <- data %>% 
 select(-`SubjID2 `) %>% 
  #select(RawData, SubjID, SessID, ScanID,  RecoID, DataType, task, modality, Start, End) %>%  
  mutate(
    SessID = str_sub(data$SessID, 21,29),
   # fecha =str_sub(data$RawData,0,8),
    task =  case_when(data$DataType == "func" ~ "rest"),
    modality =  case_when(data$DataType == "anat" ~ "T1w",
                          data$DataType == "func" ~ "bold",
                          data$DataType == "dwi" ~ "dwi"))


# dataset[dataset == "NA"] <- ""
write_excel_csv(dataset, "/home/dangeles/Desktop/brkraw_example/Data/Modelo_1.csv")

write.csv(dataset, "/home/dangeles/Desktop/brkraw_example/Data/Modelo_1.csv")


