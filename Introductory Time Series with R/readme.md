# Introductory Time Series with R
<img src="./cover.png" alt="" height="300">

* **Publisher** http://www.springer.com/gp/book/9780387886978

## TOC
### Time Series Data 15
* Purpose 15  
* Time series 16  
* R language 17  
* Plots, trends, and seasonal variation 18  
  * A flying start: Air passenger bookings 18  
  * Unemployment: Maine 21  
  * Multiple time series: Electricity, beer and chocolate data 24  
  * Quarterly exchange rate: GBP to NZ dollar 28  
  * Global temperature series 30  
* Decomposition of series 33  
  * Notation 33  
  * Models 33  
  * Estimating trends and seasonal effects 34  
  * Smoothing 35  
  * Decomposition in R 36  
* Summary of commands used in examples 38  
* Exercises 38  

### Correlation 40
* Purpose 40  
* Expectation and the ensemble 40  
  * Expected value 40  
  * The ensemble and stationarity 43  
  * Ergodic series* 44  
  * Variance function 45  
  * Autocorrelation 46  
* The correlogram 48  
  * General discussion 48  
  * Example based on air passenger series 50  
  * Example based on the Font Reservoir series 53  
* Covariance of sums of random variables 54  
* Summary of commands used in examples 55  
* Exercises 55  

### Forecasting Strategies 57
* Purpose 57  
* Leading variables and associated variables 57  
  * Marine coatings 57  
  * Building approvals publication 58  
  * Gas supply 61  
* Bass model 63  
  * Background 63  
  * Model definition 63  
  * Interpretation of the Bass model* 63  
  * Example 64  
* Exponential smoothing and the Holt-Winters method 67  
  * Exponential smoothing 67  
  * Holt-Winters method 71  
  * Four-year-ahead forecasts for the air passenger data 74  
* Summary of commands used in examples 76  
* Exercises 76  

### Basic Stochastic Models 79
* Purpose 79  
* White noise 80  
  * Introduction 80  
  * Definition 80  
  * Simulation in R 80  
  * Second-order properties and the correlogram 81  
  * Fitting a white noise model 82  
* Random walks 83  
  * Introduction 83  
  * Definition 83  
  * The backward shift operator 83  
  * Random walk: Second-order properties 84  
  * Derivation of second-order properties* 84  
  * The difference operator 84  
  * Simulation 85  
* Fitted models and diagnostic plots 86  
  * Simulated random walk series 86  
  * Exchange rate series 87  
  * Random walk with drift 89  
* Autoregressive models 91  
  * Definition 91  
  * Stationary and non-stationary AR processes 91  
  * Second-order properties of an AR(1) model 92  
  * Derivation of second-order properties for an AR(1) process* 92  
  * Correlogram of an AR(1) process 93  
  * Partial autocorrelation 93  
  * Simulation 93  
* Fitted models 94  
  * Model fitted to simulated series 94  
  * Exchange rate series: Fitted AR model 96  
  * Global temperature series: Fitted AR model 97  
* Summary of R commands 99  
* Exercises 99  

### Regression102
* Purpose102  
* Linear models103  
  * Definition103  
  * Stationarity104  
  * Simulation104  
* Fitted models105  
  * Model fitted to simulated data105  
  * Model fitted to the temperature series (1970--2005)106  
  * Autocorrelation and the estimation of sample statistics*107  
* Generalised least squares109  
  * GLS fit to simulated series109  
  * Confidence interval for the trend in the temperature series110  
* Linear models with seasonal variables110  
  * Introduction110  
  * Additive seasonal indicator variables110  
  * Example: Seasonal model for the temperature series111  
* Harmonic seasonal models112  
  * Simulation113  
  * Fit to simulated series114  
  * Harmonic model fitted to temperature series (1970--2005)116  
* Logarithmic transformations120  
  * Introduction120  
  * Example using the air passenger series120  
* Non-linear models124  
  * Introduction124  
  * Example of a simulated and fitted non-linear series124  
* Forecasting from regression126  
  * Introduction126  
  * Prediction in R126  
