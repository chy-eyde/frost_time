# install.packages(c("ggplot2","gganimate","tidyr"))
library(ggplot2)
library(gganimate)
library(tidyr)

#### Sample that animates just a bar chart (using toy data)

# your toy data


# # build plot + transition + shadow
# p <-  #bar chart with animation - bars appear one-by-one and then loop. 
#   ggplot(g, aes(x = x, y = a)) +
#   geom_col(fill = "steelblue") +
#     transition_states(i,
#     transition_length = 0,
#     state_length      = 1,
#     wrap              = FALSE) +
#   shadow_mark(past = TRUE, future = FALSE) +
#   labs(x = "Value", y = "Height",
#       title = "Step: {closest_state}")
# 
# p #print

dat <- data.frame(
  enr = c(5, 10, 15, 20, 25), #values of bars - y-axis
  i = c(1, 2, 3, 4, 5), #order bars will appear
  est = c(10, 10, 10, 19, 24), #for eventual line
  year = c(2021, 2022, 2023, 2024, 2025), #x-axis
  barcolor = c("azure2", "azure2", "cadetblue3", "cadetblue3", "cadetblue3")
  )

theme <- theme(panel.grid.major = element_blank(), panel.grid.minor = element_blank(),
               panel.background = element_blank(), axis.line = element_line(colour = "black"))

## WORKS - bar and line animate overlaid  
#based on a stack overflow post: https://stackoverflow.com/questions/58830811/animate-plot-containing-both-bar-and-line-plots-using-r
dat %>%
  ggplot(aes(x = year, y = enr, fill = barcolor)) + #aes(x-axis, y-axis, fill color)
  geom_bar(stat = 'identity') + #specifies the stat layer - not totally clear what this is!
  geom_line(aes(year, est)) + #aes(x-axis, y-axis for line)
  geom_point(aes(year, est, shape = "circle"), size = 5, fill = "red") +
  scale_y_continuous(name = 'Price') + #,
                     #sec.axis = sec_axis(NULL, 'est')) + #sec_axis(~./100, 'Profit%')) + #creates the secondary y-axis
  transition_manual(year, cumulative = TRUE) + 
  theme 

