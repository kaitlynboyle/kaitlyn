# Derm Review Stats

This RMD was written for exploratory data analysis and reviewer stats. The goal is to see what we can learn from the data, and determine inter-reviewer agreement and overall accuracy based on ground truth/

The markdown file:

- creates dataframes from the reviews output to make stats easier

- counts of how often a condition is selected

- co-occurrences tables between primary and secondary conditions, primary and tertiary conditions

- histograms showing frequency of confidence levels of each condition

- krippendorf's alpha

- fleiss' kappa and inter-derm agreement

- frequency charts for conditions chosen by derms

- averages and confidence intervals for derm accuracy, group accuracy

- t-test for confidence interval on true individual derm accuracy average

- qqnorm plot to look for outliers in condition selection

- individual derm variances in condition selection


## File Requirements

1. **Full sorted reviews CSV file from Albert's analysis code, preferably the one including the diagnosis nodes aggregation.**

2. **Primary and Secondary diagnosis nodes CSV, created from the reviews CSV.**

3. **Primary and tertiary diagnosis nodes CSV, created from the reviews CSV.**

4. **Binary correct/incorrect dataframe. Created manually for now, a dataframe with derm names and group decision as column heads, first column is image ids, and cells contain 1 or 0 to indicate correct/incorrect**


## RMD Outputs

1. **Generate a dataframe to output to CSV with Diagnosis Node counts.**
   _Code chunk "output_DN_Freq_
   _Can be used for determining where the majority of labels exist, and what our most common diagnosis nodes are._

2. **Derm Choices Stats**
  _From previous dataframes created by the RMD, code chunk "derm_choices_full" will output a table with diagnosis choice frequencies for each derm, variance in diagnosis selection, and plot their choices._

3. **Overall Diagnosis Choices Stats**
  _Code chunk "overall_diagnosis_choices"._
  _Outputs a table with diagnosis choice frequencies with bad quality, uncertainty, and outliers removed, variance in diagnosis choices, plot of diagnosis selections, as well as QQNorm plot to show outliers._

4. **Derm Choices Stats, uncertainty and bad quality removed**
  _Code chunk "derm_choices_stats_poor_quality_uncertainty_removed"._
  _Same output as derm choices stats, but removes uncertainty and bad quality._

5. **Matrix of diagnosis choices**
   _Used for visualization of diagnosis choices._

6. **Co-Occurrence Matrixes**
   _First, takes in a dataframe of primary and secondary diagnosis choices for each image, created from a Python script._
   _Outputs a matrix of counts of diagnosis nodes occurring with each other. Can be useful for determining what diagnosis nodes are related, if differentials are making sense, if there are outliers in the differentials, etc._
   _Second, takes in a dataframe of primary and tertiary diagnosis choices for each image, created from a Python script._
   _Outputs a matrix of counts of diagnosis nodes occurring with each other._

7. **Inter-Reviewer Agreement and Accuracy Measures**
   _Takes in a dataframe of binary 0/1 values representing Correct/Incorrect diagnosis selections for each derm and the aggregated group response._
   _Used for calculating Fleiss' Kappa values, Krippendorff's Alpha, agreement between each derm, summary stats for each derm's accuracy, confidence interval and t-test for overall average derm accuracy. 
