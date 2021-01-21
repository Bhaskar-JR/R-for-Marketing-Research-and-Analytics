# R-for-Marketing-Research-and-Analytics

## Describing Data  

It is important to describe and explore any data set before moving on to more complex analysis.  
This would involve summarizing and exploring a data set with descriptive statistics (mean, standard deviation, and so forth) and visualization methods.  
### General Approach to inspect a data set
We can now recommend a general approach to inspecting a data set after compiling or importing it; replace “my.data” and “DATA” with the names of your objects:  
1. Import your data with read.csv() or another appropriate function and check that the importation process gives no errors.  
2. Convert it to a dataframe if needed (my.data <- data.frame(DATA) and set column names (names(my.data) <- c(...)) if needed.  
3. Examine dim() to check that the data frame has the expected number of rows and columns.  
4. Use head(my.data) and tail(my.data) to check the first few and last few rows; make sure that header rows at the beginning and blank rows at the end were not included accidentally. Also check that no good rows were skipped at the beginning.  
5. Use some() from the car package to examine a few sets of random rows.  
6. Check the data frame structure with str() to ensure that variable types and values are appropriate. Change the type of variables—especially to factor types—as necessary.  
7. Run summary() and look for unexpected values, especially min and max that are unexpected.  
8. Load the psych library and examine basic descriptives with describe(). Reconfirm the observation counts by checking that n is the same for each variable, and check trimmed mean and skew (if relevant).  

### Guidelines to describe data accurately
The following guidelines and pointers will help you to describe data accurately and quickly:  
• Consider simulating data before collecting it, in order to test your assumptions and develop initial analysis code (Sect. 3.1).  
• Always check your data for proper structure and data quality using str(), head(), summary(), and other basic inspection commands (Sect. 3.3.3).  
• Describe discrete (categorical) data with table() (Sect. 3.2.1) and inspect continuous data with describe() from the psych package (Sect. 3.3.2).  
• Histograms (Sect. 3.4.1), boxplots, and beanplots (Sect. 3.4.2) are good for initial data visualization.  
• Use by() and aggregate() to break out your data by grouping variables (Sect. 3.4.5).  
• Advanced visualization methods include cumulative distribution (Sect.3.4.4),normality checks (Sect. 3.4.3), and mapping (Sect. 3.4.6).  

## Relationships Between Continuous Variables  
The most important insights in marketing analysis often come from understanding relationships between variables. It helps marketers to understand how to reach customers more effectively. For example, if people who live closer to a store visit more frequently and buy more, then an obvious strategy would be to send advertisements to people who live in the area.  
  
We shall focus on understanding the relationships between pairs of variables in multivariate data, and examine how to visualize the relationships and compute statistics that describe their associations (correlation coefficients).  
  
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
• When the relationship between two variables is nonlinear, r does not give an accurate assessment of the association. Computing r between transformed variables may make associations more apparent (Sect. 4.5.3.).  
• There are common distributions that often occur in marketing, such as unit sales being related to log(price). Before modeling associations, plot histograms of your variables and assess potential transformations of them (Sect. 4.5.4).  
• An automated way to select an optimal transformation is to use a Box-Cox transform (Sect. 4.5.5).  
• The function polychor() from the psych package is useful to compute correlations between survey responses on ordinal ratings scales (Sect. 4.6.2).  
  
### Transforming Variables Before Computing Correlations

Correlation coefficient r measures the linear association between two variables. If the relationship between two variables is not linear, it would be misleading to interpret r. Many relationships in marketing data are nonlinear.It is therefore important to consider transforming variables to approximate normality before computing correlations or creating scatterplots; the appropriate transformation may help you to see associations more clearly.

#### Typical Marketing Data Transformations 

##### Common transformations of variables in marketing  
Variable | Common Transformations 
--- | --- 
Unit Sales, revenue, household income, price | log(x) 
Distance | 1/x, 1/x^2, log(x) 
Market or Preference Based Share on a utility value | e<sup>x</sup>/(1+e<sup>x</sup>)
Right Tailed Distributions (generally) | <span>&#8730;</span>x or log(x)
Left Tailed Distributions (generally) | x<span>&sup2;</span>   
  
  
In practice, you could consider Box-Cox transformations on all variables with skewed distributions before computing correlations or creating scatterplots. This will increase the chances that you will find and interpret important associations between variables.

https://www.toptal.com/designers/htmlarrows/math/

## Comparing Groups: Tables and Visualizations

Marketing analysts often investigate differences between groups of people. Do men or women subscribe to our service at a higher rate? Which demographic segment can best afford our product? Does the product appeal more to homeowners or renters? The answers help us to understand the market, to target customers effectively, and to evaluate the outcome of marketing activities such as promotions.  
  
Such questions are not confined to differences among people; similar questions are asked of many other kinds of groups. One might be interested to group data by geography: does Region A perform better than Region B? Or time period: did same- store sales increase after a promotion such as a mailer or a sale? In all such cases, we are comparing one group of data to another to identify an effect.  
  
  
##### In R code in general:  
• When writing for() loops, use seq_along() instead of 1:length() (Sect. 5.1.2).  
• For if() and for() blocks, always use brackets (“{” and “}”) for improved readability and reliability (Sect. 5.1.3).  
• When creating a data object from scratch, pre-populate it with missing data (NA) and then fill it in, for speed and reliability (Sect. 5.1.1).  

##### When describing and visualizing data for groups:  
• The by() command can split up data and automatically apply functions such as mean() and summary() (Sect. 5.2).  
• aggregate() is even more powerful: it understands formula models and pro- duces a reusable, indexable object with its results (Sects. 5.2 and 5.2.1).  
• Frequency of occurrence can be found with table(). For count data, especially when using formulas, xtabs() is useful (Sect. 5.2.2).  
• Charts of proportions and occurrence by a factor are well suited to the lattice package histogram() command (Sect. 5.2.2).  
• Plots for continuous data by factor may use barchart(), or even better, box- and-whiskers plots with boxplot() (Sect. 5.2.4) or bean plots (Sect. 3.4.2). The lattice package extends boxplots to multiple factors using formula specifica- tion in the bwplot() command (Sect. 5.2.4).  
  
  
Recommended Books.  
Norman Matloff’s The Art of R Programming.  
Sarkar’s Lattice.  