* Inverse transform and bias correction126  
  * Log-normal residual errors126  
  * Empirical correction factor for forecasting means128  
  * Example using the air passenger data128  
* Summary of R commands129  
* Exercises129  

### Stationary Models132
* Purpose132  
* Strictly stationary series132  
* Moving average models133  
  * MA(q) process: Definition and properties133  
  * R examples: Correlogram and simulation134  
* Fitted MA models135  
  * Model fitted to simulated series135  
  * Exchange rate series: Fitted MA model137  
* Mixed models: The ARMA process138  
  * Definition138  
  * Derivation of second-order properties*139  
* ARMA models: Empirical analysis140  
  * Simulation and fitting140  
  * Exchange rate series140  
  * Electricity production series141  
  * Wave tank data144  
* Summary of R commands146  
* Exercises146  

### Non-stationary Models148
* Purpose148  
* Non-seasonal ARIMA models148  
  * Differencing and the electricity series148  
  * Integrated model149  
  * Definition and examples150  
  * Simulation and fitting151  
  * IMA(1, 1) model fitted to the beer production series152  
* Seasonal ARIMA models153  
  * Definition153  
  * Fitting procedure154  
* ARCH models156  
  * S&P500 series156  
  * Modelling volatility: Definition of the ARCH model158  
  * Extensions and GARCH models159  
  * Simulation and fitted GARCH model160  
  * Fit to S&P500 series161  
  * Volatility in climate series163  
  * GARCH in forecasts and simulations166  
* Summary of R commands166  
* Exercises166  

### Long-Memory Processes169
* Purpose169  
* Fractional differencing169  
* Fitting to simulated data171  
* Assessing evidence of long-term dependence174  
  * Nile minima174  
  * Bellcore Ethernet data175  
  * Bank loan rate176  
* Simulation177  
* Summary of additional commands used178  
* Exercises178  

### Spectral Analysis181
* Purpose181  
* Periodic signals181  
  * Sine waves181  
  * Unit of measurement of frequency182  
* Spectrum183  
  * Fitting sine waves183  
  * Sample spectrum185  
* Spectra of simulated series185  
  * White noise185  
  * AR(1): Positive coefficient187  
  * AR(1): Negative coefficient188  
  * AR(2)188  
* Sampling interval and record length189  
  * Nyquist frequency191  
  * Record length191  
* Applications193  
  * Wave tank data193  
  * Fault detection on electric motors193  
  * Measurement of vibration dose194  
  * Climatic indices197  
  * Bank loan rate199  
* Discrete Fourier transform (DFT)*200  
* The spectrum of a random process*202  
  * Discrete white noise203  
  * AR203  
  * Derivation of spectrum203  
* Autoregressive spectrum estimation204  
* Finer details204  
  * Leakage204  
  * Confidence intervals205  
  * Daniell windows206  
  * Padding206  
  * Tapering207  
  * Spectral analysis compared with wavelets207  
* Summary of additional commands used207  
* Exercises208  

### System Identification210
* Purpose210  
* Identifying the gain of a linear system210  
  * Linear system210  
  * Natural frequencies211  
  * Estimator of the gain function211  
* Spectrum of an AR(p) process212  
* Simulated single mode of vibration system212  
* Ocean-going tugboat214  
* Non-linearity216  
* Exercises217  

### Multivariate Models219
* Purpose219  
* Spurious regression219  
* Tests for unit roots222  
* Cointegration224  
  * Definition224  
  * Exchange rate series226  
* Bivariate and multivariate white noise227  
* Vector autoregressive models228  
  * VAR model fitted to US economic series230  
* Summary of R commands235  
* Exercises235  

### State Space Models237
* Purpose237  
* Linear state space models238  
  * Dynamic linear model238  
  * Filtering*239  
  * Prediction*240  
  * Smoothing*241  
* Fitting to simulated univariate time series242  
  * Random walk plus noise model242  
  * Regression model with time-varying coefficients244  
* Fitting to univariate time series246  
* Bivariate time series -- river salinity247  
* Estimating the variance matrices250  
* Discussion251  
* Summary of additional commands used252  
* Exercises252  