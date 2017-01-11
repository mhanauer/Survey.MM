install.packages("BaylorEdPsych")
library(BaylorEdPsych)
EndersTable1_1
data(EndersTable1_1)
# Ok so the patterns are analyzing where the missing data was at
# For example the first case is always where all of the data was complete
# It gets all of the cases where all of the data was complete
# Then it has the next largest pattern of missing data which can be where one variables has missing data and the other does not
#####################
# First step create a variable 
end.jp.miss = as.integer(complete.cases(end.jp)); end.jp.miss
#####################
# Add that variable to the data set
EndersTable1_1$end.jp.miss = end.jp.miss; EndersTable1_1
#####################
# First omit the JP variable because that cannot be analyzed and it make you drop all of the missing cases
EndersTable1_1 = EndersTable1_1[c(-2)]; EndersTable1_1
# Omit missing data for the sake of the anlaysis, but may need to use MI to estimate the values
EndersTable1_1 = na.omit(EndersTable1_1); EndersTable1_1
# Second step is to create the logisitic regression
jp.miss.logit = glm(end.jp.miss ~ WB + IQ, data = EndersTable1_1, family = "binomial")
# Question: Do you include the variable where the missing data is from
# If so, then why can't you detect if data is not missing at random, because if it related to it then it should be missing not at random 
# I think it is becuase you have no data on the missing values therefore you cannot tell if there is relationship between the two
summary(jp.miss.logit)
########################
# Something being werid with the logit, but correlations are fine so that will work
cor(EndersTable1_1$end.jp.miss, EndersTable1_1$IQ)
cor(EndersTable1_1$end.jp.miss, EndersTable1_1$WB)
