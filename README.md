# CanterburyRegression
Accurate multi-parameter symbolic regression to find best-fit multivariate [rational functions](https://en.wikipedia.org/wiki/Rational_function) (also known as [Padé, Chrisholm or Canterbury approximants](https://en.wikipedia.org/wiki/Pad%C3%A9_approximant), for 1, 2 or 3+ independent variables respectively). This is implemented in a spreadhseet with visual basic code. Rational Functions ideal for regressions to empirical data, and for approximating complex analytical formulae. They have the following form:

#### Univariate form (Padé approximants)
If you provide only two columns of data (f and x), the program finds candidate best-fit equations in the following form of rational function:

&nbsp;&nbsp;*f* = (*a<sub>0</sub> + a<sub>1</sub>·x + a<sub>2</sub>·x² +...+ a<sub>n</sub>·x<sup>n</sup>*) / (*b<sub>0</sub> + b<sub>1</sub>·x + b<sub>2</sub>·x² +...+ b<sub>m</sub>·x<sup>m</sup>*)
   
Where *a*<sub>i</sub> and *b*<sub>j</sub> are coefficients, and the first non-zero value of *b*<sub>j</sub> is set to 1 to ensure a unique set of coefficients. Conventional Padé approximants always start with *b*<sub>0</sub>=1 in the denominator, e.g. *f*=1/(1+*x²*). However, this program can also search for equations with *b*<sub>i</sub>=0, e.g. *f*=1/*x²*, checking that the denominator never becomes zero (or changes sign) for the given input data.

#### Multivariate form (Canterbury approximants), *f*(*x*,*y*,*z*...)
If you provide 2 or 3 independent variables (e.g. x,y,z), in addition to *f*-values, the program finds candidate best-fit equations of the form:

&nbsp;&nbsp;*f* = &sum;<sub>(i,j,k)&isin;N</sub> (*a<sub>ijk</sub>·x<sup>i</sup>·y<sup>j</sup>·z<sup>k</sup>*) / &sum;<sub>(i,j,k)&isin;N</sub> (*b<sub>ijk</sub>·x<sup>i</sup>·y<sup>j</sup>·z<sup>k</sup>*)
  
Where either *a*<sub>i</sub> and *b*<sub>i</sub> are coefficients, and the first non-zero value of *b*<sub>i</sub> is set to 1 to ensure a unique set of coefficients.  

### Program features
Symbolic regression is a very useful branch of machine learning. There exist commercial genetic algorithm codes (e.g. Eureqa, TuringBot, DataRobot) and deterministic codes based on polynomials (e.g. Mathworks function *Pade()*).

### How to use the program
- **STEP 1**: Enter a data set in sheet ***1.Data***:
  - i.e. enter *f*-values (regressand) in column A, and up to 3 regressor values (*x,y,z*) in columns B to D, of sheet ***1.Data***. There is no limit on the number of rows of data.
  - If the *f*-values have different weights, enter these in column E. If all the *f*-values have the same uncertainty (i.e. standard least-squares regression), then you can leave column E empty. If each value of *f* has an individual standard deviation (i.e. [heteroskedastic](https://en.wikipedia.org/wiki/Heteroscedasticity)), then enter 1/&sigma; in column E. For example, if the uncertainty is proportional to the *f*-values (i.e. constant percent standard deviation), then enter weight 1/*f* in column E.
- **STEP 2**: Adjust the user-definable settings in sheet ***2.Options***.  These settings include the maximum exponent of variables in the numerator and denominator of the rational function, and the maximum number of polynomial coefficients permitted. These options help to speed up the search process. The search algorithm will try all combinations of variables and exponents up to the user-defined limit.
- **STEP 3**: Click on the tab for sheet ***3.Analyze***, and wait for results to appear in sheet ***4.Results***:
  - The solver to generates all combinations of rational functions with up to the given number of coefficients.
  - For each function, the polynomial coefficients are fitted by SVD ([Singular-Value Decomposition](https://en.wikipedia.org/wiki/Singular_value_decomposition)) that can omit outliers with a user-defined tolerance.
  - All fitted equations are tested for singularities in the denominator.
  - All fitted equations that pass the test are output in [Horner's nested form](https://en.wikipedia.org/wiki/Horner%27s_method), for fastest possible calculation. 
  - For each equation, statistics are reported including *[R²](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient)*, *[X²](https://en.wikipedia.org/wiki/Chi-squared_distribution)*, [mean and maximum absolute error]((https://en.wikipedia.org/wiki/Mean_absolute_error)), and [Akaike Information Criterion](https://en.wikipedia.org/wiki/Akaike_information_criterion).
- **STEP 4**: Select your preferred equation by sorting the results in sheet ***4.Results*** by a statistic of your choice in columns B-G. The best candidate equations are flagged in column *Pareto*.

### Installation and activation
- Simply download the spreadsheet file and open it in Microsoft Excel. No installation or registration is needed.
- However, this is a Visual Basic macro-enabled spreadhseet. You must activate macros for it to function: 
  - When you open the file for the first time in Excel, you will see a yellow bar at the top of the window, with the message *"PROTECTED VIEW Be careful... [Enable Editing]"*. Click on the 'Enable Editing' button. 
  - Next, depending on the security settings on your installation of Microsoft Excel, a red bar may appear at the top of the window, with the message *"BLOCKED CONTENT Macros in this document have been disabled..."*. This can be solved by moving the file to a directory on your PC that you designate for files that you trust, then open the file in Excel. To designate a 'trusted directory', click on **File > Options > Trust Center > Trust Center Settings > Trusted Locations > Add new location**, then browse to a directory, e.g. C:\TEMP\. Finally check that **Trust Center Settings > Trusted Documents > Disable Trusted Documents**  is not ticked.
  - When macros are properly activated, a small square splash-screen will appear when you open the file. This splash screen shows the licence info, and advises you if an update is available for download from GitHub. Simply press 'Close' button to close the splash-screen. 
  - If still no splash-screen appears, then you might be able to fix it by menu option **File > Options > Trust Center > Trust Center Settings > Macro Settings > Disable all macros with notification**, which is a suitable level of security.
  
### License & warranty
- Distributed under the GLP v3 lisence (https://www.gnu.org/licenses/gpl-3.0.en.html). Please acknowledge/attribute use of this software in your report/publication with an appropriate author citation and URL to this site.
- Provided without warranty of any kind.

### Author & copyright owner
© Peter.Schild@OsloMet.no
