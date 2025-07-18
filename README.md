**THIS REPO IS FOR A CURRENTLY IN PROGRESS PROJECT AND IS NOT YET FINALIZED**

# Ohio Weasel Distribution Models (2025)
This repo covers the scripts and data used to model the distribution/habitat suitability of long-tailed, short-tailed, and least weasels in the state of Ohio. Multiple versions of this project are included here such as preliminary modeling efforts presented at the Ohio University Student Expo ([PDF](https://github.com/oxyppgyn/oh-weasel-dist-model/blob/b1d665f112f0b6d399843dc565a8ef20387e6f89/OUStudentExpo/oh-weasel-dist-model_Poster_Expo.pdf)) and the American Society of Mammalogists Annual Meeting ([PDF](https://github.com/oxyppgyn/oh-weasel-dist-model/blob/91d631e96cbdc7e52ed8156262d2f6d122afc1b7/ASM/oh-weasel-dist-model_Poster_ASM.pdf)).

## Data & Documentation
Due to some data in this dataset provided by the Ohio Department of Natural Resources and Cleveland Metroparks not being public, only part of the original dataset used for these analyses has been added to this repo. The full dataset may be available upon request. Running this analysis with a partial dataset _will_ produce differing results. After filtering, the datasets between both iterations (OU Student Expo and ASM) are the same, but copies of these files are included in both folders.

Information about the data tables can be found in `oh-weasel-dist-model_datadict.json`, which contains metadata for each field formatted as JSON.

## Rerun this Analysis
All analyses were performed using R 4.4.0 via RStudio and ArcGIS Pro 3.3.0. If you are interested in using parts of the code created for this project for a different analysis using the _intSDM_ package, the code used for the American Society of Mammalogists annual meeting may be the best starting point as it was written to be more dynamic and allow for different datasets with minimal changes.

### Ohio University Student Expo
* Download the pre-generated boundary shapefile `OH_buffer_1km.shp` and covariate tiff file `OH_NLCD_Forest_2023.tif`.
* Run the provided R notebook `oh-weasel-dist-model_Expo.Rmd` to create the iSDMs used and their related distribution maps.

### American Society of Mammalogists (ASM) Annual Meeting
* Download the aspect tiff file from [STRMGL3](https://portal.opentopography.org/raster?opentopoID=OTSRTM.042013.4326.1), which is used to derive eastness and northness (components of aspect).
  * In box 1 ("Coordinates"), select "Manually enter selection coordinates" and use the following values:

    Xmin | Ymin | XMax | YMax
    --|--|--|--
    -85.155029296875 | 38.161016176890456 | -80.16723632812499 | 42.188337776657335

    _The boundary can also be selected on the map on this page as long as it is includes at least the entire state of Ohio plus at a 1km buffer on all sides._

  * In box 3A ("Raster Visualization") check "Aspect".
  * Click the submit button at the bottom of the page and wait for your download.
* Run the provided Python notebook `oh-weasel-dist-model_ASM.ipynb` to create raster and polygon layers used in this analysis. This uses _arcPy_ through ArcGIS Pro, but the same processes could be done relatively easily through R's geospatial libraries as well.
* Run the provided R notebook `oh-weasel-dist-model_ASM.Rmd` to create the iSDMs used and their related distribution maps.

