<strong>preprocessorAH</strong> is a Python module for data preprocessing purpose and is distributed under MIT license.

The project is started on 2021 by Anupam Hore as a creator.

It is currently maintained by Anupam Hore.

<h1>Installation</h1>
<hr>

<h3>Dependencies</h3>

preprocessorAH requires:

 <ul>
    <li>Python(>=3.8)</li>
    <li>statsmodels(0.12.0)</li>
    <li>pandas(0.25.3)</li>
    <li>scikit_learn(0.24.2)</li>
</ul>
<hr>

<h3>User Installation</h3>
The easiest way to install <strong>preprocessorAH</strong> is using pip:

<pre>pip install preprocessorAH</pre>

<h3>IMPORT</h3>
<pre>from preprocessorAH import preprocessor</pre>

<h3>Development</h3>
<hr>
We welcome new contributors of all experience levels.Our main aim is to build and enhance this library in best possible way.

<h3>Contributing</h3>
To learn more about making a contribution, please drop an email at anupam.hore@yahoo.com

<h3>Testing</h3>
You can test the package after installation using pytest

<pre>pytest preprocessorAH</pre>

<h1>Change Log</h1>
<hr>
0.0.1 (02/09/2021) - First Release
<hr>

<h1>Documentation</h1>
<hr>
<h3>getDescribe(data)</h3>
    
    Method Name:getDescribe
    Description: This method calls the DataFrame's describe() method
    Input: Expected arguments are DataFrame, List, Series
    Output: A dataframe with all statistical information about data distribution
    On Failure: Raise Exception
    Written By: Anupam Hore
    Version: 1.0
    Revisions: None

<h3>getHead(df, num)</h3>
    
    Method Name:getHead
    Description: This method calls the DataFrame's head() method
    Input: Expected arguments are the dataframe and the number of observations to be viewed
    Output: A dataframe with first 'num' number of observations
    On Failure: Raise Exception
    Written By: Anupam Hore
    Version: 1.0
    Revisions: None

<h3>getHeadforFirstFive(df)</h3>
    
    Method Name:getHeadforFirstFive
    Description: This method calls the DataFrame's head() method
    Input: Expected arguments is the dataframe
    Output: A dataframe with first 5 number of observations
    On Failure: Raise Exception
    Written By: Anupam Hore
    Version: 1.0
    Revisions: None

<h3>loadcsv(file)</h3>
    
    Method Name:loadcsv
    Description: This method calls the DataFrame's read_csv() method
    Input: Expected arguments is the file path
    Output: A dataframe
    On Failure: Raise Exception
    Written By: Anupam Hore
    Version: 1.0
    Revisions: None

<h3>getTailForLastFive(df)</h3>
    
    Method Name:getTailForLastFive
    Description: This method calls the DataFrame's tail() method
    Input: Expected arguments is the dataframe
    Output: A dataframe with last 5 number of observations
    On Failure: Raise Exception
    Written By: Anupam Hore
    Version: 1.0
    Revisions: None

<h3>getTail(df, num)</h3>
    
    Method Name:getTail
    Description: This method calls the DataFrame's tail() method
    Input: Expected arguments are the dataframe and the number of observations
    Output: A dataframe with last 'num' number of observations
    On Failure: Raise Exception
    Written By: Anupam Hore
    Version: 1.0
    Revisions: None

<h3>checkNull(df)</h3>
    
    Method Name:checkNull
    Description: This method calls the dataframe's isnull().sum() method
    Input: Expected argument is the dataframe
    Output: A Series with all of the columns from the dataframe and the sum of their null values
    On Failure: Raise Exception
    Written By: Anupam Hore
    Version: 1.0
    Revisions: None

<h3>dropVariables(df,varlist,axis,inplace)</h3>
    
    Method Name:dropColumns
    Description: This method calls the dataframe's drop method
    Input: Expected arguments are the dataframe, list of columns to drop, axis, inplace
            axis => 1 - Columns, 0 - Row
            inplace => 1 - Permanent Drop, 0 - Temporary Drop
    On Failure: Raise Exception
    Written By: Anupam Hore
    Version: 1.0
    Revisions: None

<h3>createdummies(df)</h3>
    
    Method Name:createdummies
    Description: This method calls the dataframe's get_dummies method to create dummies for categorical variables
    Input: Expected argument is the dataframe
    Output: The dataframe with the dummies incorporated
    On Failure: Raise Exception
    Written By: Anupam Hore
    Version: 1.0
    Revisions: None

