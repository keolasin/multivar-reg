---
Week: 1
Lecture: Lecture 1
Topic: Introduction to Multivariate Statistics
Instructor: Lexin Li
Course: Multivariate Statistics, PH 245
Tags: Introduction, Multivariate Statistics
---

# Course Overview

Office hours: BWW, Room 5330 with Lexin Li

## Course info

Suggested books:

1. Applied Multivariate Statistical Analysis, Richard Johnson and Dean
Wichern, 2007, 6th edition, Pearson Prentice Hall

- some homework problems from this book, but all context for homework provided in class
- lecture roughly follows this textbook

2. Statistics for Epidemiology, Nicholas Jewell, 2003, Chapman & Hall

- Jewell at UC Berkeley

3. Applied Regression Including Computing and Graphics, R Dennis Cook
and Sanford Weisberg, 1999, Wiley

4. The Elements of Statistical Learning – Data Mining, Inference and
Prediction, Trevor Hastie, Robert Tibshirani, and Jerome Friedman,
2009, 2nd edition, Springer

- learning the basic statistics

## Topics & tentative schedule

- review of basic concepts & matrix algebra
- comparison of multivariate means (ch 6)
- linear regression model (ch 7, Cook & Weisberg's)
- logistic regression model (Jewell's book, ch 12-15)
- Principal components analysis (ch 8)
- Factor analysis (ch 9)
- Classification (ch 11)
- Clustering (ch 12)

### Computing

- R, Rstudio
- Lecture: command, output, and interpretations
- Lab: everything else

## Homework & Exams

- 5 Homework assignments, on your own, two weeks to complete, due two weeks from assigned date
- No Final Exam
- Final Project

## Final Project

Real data analysis project

Can pair up to do the project, only 2 people per team

### Data

- analysis of a data set of moderate complexity, using one or more of the techniques covered in the course
- it would be best if this data is from your own research / thesis / dissertation, Lexin can recommend some datasets as well

### Schedule

Email Lexin a one-page project proposal (problem to address, key info about the data, method to use, etc) between Nov 7 and 11

Final project report is due on Dec 12

### Final Project Report

No more than 5 pages, which includes figures and tables
Divided into sections:

- Executive summary (bullet points)
- Background
- Problem (question to address)
- Data (summary of the data, the study design, data collection)
- Method (your choice of model / analytic method, and why)
- Results (summary of numerical analysis, interpretation, assumptions check)
- Conclusion

We need to tell Lexin the interpretation of the results, don't just run the code, needs analysis

## Objectives

End of the semester, be able to:

- have appreciation for a range of multivariate methods and their use and limitations in a research context
- examine critically other researchers' use of methods of analysis for multivariate data
- select (know what to search and why to choose), carry out and interpret appropriate statistical methods for describing and analyzing multivariate data sets, in the context of your own research
- if you have any specific objective in mind, feel free to reach out to Lexin.

### Math in the course

We'll need to use a fair amount of math, specifically matrix algebra

## Plan

- review basic matrix algebra and concepts
- emphasize intuition behind each method
- emphasize assumptions of each method and their consequences
- emphasize characterization of uncertainty
- connect to some typical real world examples
- connect with other related methods
- introduce briefly some more recent extensions

### Keep in mind...

What is the method about? What kind of question does this method try to address? Can you explain it in no more than 3 min/sentences?

What is the intuition behind this method?

## Topics Overview

### Comparison of multivariate means (slide 11)

Example: Anesthetizing effect of CO2 ad halothane

- n=19 dogs, each of which was treated with 4 treatments
- response variable is ms between heartbeats
- 4 different treatments: 2 CO2 pressures x halothane

| Treatment | CO2 pressure | Halothane |
|-----------|--------------|-----------|
| 1         | high         | present   |
| 2         | low          | absent    |
| 3         | high         | absent    |
| 4         | low          | present   |

- What will change to answer the same question?
    - suppose we select 5 dogs for each of 4 treatments
    - suppose there are 20 different levels of CO2
    - suppose the CO2 level should really be treated as continuous rather than discrete

#### Rationale

What is it about?

Compare quantitative measures of subjects between groups that are defined by factor(s) with two or more levels

Topics to cover:

- **same subjects** - within-subject comparison (section 6.2)
    - multiple variables, paired comparison
    - multiple measurements, repeated measures design
- **different subjects** - between-subject comparison
    - *one factor*: two populations (section 6.3) - two sample t^2 test
    - *one factor*: more than two populations (section 6.4) - one-way MANOVA
    - *two factors*: two way MANOVA (section 6.7)
- **Multiple testing**

Pay special attention:

- one-to-one correspondence to the univariate comparison
- assumptions! (because they lead to different choices of test)

### Linear Regression Model (slide 13)

Example: US infant mortality rate from Annie E. Casey Kids Count Data Center

- Y: infant mortality rate
- X1: low birthweight rate
- X2: teen birth rate
- X3: poverty rate
- X4: no insurance rate
- 50 states + D.C.
- many other variables

If you can visualize the data, do that first thing to get a sense of the data

#### Rationale

What is it about:

- Association/relation between response/dependent variable (Y) and predictor/input/feature variable (X); how the value of Y changes as a function of X (or, change of Y when you change the value of X)

Topics to cover:

- data visualization
- Model, interpretation, estimation, prediction
- Characterization of uncertainty
- Categorical explanatory variables
- Goodness-of-fit, model diagnosis, and remedies
- Extensions: multivariate responses, nonlinear models, variable selection

Pay special attention:

- interpretation! it's our job to interpret the results, how do we characterize the uncertainty in our analysis, how do we know it's a good model/fit, etc.
- is this a good model?

### Logistic Regression Model (slide 15)

Example: western collaborative group study

- *samples*: 3154 men, ages 39 to 59, free of coronary heart disease (CHD) at beginning of study
- *response*: a *binary* (event occurs or does not occur) indicator whether a CHD event occurred (about 8%) within the 8.5 year follow-up period
- *predictors*: the type A/B behavior pattern, height and weight, total cholesterol levels, systolic and diastolic blood pressure, and smoking history (number of cigarettes smoked per day)
- one of main goals was to explore the relationship between behavior pattern, so-called Type A behavior, and the risk of coronary heart disease (CHD)

#### Rationale

What is it about:

- model the probability of disease as a function of a number of explanatory variables
- explanatory variables include: exposure/risk factors, or treatment variables + covariates to adjust for

Topics to cover:

- Model, interpretation, estimation
- Extensions: parallel to linear regression

Pay special attention:

- interpretation: relative risks, odds ratio
- study design and how it affects the model
- Ultimately, observing association between X & Y

### Principal Components Analysis (slide 17)

Example: HapMap data

- HapMap: an international organization that aims to develop a haplotype (collection of specific alleles) map of the human genome, which will describe the common patterns of human genetic variation
- 2918 SNPs on chromosome 21 (smallest chromosome; associated with diseases such as Down Syndrome)
- 208 Yoruban (YRI, an ethnic group in west Africa), Japanese (JPT), Han Chinese (CHB), and CEPH (CEU, Utah residents with ancestry from northern and western Europe) individuals
- representing a single individual as a 2918-unit long vector
    - But, if each individual were only represented by two variables (weight & height), can you visualize that data easily? Yes
    - But, since each individual is represented by 2918 variables, how do we represent that? Try to summarize and turn into some summary variables, then plot that data more easily

#### Rationale

What is it about:

- dimension reduction / data compression / data visualization...
- find a few (linear) combinations of the variables to "best summarize" those variables
- represent data in a low dimensional space, and preserve data variability by exploiting the covariance structure of the set of variables

Topics to cover:

- population solution, sample version (sections 8.2, 8.3)
- Extensions: sparse pca, principal components regression

Pay special attention:

- Applications! (principal components analysis is widely used)

### Factor Analysis (slide 20)

Example: consumer-preference study

- in a consumer-preference study, a random sample of customers were asked to rate 5 attributes of a new product
- the response is on a 7-point semantic differential scale, and the correlation matrix is:

(add table from slide 20)

- question of interest: any underlying patterns / grouping of those attributes? What are the underlying summary variables that capture most of the information of the data?

#### Rationale

What is it about:

- find unobservable latent variables, called factors, which are responsible for groups of strongly correlated variables in the data
- widely used in the quality of life (QoL) studies. Among many questions in a survey, it is of common interest to learn how they are grouped as well as characteristics of each group. Characteristics of each group may be represented by a (latent) factor, which reflects, say, physical ability or mental health

Topics to cover:

- Model, estimation, rotation, factor scores (sections 9.2-9.5)
- Extension: latent regression models

Pay special attention:

- Identifiability, then interpretation
- Closely related to Principal Components Analysis but different in critical ways.
- mostly focuses on the X variables, rather than the association between X & Y

### Discriminant Analysis and Classification (slide 22)

Example: Cleveland heart disease data

- 303 patients, a dx of heart disease (0=absence, 1=presence, 160 absence and 137 presence)
- 13 attributes, including age, gender, chest pain type (1-4), resting blood pressure, serum cholesterol, fasting blood sugar (1=true, 0=false), resting ECG results, max heart rate achieved, exercise induced angina (1=yes, 0=no)

Many classification examples:

- classify tumor samples as benign or malignant
- classify patients as having Alzheimer's disease or general pop

Machine learning developed for classification methods

- if we want to classify, we need to train our model to develop a good method for classifying
- how do we make a classification? based on the previous training
- how accurately can we *classify future* samples using our model/method

Ultimate goal in this topic is classify one of these into a class, to better understand the association between X & Y and model it

Another example: credit-card transactions identified as fraud or not?

Credit card transactions trained on previous data, how do we classify as fraud if there's a transaction that might be weird? Using the trained model to classify as fraud/normal transaction

#### Rationale

What is it about:

- separation and allocation: to describe graphically or algebraically the differential features (e.g., biomarkers, patient's demographics, etc) of data from several known populations (e.g., progressive and non-progressive); to develop a rule to allocate data cases (e.g., patients) into two or more known classes
- supervised learning

Topics to cover:

- how to evaluate a classifier?
- two groups:

### Clustering (slide 24)

example: NCI60

- 60 cell lines derived from human tumors + gene expressions of about 8,000 genes
- cell lines from leukaemia, melanoma, central nervous system, colon, renal, and ovarian tissue were clustered into branches specific to the respective organ types with few exceptions
- cell lines derived non-small lung carcinoma and breast tumors were distributed in different terminal branches suggesting that their gene expression patterns were more heterogeneous
- initially, we don't have any info on the classification for those 60 samples, can we find something interesting?
- clustering at high-level tries to see which samples are similar to one another using some rule/method
    - in this process, we don't know how many groups there are
    - after clustering, we've found some interesting groups, and now we can compare these identified groups (from the clustering analysis) to some additional info (which cell lines the samples were obtained from, such as renal, colon, leukaemia, etc.)

#### Rationale

What is it about:

- discover natural, unkown grouping patterns in data
- more used for exploration
- unsupervised learning (different from classification, which is a supervised learning)
    - clustering, we don't have the training set to model

Topics to cover:

- similarity / distance measures (sections 12.1 and 12.2) - define what you feel sound right and legitimate
- clustering methods
    - hierarchical clustering (section 12.3)
    - K-means (section 12.4)
    - Model-based clustering (section 12.5)
- extensions: multidimensional scaling

Pay special attention:

- robustness
- exploratory nature: starting points for future research

### Super Example

Example: Body fat

- body fat, a measure of health, is estimated through an underwater weighing technique. Fitting body fat to the other measurements using multiple regression provides a convenient way of estimating body fat for men using only a scale and a measuring tape.
- Percentage of body fat, age, weight, height, and ten body circumference measurements are recorded for 252 men.

    - percent body fat using Brozek's equation, 457/Density - 414.2
    - percent body fat using Siri's equation, 495/Density - 450
    - Density (gm/cm^3); Age (yrs); Weight (lbs); Height (inches); Adiposity index = Weight/Height^2 (kg/m^2); Fat Free Weight = (1 - fraction of body fat) * Weight, using Brozek's formula (lbs)
    - Circumference (cm): Neck; Chest; Abdomen; Hip; Thigh; Knee; Ankle: Extended biceps; Forearm; Wrist

- Dichotomized body fat groups: Obese (>25%), Normal (<25%)

## Big Picture

The most fundamental question we aim to address throughout the semester:

The association between X and Y.

- What is X? How many X? categorical or continuous? How many levels?
- What is Y? How many Y? Categorical or continuous? How many levels?
- What is the data replication / individual sampling unit? How many?

Our answer to those 3 questions will tell us which method we should/should not use