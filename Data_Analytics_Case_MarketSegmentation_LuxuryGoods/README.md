Data Analytics Case Study: 
---------------------------------------------------------

Data_Analytics_Case_MarketSegmentation_LuxuryGoods
---------------------------------------------------------

**Organization:** Boating Company

**Industry:** Boats Industry

**Project Description:** Segment the market based on a market research survey

**Data Description:** Survey data

**Author(s):** J. Niessing and T. Evgeniou 

**Author(s)' Affiliations:** INSEAD

**Date:** January 2014 

Background of the project
--------------------------------------------------

A boating company had become a victim of the crisis in the boating industry. The team believed that in order to develop a strategy for North America, they needed a better understanding of their current and potential customers in that market. They believed that they had to build more targeted boats for their most important segments there. To that purpose, the boating company had been commissioned a segmentation project for that market. Being a data-friendly company, the decision was made to develop a segmentation in a data-driven way - none of that soft hold-hands-and-discuss stuff. 


The Data
--------------------------------------------

With the aid of a market research firm, the boating company gathered various data about the boating market in the US through interviews with almost 3,000 boat owners and intenders. The data consisted, among others, 29 attitudes towards boating, which respondents indicated on a 5-point scale (Q. 1, 1-29 shown in the survey in the appendix).

Other types of information had been collected, such as demographics (Q. 11-15 in the survey). Finally, the boating company had compiled information about the boats, such as the length of the boat they owned, how they used their boats, and the price of the boats (Q. 2-10 in the survey). A segmentation and profile of the market would be done using all this data. 

The Approach
--------------------------------------------

Based on past experience, the decision was made to develop a segmentation that was mostly driven by attitudes that consumer held regarding boating - the attitudinal data from the 29 questions in Q.1.
Likert scale of 1-5. All the 29 items are integer variables that take values between 1 (=strongly disagree) and 5 (=strongly agree).

### Factor Analysis

As a first step, the company decided to simplify the data by grouping the 29 attitudinal statements in Q1 into a few meaningful sets/factors. This could be done using a standard method: factor analysis. The objective is to summarize information (the variation) in correlated raw attributes to a smaller number of manageable factors - which are typically uncorrelated or independent. 

## Data interpretation

1. **number of factors** can be used by the code in Report.Rmd  using the scree plot to decide the factors
the scree plot which points out the number should be the one covered more than 80%, but since the team wants more than one and five, the 5 factors still explained well of the overall survey
2. **Extraction Method** There at least five extraction methods. The evidence supports the use of one of these two:
- principal axis factoring
- maximum likelihood approaches (i.e. canonical factoring)
![image](https://github.com/user-attachments/assets/42aadaec-c5e5-4aa1-a290-b81c9b0bc039)

### Rotation Method

Once an initial solution is obtained, the loadings are rotated. Rotation is a way of maximizing high loadings and minimizing low loadings so that the simplest possible structure is achieved.

There are two commen types:
- no rotation
- `r rotation_used `, which is one of the key rotation methods used

We use the fa() function from the library Phsych because it allows us to specify different factoring methods (e.g. PAF, ML) and also different types of rotation (e.g. varimax, Oblimin and others). In such a function we have to specify r (the corelation matrix: corMat), nfactors (number of factors), rotate (type of rotation or transformations of the solution: oblimin), and fm (factoring method: principal axis).

Below are the tables of factor loadings and other statistics for the principal axis factoring and two rotation scenarios. Only the factors selected based on `r factor_selectionciterion` are shown. The first table is showing the unrotated 10-factor solution while the second table is showing the results from the variamx rotation: 

##we can tell the questions correlation and decide the main metrics we can use for analysis

for instance
Q1_27, Q1_28 and Q1_20 load strongly into the same factor (besides other attitudes).
Q1_27: "Boating is the number one thing I do with my spare time"
Q1_28: "Boating is my true passion in life"
Q1_20: "When not on my boat, I often find myself doing boating related activities"

Based on the descriptions of the attitudes that are loading into the first factor, we could say that the first factor measures a construct of "Passion and expertise around boating". We do not observe the extent to which passion is important for the respondents (the questionnaire does not ask a direct question about something called "personal image"); however, the actual attitudes allow deriving such a construct. ---> simply 29 questions to 10 main focus

**##cluster analysis**


