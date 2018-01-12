## SedSAS

###Sediment Size Analysis by Sieve  or  Sediment Size Analysis System


## Part I: Introduction:

SedSAS is a class object written in the Python programming language. Its purpose is to provide a set of basic statistical and visualization tools for analyzing unconsolidated sediment size-fraction samples collected in the field and separated using either mechanical sieves or similar analog partition-by-size methods. The class performs the following computations and/or visualizations:

- compute weight percentages and cumulative weight percentages for each size-fraction weight class relative to the total sample.

- derive and compute the mean, sorting (standard deviation) in $\phi$ units, along with skewness, and kurtosis using the logarithmic method described by Folk and Ward (1957) and Folk (1974, 1980). This graphic method is perhaps the most widely used in the geosciences.

- derive and compute the mean, sorting (standard deviation) in millimeter units, along with skewness, and kurtosis using the graphic geometric method described by Folk and Ward (1957).

- derive and compute the mean, sorting (standard deviation) in millimeter units, along with skewness, and kurtosis using the arithmetic method of moments.

- derive and compute the mean, sorting (standard deviation) in millimeter units, along with skewness, and kurtosis using the geometric method of moments.

- derive and compute the mean, sorting (standard deviation) in $\phi$ units, along with skewness, and kurtosis using the logarithmic method of moments.


- identify (the first three) distribution modes in $\phi$ and millimeter units.

- generate a histogram (bins=#sieves) with frequency (PDF) curve and cumulative frequency (CDF) curve for sample weight percentages and cumulative weight percentages, respectively.


SedSASClass.py is a stand-alone ASCII-compliant text file with UNIX record delimiters (\n). It is designed as a Python class, to be imported and instantiated from within an external user-built Python script. 
    <br><br>
    <br><br>

## Part II: Requisite Python Libraries:
SedSASClass will attempt to load: numpy, pandas, and matplotlib at instantiation. 

import numpy as np<br>
import pandas<br>
import matplotlib.pyplot as plt<br>
    <br><br>
    
## The most thorough documentation for the class is to be found in the Jupyter Notebook: SedimentSizeAnalysisbySieveNotebook, found elsewhere in this repository.
<br><br>



## Part III: Notes:
1. SedSASample was written and tested in a Python 3.x environment. It should work under 2.7.x conditions, but do test before proceeding with production work.

2. SedSASample doesn't [yet] do much error handling and so, if something goes wrong expect to see a jumble of obscure tracebacks and other text that may or may not make much sense. Error handling is being folded into the class, but it may never be implemented sufficiently to cover every possible event. 

3. If you do not already have Python installed (Windows users), or only have the core interpreter (Linux, Unix, and OSX users), suggest installing Continuum Analytic's Anaconda distribution. Anaconda contains a really nice softare application package manager called conda that makes it easy to install and updated a Python environment, or environments. Get it here: https://www.continuum.io/downloads


**Included sample scripts:**  Actually, just sample data sets, for now. These work with the example scripts presented in SedimentSizeAnalysisbySieveNotebook, a Jupyter Notebook that also just happens to document much of the internals and user interface(s) for the class.
    <br><br>
    <br><br>
## Part IV: User-callable Class Methods:
- **InterpolateQuantileValues:** interpolates/extrapolates the sample data values for the 5th, 10th, 16th, 25th, 50th, 75th, 86th, 90th, and 95th quantiles (per Folk, 1980). Quantiles are required for statistics generated by: ComputeFWLogarithmicGraphicStats andComputeFWGeometricGraphicStats. Both methods call InterpolateQuantileValues internally during execution. The user will generally have no need to call this method, but can do so if desired.
    <br><br>
- **ComputeFWLogarithmicGraphicStats:** compute logarithmic graphical statistics (mean, sorting (standard deviation), skewness, and kurtosis) for the sample data as described by Folk and Ward, 1957, Folk, 1980 and others. _This has long been the most common method used in sedimentology to characterize sediment particle size._
    <br><br>
- **ComputeFWGeometricGraphicStats:** compute geometric graphical statistics (mean, sorting (standard deviation), skewness, and kurtosis) for the sample data as described by Folk and Ward, 1957.
    <br><br>
- **ComputeArithmeticMethodofMomentsStats:** computes the mean, sorting (standard deviation), skewness, and kurtosis for the sample data using the arithmetic method of moments (Ref).
    <br><br>
- **ComputeGeometricMethodofMomentsStats:** computes the mean, sorting (standard deviation), skewness, and kurtosis for the sample data using the geometric method of moments (Ref).
    <br><br>
- **ComputeLogarithmicMethodofMomentsStats:** computes the mean, sorting (standard deviation), skewness, and kurtosis for the sample data using the logrithmic method of moments (Ref).
    <br><br>
- **FindSampleModes:** locates and reports [up to] the first three sample mode values seen in the sample data
    <br><br>
- **PrintSampleWeightsDataTable:** prints the sample weights, percent sampled weights, cumulative weights, and sample quantile values to standard out.
    <br><br>
- **PrintGraphicStats:** prints the graphical statistics generated by method ComputeLogGraphicStats and ComputeGeomGraphicStats, formatted to standard out (console). _This is an internal method not usually called directly by the user_.
    <br><br>
- **PrintMomentStats:** prints the method of moment based statistics generated by method ComputeMomentStats formatted to standard out (console)
    <br><br>
- **PrintSampleModes:** prints the modal values detected in the data by method FindSampleModes formatted to standard out (console). THIS METHOD IS DEPRECATED AND WILL BE REMOVED IN A FUTURE VERSION OF THE CLASS.
    <br><br>
- **PLOTSampleWtPercents:** generates a histogram of weight percentage values for given sample as generated in the class constructor (__init__) and stored in the dataframe df
    <br><br>
- **PLOTSampleCumWtPercents:** generates a cumulative frequency curve (line) of weight percentage values for given sample as generated in the class constructor (__init__) and stored in the dataframe df
    <br><br>
- **PLOTDualSampleWeightPercents:** generates both a histogram and a cumulative frequency curve (line) of weight percentage values for given sample as generated in the class constructor (__init__) and stored in the dataframe df. This is a convenience method that combines the work of PLOTSampleWtPercents and PLOTSampleCumWtPercents into a single function call.
<br><br>
- **GetDataFrame:** returns a copy to the pandas data frame df that is built in the SedSASampleClass constructor during initialization and is used throughout the class methods for subsequent computations and reporting. This method will likely prove to be useful when calling SedSASampleClass methods directly (rather than doing streamlined processing-see below).
    <br><br>
- **GetQuantileList:** returns a Python list of interpolated/extrapolated values for the 5th, 10th, 16th, 25th, 50th, 75th, 86th, 90th, and 95th quantiles, based on the CDF. 
<br><br>


