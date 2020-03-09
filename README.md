# bank_marketing
# Dataset: This data contains direct market phone call campaign from 2008 to 2010 for a bank term-deposit offer. Data includes demographic (age, gender, education), financial information (default history, mortgage, or personal loan), previous campaign result (contact gap, outcome, contact attempts) and current campaign (month, day, contact attempts, duration). The data contains roughly 40k rows and 17 features (7 numerical and 10 categorical). Overall 12% customers responded to the offer. 
# Business Objective: Build predictive models to identify customers with high likelihood to respond and optimize calling strategy. The focus of the project is on using the H2o module and some feature selection methods
   # H2o: H2o is a powerful open-sourced tool for building machine learning models. It has the capability to perform parallel, distributed, and in-memory computation. 
   # AutoML: H2O’s AutoML can be used for automating the machine learning workflow, which includes automatic training and tuning of many models within a user-specified time-limit. Stacked Ensembles will be automatically trained on collections of individual models to produce highly predictive ensemble models which, in most cases, will be the top performing models in the AutoML Leaderboard.
    * Feature Selection Methods:
        * Wrapper: Model based feature selection, forward, backward, stepwise selection based a certain criterion, MSE, R-2
        * Filter: Correlation based selection, Chi-square test of independence
        * Embedded: Regularization (shrinkage), LASSO, Ridge, ElasticNet
* Data Preprocessing and EDA: 
    * Deduplication, outlier, and missing imputation
    * Correlation Plot (no highly correlated features)
    * Duration: highly correlated with response, however, this feature is not available before phone call, therefore should be excluded from the model
    * Customers with mortgage, personal loans, and default history are less likely to respond
￼
* Feature Engineering
    * Create new variable age_group by binning age feature
    * Standardization and Dummy Coding
* Model Building: 
    * 80%/20% train-test split
    * Baseline Logistic Regression: 0.89
    * Optimal Cutoff: 0.104, intersection of TPR and TNR 
    * KS-statistic: Plot TPR against FPR, and find the cutoff that maximizes the difference
* Evaluation and Parameter Tuning: 
    * H20: GBM model with max_depth = 4 after tuning gives 0.9 AUC
    * AutoML: stacked ensemble gives 0.91 AUC
