# SR2022Malnutrition
Ay Lab, Colgate University\
Summer 2022\
Jim Perry, Will Russel

INSTRUCTIONS FOR RUNNING:
1. Install RStudio and/or make sure it's up-to-date.
2. Download and unzip this repository. 
3. Open "Malnutrition Masterscript.Rmd" in RStudio. 
4. Run "Malnutrition Masterscript". You can press ctrl+shift+R to run everything at once. Alternatively, you can click on specific chunks and use ctrl + shift + enter to run the entire block.
5. (OPTIONAL) Adjust number of features selected on line 931. Default is 10.

ACCESSING RESULTS:\
Feature selection is run on three response variable sets (stunting, thinness, and underweight/wasting), each of which contains seven subsets (full data, Urban-only, Non-urban-only, Male-only, Female-only, Youth-only (ages 10 and under), and Adolescent-only (ages 11 and older). Wasting can only be calculated for youths, so it does not contain a Youth or Adolescent split. Most results are stored in intuitive but layered data.frames in RStudio, making them very hard to write as .csvs in any meaningful way. These data.frames are stored in RStudio's environment, and are as follows:
  - "TopFeatures" holds the top n features (as determined by input on line 931, default is 10) for a specific subset as determined by various feature selection methods. For example, to find significant features for stunting in males, open "TopFeatures" from the RStudio environment iterate through "Stunting" ==> "Male".
  - "LinResults" holds results for linear regression runs. It is structured similarly to "TopFeatures" e.g. to find significant features for thinness in females according to stepwise multivariate linear regression, you open "LinResults" from the RStudio environment and iterate through "Thinness" ==> "Female".
  - "RegResults" holds results for multivariate logistic regressions on overall subsets. We used this to determine odds ratios and confidence intervals, while the regression in "TopFeatures" was done for just feature selection. It is structed similarly to "TopFeatures" and "LinResults".
  - Association Rule Learning results are written to a .csv file titled "Association_Rules.csv". It is stored in the same folder as the result of the files.
  - "RiskResults" holds Chi-Square test results (odds ratios, 95% confidence intervals, p-values and adjusted p-values) for risk factor groups determined by Association Rule Learning. Each of the three response variable sets (stunting, thinness, wasting/underweight) has several rulesets associated with them; specific rules can be obtained by opening "RiskResults" and hovering over the name of the set e.g. the first stunting ruleset is "HousePet_DontUseTP_Chicken_ ==> Stunting". Opening the ruleset shows the odds ratio (under "measure", in the order of estimate --> lower bound --> upper bound), p-value, and adjusted p-value according to Yate's continuity correction.
