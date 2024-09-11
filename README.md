# CLIGEN Version 5


Cligen (ClImate GENerator) is a stochastic weather generator which produces daily estimates of precipitation, temperature, dewpoint, wind, and solar radiation for a single geographic point, using monthly parameters (means, SD's, skewness, etc.) derived from the historic measurements. 
Unlike other climate generators, it produces individual storm parameter estimates, including time to peak, peak intensity, and storm duration, which are required to run the WEPP and the WEPS soil erosion models. 

For more information on CLIGEN see the USDA webpage at: (https://www.ars.usda.gov/midwest-area/west-lafayette-in/national-soil-erosion-research/docs/wepp/cligen/)

The orginal version was written in the 1990's by Arlin Nicks. The version 5 releases include the addition of quality control on the output values to test that the generated values are matching the statistics of the input parameter file.

This repository has the version 5 releases:
- **Version 5.522.63** - In SR USR_OPT variable NDFLAG was not being initialized unless the type of run was 6 or 8.  Added a default "else" to the loop to set it to zero.
- **Version 5.522.64** - In SR R5MONB variable WI(I) which is used to calculate AI, was getting hosed when F went negative.  This would mess up Ip for very dry climates where the average number of rainfall events is less than 0.5
- **Version 5.30** - Corrected dew point calculation for a type 6 run. Dew point was not being calculated from tmin and tmax values read from the observed input.
- **Version 5.32** -
    + Changed order of reading in wet/wet & wet/dry Equivalence statement had interleaved the values making them incorrect Affected only Yoder-Foster & Fourier interpolation From WEPS 5.30001
    +  Extended character string length for reading command line arguments to allow longer output path length on linux. Should now allow paths as long as WEPS. Path length on Windows was already longer than maximum allowed. From WEPS 5.30002
    +  Corrected solar radiation, it was not using standard deviations from input par file. Increased year field to 5 digits for 10000 year+ runs.
    +  Using observed option (type=6) the tpeak variable was being generated based only the cligen predicted days with precip so most days with observed data had tpeak=0. Updated to make sure type 6 input has the same distribution of tpeak as generated precip.
- **Version 5.321** - Fix for leap years to include years divisible by 400 but not divisible by 100
- **Version 5.322** - Corrected calculation of Coefficient of Variation so a zero monthly average temperature does not cause a divide by zero. Merged change from WEPS version 5.3004 12/13/18. Note that WEPS change 5.30003 is not included since it also was a correction for leap years already implememted in 5.321.


Older original version 4 releases of CLIGEN are at: (https://github.com/jfrankenberger/cligen4)
