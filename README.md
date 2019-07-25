# Common-Codes
common codes and packages to use for projects

#install swirl-- this is a program that will walk you through r coding to let you learn a little more
install.packages(“swirl”)
library(swirl)

#install tidyverse- helps with data manipulation, exploration and visualization
install.packages("tidyverse")

#load tidyverse
library(tidyverse)

#install esquisse
install.packages("esquisse")
library(esquisse)

#load data set (choose name for data set, read the name of how the data is on computer)
ca <- read_csv("https://raw.githubusercontent.com/OHI-Science/data-science-training/master/data/ca.csv")

#chi square test for independence and fisher exact examples
#read in excel file
breastfeedingcompliancelist <- read_excel("~/Downloads/breastfeedingcompliancelist.xlsx")

#view data layout
View(breastfeedingcompliancelist)

#variable label/create new variable
year <-breastfeedingcompliancelist$Year

#variable label/create new variable
compliance <-breastfeedingcompliancelist$Compliance

#contingency table 
table(year,compliance)

#create table variable 
table1<-table(year, compliance)

#chi sqaure test and fisher exact using table variable 
chisq.test(table1)
fisher.test(table1)

#Wilcoxon sign rank test: when to use: Wilcoxon signed-rank test is a non-parametric statistical hypothesis test used to compare two related samples, matched samples, or repeated measurements on a single sample to assess whether their population mean ranks differ (i.e. it is a paired difference test).Think pre and post test 

#load data
prepostgoldbergr <- read_excel("~/Downloads/prepostgoldbergr.xlsx")

#view data
View(prepostgoldbergr)

#label variable
preansiedad<-prepostgoldbergr$PrePuntajeAnsiedad

#label variable
postansiedad<-prepostgoldbergr$PostPuntajeAnsiedad

#wilcoxon sign rank test
wilcox.test(preansiedad,postansiedad,paired=TRUE)

#Man Whitney Test of Wilcoxon Rank Sum Test: s a nonparametric test of the null hypothesis that it is equally likely that a randomly selected value from one sample will be less than or greater than a randomly selected value from a second sample.

#code for man whitney 

wilcox.test(VAR1, VAR2)

#Spearman correlation: nonparametric version of the Pearson product-moment correlation. Spearman's correlation coefficient, (ρ, also signified by rs) measures the strength and direction of association between two ranked variables.

#load data set first and name variables 

#SPEARMAN code. Variable 1 is a name of a variable and variable 2 of the other variable
cor.test(VAR1, VAR2, method="spearman")

#ANOVA variation" among and between groups. Use when independent variable is continous and dependent variable has more than 2 categories

#NOTE ths this is not for repeated measures (when data is collected for the same group over time)

#load in data and review data, create variable labels 
# Compute the analysis of variance
res.aov <- aov(VAR1 ~ VAR2, data = my_data)
# Summary of the analysis
summary(res.aov)

#T TEST
#load in data and review data, create variable labels 
#how to do a t test for independent samples 

#r assumes that the variance is not equal (technically welch's test)
t.test(VAR1, VAR2)
    ## or you can use: t.test(VAR1, VAR2, var.equal = FALSE)

##note if the variance is equal use
t.test(VAR1, VAR2, var.equal = TRUE)


#RQDA for qualitative data analysis
library(RQDA)
##when new RQDA menu shows up, select new project and upload text files 
RQDA()
#Note i started with just question numner 1 in the circles which was how do you feel right now with the if starting new project, make sure that you use library(RQDA) and set up the new project
#the first file is stored in /Users/jhinshaw/Desktop/text file circles/.rqda"
summaryCodings()
#note this gives you the number of codings and average number of characters asociated with each code
getCodingTable()
codes=summaryCodings()
str(codes)
###Now starting with question #2 Nicaragua en Paz. 
# the file is stored /Users/jhinshaw/Desktop/text file circles/Nicaragua en Paz.rqda"
summaryCodings()