<h3>findHighCorr_Vars(df,threshold = 10)</h3>
    
    Method Name:findHighCorr_Vars
    Description: This method calls the dataframe's corr() method to get the correlation and then based on the threshold value, create a list of all the variables with high correlation
                 This method should be used to find correlation between independant variables (NOT TARGET Variable)
                 Use "separate_label_features" from this package to separate dependant and independant variables
    Input: Expected arguments are the dataframe(excluding the target variable) and the threshold value
           Threshold -> till what value, correlation is ok between independant variables. Beyond this value, we should remove the variables from the dataframe
    Output: Return a list of highly correlated variables
    On Failure: Raise Exception
    Written By: Anupam Hore
    Version: 1.0
    Revisions: None

<h3>impute_missing_values(df,discrete=None)</h3>
    
    Method Name:impute_missing_values
    Description: This method calls the dataframe's fillna() method to fill the missing values with column's median,mode value depending on numerical or categorical data
    Input: Expected argument is the dataframe and discrete(True or False)
           DataFrame columns can contain continuous,discrete and categorical variables
           If discrete is set to True then we will handle discrete variable
    For Discrete: For detecting discrete variables, the criteria is the variable should have more than 0 unique values and less than 5. if more than 5 then we will consider it as continuous variable. Median value will be considered if continuous or else mode value
    Output: The dataframe with the missing values removed
    On Failure: Raise Exception
    Written By: Anupam Hore
    Version: 1.0
    Revisions: None

<h3>impute_outliers(df,cols,type)</h3>
    
    Method Name:impute_outliers
    Description: This method calls the dataframe's quantile method to calculate Inter Quantile Range of the variable, based on which the upper and lower bounds for the variables are calculated
    Input: Expected argument are the dataframe, the columns which have outliers and type of distribution.
           Type = It is a list of data distribution. Values excepted are "Gaussian", "Skewed", "Highly Skewed"
           e.g., type = ["Gaussian, "Skewed", "Highly Skewed"] for three variables.
    Expected Criteria: The length of "types" list should be same as the length of "cols" list

    Example:
          impute_outliers(df, ['Age','Salary', 'Fare'],['Gaussian','Skewed','Highly Skewed']
          impute_outliers(df, ['Age','Salary', 'Fare'],['Gaussian','Gaussian','Skewed']
          etc.,

          For Gaussian Distribution:
               bound  = df[variable].mean() +- 3 * df[variable].std()
          For Skewed Distribution:
              bound = df[variable].quantile(0.25) +- 1.5 * IQR
          For Highly Skewed Distribution:
              bound = df[variable].quantile(0.25) +- 3.0 * IQR

    Output: The dataframe with outliers handled
    On Failure: Raise Exception
    Written By: Anupam Hore
    Version: 1.0
    Revisions: None

<h3>separate_label_features(df,labelName)</h3>
    
    Method Name:separate_label_features
    Description: This method separates the independant and dependant variables in the dataset
    Input: Expected arguments are the dataframe and the target variable
    Output: The independant and target(dependant) variables
    On Failure: Raise Exception
    Written By: Anupam Hore
    Version: 1.0
    Revisions: None

<h3>getScalarDistribution(df)</h3>
    
    Method Name:getScalarDistribution
    Description: This method calls the sklearn.preprocessing StandardScaler() to get the scaled distribution
    Input: Expected arguments is the dataframe (with ONLY Independant Variables. NO TARGET VARIABLES)
           Use "separate_label_features" from the package to separate dependant and independant variables
    Output: Array of scaled distribution
    On Failure: Raise Exception
    Written By: Anupam Hore
    Version: 1.0
    Revisions: None
    
<h3>find_variance_inflation_factor(arr, df)</h3>
    
    Method Name:find_variance_inflation_factor
    Description: This method calls the statsmodels.stats.outlier_influence 's  variance_inflation_factor to calculate the VIF
    Input: 
            arr = scaled transformed array. Find the scaled transformed array using
             E.g.,
               arr = preprocessor.getScalarDistribution(df)
            df  : a dataframe
             E.g.,
            df = preprocessor.loadcsv('FilePath')
          
    Output: Returns list of variables with Variance Inflation Factor(VIF) greater than 10
    On Failure: Raise Exception
    Written By: Anupam Hore
    Version: 1.0
    Revisions: None
