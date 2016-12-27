# Survey.MM
# Need the following packages to run the Little test
install.packages("BaylorEdPsych")
library(BaylorEdPsych)
install.packages("mvnmle")
library(mvnmle)
# Loading the data as an example
data(EndersTable1_1)
head(EndersTable1_1)
# Running the program
LittleMCAR(EndersTable1_1)
# Running another test
TestMCARNormality(EndersTable1_1)
install.packages("mice")
library(mice)
# Output shows the pattern for missing data
# First row showing no missing data second row shows the number
# missing data on the last variable
md.pattern(EndersTable1_1)
# Loading another package
install.packages("MissMech")
library(MissMech)
