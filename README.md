# R-for-Marketing-Research-and-Analytics

## General Approach to inspect a data set
We can now recommend a general approach to inspecting a data set after compiling or importing it; replace “my.data” and “DATA” with the names of your objects:  
1. Import your data with read.csv() or another appropriate function and check that the importation process gives no errors.  
2. Convert it to a dataframe if needed (my.data <- data.frame(DATA) and set column names (names(my.data) <- c(...)) if needed.  
3. Examine dim() to check that the data frame has the expected number of rows and columns.  
4. Use head(my.data) and tail(my.data) to check the first few and last few rows; make sure that header rows at the beginning and blank rows at the end were not included accidentally. Also check that no good rows were skipped at the beginning.  
5. Use some() from the car package to examine a few sets of random rows.  
6. Check the data frame structure with str() to ensure that variable types and values are appropriate. Change the type of variables—especially to factor types—as necessary.  
7. Run summary() and look for unexpected values, especially min and max that are unexpected.  
8. Load the psych library and examine basic descriptives with describe(). Reconfirm the observation counts by checking that n is the same for each variable, and check trimmed mean and skew (if relevant).  

## Guidelines to describe data accrurately
The following guidelines and pointers will help you to describe data accurately and quickly:  
• Consider simulating data before collecting it, in order to test your assumptions and develop initial analysis code (Sect. 3.1).  
• Always check your data for proper structure and data quality using str(), head(), summary(), and other basic inspection commands (Sect. 3.3.3).  
• Describe discrete (categorical) data with table() (Sect. 3.2.1) and inspect continuous data with describe() from the psych package (Sect. 3.3.2).  
• Histograms (Sect. 3.4.1), boxplots, and beanplots (Sect. 3.4.2) are good for initial data visualization.  
• Use by() and aggregate() to break out your data by grouping variables (Sect. 3.4.5).  
• Advanced visualization methods include cumulative distribution (Sect.3.4.4),normality checks (Sect. 3.4.3), and mapping (Sect. 3.4.6).  
