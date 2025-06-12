# MTFI_short
$~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~$
## Overview
This is the source code and summary of datasets used for the short paper, which aims to investigate and model the relationship between characteristics of traffic infrastructure and the presence of e-scooter accidents, with a focus on curb and complexity of street views.
$~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~$
## Table of Contents
### [Data & Software](#data-and-software)
### [Functions](#mtp_function_yl)
### Workflow
Preproccessing and image data preparation
- [Obtain Google Street View Images](#work_01_googlestreetviewimages_processing) 
  
Image segmentation and calculation of mask properties
- [Apply Segment Anything Model(SAM) and filtering output masks](#work_02_imagesegmentation_maskfiltering)
- [Detect contours and calculate mask properties](#work_03_contourdetection_maskpropertiescalculation)
- [Interpret masks and label](#work_04_maskinterpretationandlabelling)
- [Statistical analysis of mask properties](#work_05_maskpropertiesstatisticsdistribution)

Generation of Pseudo-absence points and processing image data
- [Obtain GSV images of pseudo-absence points, apply SAM, calculate mask properties](#work_06_randompseudopoints_gsvimages_segmentation_maskfiltering)

Construction of classification models
- [Build classification models](#work_07_buildingclassificationmodel_curbextraction_entropycalculation)
- [Apply classification models to extract curbs and calculate entropy values](#work_08_maskpropertiescalculation_entropycalculation)

Preparation of variables
- [Prepare curb-related variables and entropy variables](#work_09_variablespreparation_curbrelated_entropyvariables)
- [Prepare traffic transport infrastructure variables](#work_10_variablespreparation_traffictransportinfrastructurevariables)
- [Variables transformation](#work_11_variablestransformation)

Modelling
- [Logistic regression analysis and random forest classification](#work_12_modellingpresenceofaccident)

Data Visualization
- [Map and illustration](#work_13_datavisualization_illustrationfigures)

$~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~$
## Data and Software
- Data sources:
    - Google Street View Images, accessed through static API by the [Google Maps Platform](https://developers.google.com/maps/documentation/streetview/overview).
    - Traffic, transport and infrastructure datasets, obtained from [Open Data Zurich](https://data.stadt-zuerich.ch/).
    - Supplementary traffic, transport and infrastructure data, queried from [Open Street Map](https://www.openstreetmap.org).
- Model application:
    - [Segment Anything Model](https://github.com/facebookresearch/segment-anything)
- Software used for data preprocessing:
    - [QGIS](https://qgis.org/project/overview/)
- Python packages
    - [pytorch](https://pytorch.org/)
    - [opencv](https://pypi.org/project/opencv-python/)
    - [numpy](https://numpy.org/)
    - [mlxtend](https://rasbt.github.io/mlxtend/)
    - [pandas](https://pandas.pydata.org/)
    - [matplotlib](https://matplotlib.org/)
    - [seaborn](https://seaborn.pydata.org/)
    - [shapely](https://shapely.readthedocs.io/en/stable/)
    - [sklearn](https://scikit-learn.org/stable/)
    - [scipy](https://scipy.org/)
    - [category_encoders](https://pypi.org/project/category-encoders/)
    - [joblib](https://joblib.readthedocs.io/en/stable/)
    - [pyproj](https://pyproj4.github.io/pyproj/stable/)
    - [PIL](https://pypi.org/project/pillow/)
    - [statsmodels](https://www.statsmodels.org/stable/index.html)
    - [geoplot](https://residentmario.github.io/geoplot/)
    - [geopandas](https://geopandas.org/en/stable/)
    - [glob](https://docs.python.org/3/library/glob.html)
    - [shapefile](https://pypi.org/project/pyshp/)
    - [folium](https://python-visualization.github.io/folium/latest/)
    - [pathlib](https://docs.python.org/3/library/pathlib.html)
    - [cartopy](https://pypi.org/project/Cartopy/)
    - [math](https://docs.python.org/3/library/math.html)
    - [cmasher](https://pypi.org/project/cmasher/)
    - [earthpy](https://earthpy.readthedocs.io/en/latest/)
    - [urllib](https://docs.python.org/3/library/urllib.html)
    - [tabulate](https://pypi.org/project/tabulate/)
    - [os](https://docs.python.org/3/library/os.html)
    - [torchvision](https://pypi.org/project/torchvision/)
    - [google_streetview](https://pypi.org/project/google-streetview/)

$~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~$
## Scripts
#### Work_01_GoogleStreetViewImages_Processing
- Transforming location to coordinates
- Accessing Google Street View (GSV) images using API
- Setting identifier to location points

#### Work_02_ImageSegmentation_MaskFiltering
- Applying Segment Anything Model (SAM) for image segmentation
- Writing functions to convert and output masks, to filter out overlapping subset masks

#### Work_03_ContourDetection_MaskPropertiesCalculation
- Writing functions to detect, filter and plot contours
- Writing functions to calculate mask properties
  
#### Work_04_MaskInterpretationandLabelling
- Selecting images for labelling
- Writing functions to interpret and label masks

#### Work_05_MaskPropertiesStatisticsDistribution
- Summarising all labelled masks
- Categorising labels into label groups
- Checking statistical distribution of mask properties for different label groups
- Comparing distribution of mask properties between curb and other label groups

#### Work_06_RandomPseudoPoints_GSVImages_Segmentation_MaskFiltering
- Loading generated random pseudo points and converting to coordinates
- Accessing GSV images of random pseudo points
- Setting identifier for random pseudo points
- Applying SAM and filtering masks using written functions for random pseudo points

#### Work_07_BuildingClassificationModel_CurbExtraction_EntropyCalculation
- Constructing classification models for extraction of curbs
- Constructing classification models for calculating whole scene entropy
- Constructing classification models for calculating ground scene entropy

#### Work_08_MaskPropertiesCalculation_EntropyCalculation
- Calculating mask properties of all mask output from both accident and pseudo locations
- Applying classification models to predict label group
- Adding calculation of image entropy
- Calculating entropy variables and summarising together

#### Work_09_VariablesPreparation_CurbRelated_EntropyVariables
- Summarising curb related variables, entropy variables 

#### Work_10_VariablesPreparation_TrafficTransportInfrastructureVariables
- Preparing traffic count, and other traffic transport infrastructure variables and summarising

#### Work_11_VariablesTransformation
- Performing data transformation for both numerical and categorical variables

#### Work_12_ModellingPresenceofAccident
- Checking correlation and multicollinearity of variables and building independent variable set
- Performing logistic regression analysis
- Applying random forest classification

#### Work_13_DataVisualization_IllustrationFigures
- Plotting map for data visualization
- Preparing illustration figures for examples of SAM application and curb extraction

#### mtp_function_yl
- Functions for SAM application, mask conversion and output
- Functions for contour detection, filtering and plotting
- Functions for calculation of mask/contour properties, including geometric attributes and spectral features
- Functions for calculation of color distance between RGB points to gray line
- Functions for summarising above-mentioned properties
- Functions for calculating entropy and image entropy
- Functions for printing result of regression
- (Functions for performing feature selection, checking distribution of variables)

