# Script copied from https://owi.usgs.gov/blog/data-munging/

# load libraries
library(dplyr)
library(dataRetrieval)
library(lubridate)
library(tidyr)
library(ggplot2)
library(viridis)

# Get data for the Yahara River at Windsor in Dane County, Wisconsin
yahara_no <- '05427718'

# define parameters of interest, and get those parameter names
params <- c('00060', '00671', '80154', '00665')

# get daily values from NWIS
yahara_dat <- readNWISdv(siteNumbers = yahara_no, parameterCd = params, 
                         startDate = '1997-10-01', endDate = '2017-09-30')

# rename columns using renameNWISColumns from package dataRetrieval
yahara_dat <- renameNWISColumns(yahara_dat, 
                                p00665 = "TP_mgL",
                                p00671 = "Orthophosphate_mgL",
                                p80154 = "SS_mgL")

yahara_names <- names(yahara_dat)
grep('_cd', yahara_names) # returns the index of the match
grep('_cd', yahara_names, value = TRUE) # returns the matched elements themselves
gsub('_cd', '_code', yahara_names)
yahara_dat <- select(yahara_dat, -contains('_cd'))


# add water year variable "waterYear" to our dataframe
yahara_dat <- addWaterYear(yahara_dat)

# calculate cumulative discharge for each year by first grouping by water year,
# and then using the "cumsum" function. Add day of water year for plotting purposes.
# These steps will build a new dataframe, with the existing information in yahara_dat
# but with two additional columns.
cumulative_dat <- group_by(yahara_dat, waterYear) %>%
  mutate(cumulative_dis = cumsum(Flow), 
         wy_doy = seq(1:n()))

# visually compare cumulative discharge across years
ggplot(cumulative_dat, aes(x = wy_doy, y = cumulative_dis, group = waterYear)) +
  geom_line(aes(color = waterYear)) +
  scale_color_viridis_c() +
  scale_x_continuous(breaks = c(1, 93, 184, 275), labels = c("Oct 1", "Jan 1", "Apr 1", "July 1")) +
  theme_bw() +
  labs(color = "Water Year", x = "", y = "Cumulative Discharge")