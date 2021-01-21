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



## Relationships Between Continuous Variables  
Following are some of the important points to consider when analyzing relationships between variables.  
### Visualization  
• plot(x, y) creates scatterplots where x is a vector of x-values to be plotted and y is a vector of the same length with y-values (Sect. 4.2.1.).  
• When preparing a plot for others, the plot should be labeled carefully using argu- ments such as xlab, ylab and main, so that the reader can easily understand the graphic (Sect. 4.2.1.)  
• You can color-code a plot by passing a vector of color names or color numbers as the col parameter in plot() (Sect. 4.2.2).  
• Usethelegend()commandtoaddalegendsothatreaderswillknowwhatyour color coding means (Sect. 4.2.3).  
• The cex= argument is helpful to adjust point sizes on a scatterplot (Sect. 4.2.1).  
• A scatterplotmatrix is a good way to visualize associations among several variables at once; options include pairs() (Sect. 4.4.1) and scatterplotMatrix()
from the cars package (Sect. 4.4.2).  
• Many functions such as plot() call a generic function that determines what to do based on the type of data. When a plotting function does something unexpected,
checking data types with str() will often reveal the problem (Sect. 4.2.1).  
• When variables are highly skewed, it is often helpful to draw the axes on a logarithmic scale using the by setting the log argument of the plot() function to log="x", log="y", or log="xy" (Sect. 4.2.4). Alternatively, the variables might be transformed to a more interpretable distribution (Sect. 4.5.3).  
  
### Statistics   
• cor(x, y) computes the Pearson correlation coefficient r between variables x and y. This measures the strength of the linear relationship between the variables (Sect. 4.5).  
• cor() will produce a correlation matrix when it is passed several or many vari- ables. A handy way to visualize these is with the corrplot package (Sect. 4.5.2).  
• cor.test() assesses statistical significance and reports the confidence interval for r (Sect. 4.5.1).  
• For many kinds of marketing data, the magnitude of r may be interpreted by Cohen’s rules of thumb (r =0.1 is a weak association, r =0.3 is medium, and r =0.5 is strong), although this assumes that the data are approximately normal in distribution (Sect. 4.5).  
