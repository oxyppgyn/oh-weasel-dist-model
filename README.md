**THIS REPO IS FOR A CURRENTLY IN PROGRESS PROJECT AND IS NOT YET FINALIZED**

# Ohio Weasel Distribution Models (2025)
This repo covers the scripts and data used to model the distribution of long-tailed, short-tailed, and least weasels in the state of Ohio. Multiple versions of this project are included here such as preliminary modeling efforts presented at the Ohio University Student Expo and the American Society of Mammalogists Annual Meeting.

## Data & Documentation
Due to some data in this dataset provided by the Ohio Department of Natural Resources and Cleveland Metroparks not being public, only part of the original dataset used for these analyses has been added to this repo. The full dataset may be available upon request. Running this analysis with a partial dataset _will_ produce differing results.

Information about the data tables can be found in [oh-weasel-model_datadict.json](https://github.com/oxyppgyn/oh-weasel-dist-model/blob/643d11495c15efdd9e97da767acc88085d82c718/oh-weasel-model_datadict.json), which contains metadata for each field formatted as JSON.

## Rerun this Analysis
### OU Student Expo
* Download the [National Land Cover Database (2021)](https://www.mrlc.gov/downloads/sciweb1/shared/mrlc/data-bundles/Annual_NLCD_LndCov_2021_CU_C1V0.tif) tiff file, which is used to derive land cover covariates.
* Run the provided Python notebook `oh-weasel-dist-model_Expo.ipynb` to create raster and polygon layers used in this analysis. This uses _arcPy_ through ArcGIS Pro, but could be done through R's geospatial libraries as well.
* Run the provided R notebook `oh-weasel-dist-model_Expo.Rmd` to create the iSDMs used and their related distribution maps.

### American Society of Mammalogists (ASM) Annual Meeting
* Download the [National Land Cover Database (2020)](https://www.mrlc.gov/downloads/sciweb1/shared/mrlc/data-bundles/Annual_NLCD_LndCov_2000_CU_C1V0.tif) tiff file, which is used to derive land cover covariates.
* Download elevation and aspect tiff files from [STRMGL3](https://portal.opentopography.org/raster?opentopoID=OTSRTM.042013.4326.1), which is used as a covariate (elevation) and to derive eastness and westness (aspect).
  * In box 1 ("Coordinates"), select "Manually enter selection coordinates" and use the following values:

    Xmin | Ymin | XMax | YMax
    --|--|--|--
    -85.155029296875 | 38.161016176890456 | -80.16723632812499 | 42.188337776657335

    _The boundary can also be selected on the map on this page as long as it is includes the entire state of Ohio plus at a 1km buffer on all sides._

  * In box 3A ("Raster Visualization") check "Color-relief" and "Aspect"
  * Click the submit button at the bottom of the page and wait for your download.
* Run the provided Python notebook `oh-weasel-dist-model_ASM.ipynb` to create raster and polygon layers used in this analysis. This uses _arcPy_ through ArcGIS Pro, but could be done through R's geospatial libraries as well.
* Run the provided R notebook `oh-weasel-dist-model_ASM.Rmd` to create the iSDMs used and their related distribution maps.

