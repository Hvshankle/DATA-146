## Project 1
### Q1: Describe what is a package? Also, describe what is a library? What are the two steps you need to execute in order to install a package and then make that library of functions accessible to your workspace and current python work session? Provide examples of how you would execute these two steps using two of the packages we have used in class thus far. Be sure to include an alias in at least one of your two examples and explain why it is a good idea to do so.
A package is something that organizes classes of the same ilk, keeping them together similar to a folder. A library is a grouping of functions which can be called and added to your workspace. The 2 steps necessary to install a package and then make the library of functions accessible to workspace are (not including installing python or the IDE): importing a package and then applying it in the workspace.  
```
import os
if not os.path.exists(data_folder):
    os.makedirs(data_folder)
```
The following is an example of using an alias. An alias is used in place of another thing, like a package. It is often simpler, shorter, and easier to understand. While os is very short, other packages such as pandas and datetime can be longer, so we often shorten them.
```
import pandas as pd
df = pd.read_csv(file_name)
``` 

### Q2: Describe what is a data frame? Identify a library of functions that is particularly useful for working with data frames. In order to read a file in its remote location within the file system of your operating system, which command would you use? Provide an example of how to read a file and import it into your work session in order to create a new data frame. Also, describe why specifying an argument within a read_() function can be significant. Does data that is saved as a file in a different type of format require a particular argument in order for a data frame to be successfully imported? Also, provide an example that describes a data frame you created. How do you determine how many rows and columns are in a data frame? Is there an alternate terminology for describing rows and columns?
A data frame is a way to hold data in a set of meaningful columns and rows. The library pandas is very useful when working with data frames. 
To read a file in its remote location within the file system of my operating system, I would assign the file path to file_name:
```
file_name_short = 'ctp_' + str(dt.now(tz = pytz.utc)).replace(' ', '_').replace(':', '_') + '.csv'
file_name = os.path.join(data_folder, file_name_short)
```
To read a file and import it into my work session in order to create a new data frame, I would import pandas and use:
```
df = pd.read_csv(file_name)
```
Data that is saved in a format other than csv can be changed into a .csv format in order to be read by a read_csv() argument. To determine how many rows and columns I've created, use the following, with df for DataFrame:
```
len(df.columns)
len(df.rows)
```

### Q3: Import the gapminder.tsv data set and create a new data frame. Interrogate and describe the year variable within the data frame you created. Does this variable exhibit regular intervals? If you were to add new outcomes to the raw data in order to update and make it more current, which years would you add to each subset of observations? Stretch goal: can you identify how many new outcomes in total you would be adding to your data frame?
```
import pandas as pd
path_to_data = '/Applications/gapminder.tsv' #where is this located on mine
data = pd.read_csv(path_to_data, sep = '\t')
```
NOTE: this doesn't actually work though. Need to find out why.
There are 12 year options, spread apart by 5 years between each: (1952, 1957, 1962, 1967, 1972, 1977, 1982, 1987, 1992, 1997, 2002, 2007). Assuming we had all relevant data to update this data set up through 2020, we could add 2 more years to keep it contiguous: (2012, 2017). 
I'm not fully certain what is meant by "number of new outcomes," but given that no new countries or continents would be added and the same 2 years would be kept constant across all included countries, this suggests that the only "new outcomes" would be Life Expectancy (LifeExp), population (pop), and Gross Domestic Product Per Capita (gdpPercap). One new "outcome" for each column (LifeExp, pop, and gdpPercap) would be added for each country across the new years (2012, 2017). In total, this would add 1,704 column/row points, but only 852 would be new (as country, continent, and year would be repeating). This is: 3 * 142 * 2.
To identify how many new outcomes this would add to the data frame, you need only multiply the number of new years (2) by the number of columns that would provide unique info (3) by the number of countries total (142). 

### Q4: Using the data frame you created by importing the gapminder.tsv data set, determine which country at what point in time had the lowest life expectancy. Conduct a cursory level investigation as to why this was the case and provide a brief explanation in support of your explanation.
Rwanda had the lowest life expectancy in 1992, which is most likely attributable to the Rwandan Civil War. After the RPF, consisting primarily of Tutsi individuals, invaded Rwanda (then controlled by Hutu individuals), the Rwandan government arrested and/or massacred Tutsi individuals in Rwanda for periods of time until 1993, before then conducting the Rwandan Genocide in 1994. 

### Q5: Using the data frame you created by importing the gapminder.tsv data set, multiply the variable pop by the variable gdpPercap and assign the results to a newly created variable. Then subset and order from highest to lowest the results for Germany, France, Italy and Spain in 2007. Create a table that illustrates your results (you are welcome to either create a table in markdown or plot/save in PyCharm and upload the image). Stretch goal: which of the four European countries exhibited the most significant increase in total gross domestic product during the previous 5-year period (to 2007)?
Answer 5
### Q6: You have been introduced to four logical operators thus far: &, ==, | and ^. Describe each one including its purpose and function. Provide an example of how each might be used in the context of programming.
& is an operator which indicates both A and B are true.
Thus, the following would yield "True"
```
(2 + 2 == 4) & (5 < 7) 
```
And, the following would yield "False"
```
(2 - 2 == 4) & (5 < 7) 
```

== is an operator used for indicating equality.
Thus, the following would yield "True"
```
a = 2
a * 2 + 3 == 7
```

| is an inclusive OR operator, indicating either A or B (or both) is true.  
Thus, the following 2 instances would yield "True"

```
(2 > 3) | (4 < 5)
(2 < 3) | (4 < 5)
```
^ is an exculsive OR operator, indicating only A or B (NOT A and B) is true.
Thus, the following would yield "True"
```
(2 > 3) ^ (4 < 5)
```
While the following would yield "False"
```
(2 < 3) ^ (4 < 5)
```
### Q7: Describe the difference between .loc and .iloc. Provide an example of how to extract a series of consecutive observations from a data frame. Stretch goal: provide an example of how to extract all observations from a series of consecutive columns.
For .loc, we have to use the row or column names, whereas with .iloc we use the row or column numbers.  

### Q8: Describe how an api works. Provide an example of how to construct a request to a remote server in order to pull data, write it to a local file and then import it to your current work session.
An API is an Application Programming Interface. It works by providing a way for two servers to "communicate" or share data.
You can create an alias for a url connecting to the data.
```
url = "https://api.covidtracking.com/v1/states/daily.csv"
```
### Q9: Describe the apply() function from the pandas library. What is its purpose? Using apply() to various class objects is an alternative (potentially preferable approach) to writing what other type of command? Why do you think apply() could be a preferred approach?
The apply() function from pandas is used to apply another function to a DataFrame. It is comparable to writing a loop, but many data scientists argue it's a faster approach because it doesn't ___ . (search every singel thing??)

### Q10: Also describe an alternative approach to filtering the number of columns in a data frame. Instead of using .iloc, what other approach might be used to select, filter and assign a subset number of variables to a new data frame?
Instead of using .iloc, an individual could employ cols and specify any specific columsn they wanted to see. 
For example:
```
cols = ['date', 'state','positive', 'death']
```
