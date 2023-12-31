# SK-surge-mapping
Scripts developed to map surface velocity and elevation changes on Sít' Kusá (Turner Glacier), southeast Alaska. The customized NASA geogrid and autoRIFT script (custom_geogrid_autoRIFT_opt.ipynb) may be broadly applied to optical satellite image pairs from PlanetScope, Sentinel-2, and Landsat 7-9. The calculation of stable surface error (calculate_vmap_SSE.ipynb) may also be used to calculate the velocity error associated with each of the output velocity maps. 

Contact jukesliu@u.boisestate.edu with any questions.

## Overview
The code repository contains 4 main scripts which should be run in the following order:

**1) custom_geogrid_autoRIFT_opt.ipynb**
This script utilizes geogrid and autoRIFT algorithms to generate georeferenced velocity maps over an area of interest at custom resolutions. The workflow can be applied to folders containing Sentinel-2, Landsat 7-9, or PlanetScope images. The dates (yyyymmdd) must be in the image filenames. One can adjust the analysis parameters (e.g., pixel-tracking search range, chip size, time separation between images). Other inputs include a reference DEM over the area, a stable surface mask, and a reference velocity map. All the images and other inputs must be cropped to the same spatial extent. The [geogrid](https://github.com/leiyangleon/Geogrid) and [autoRIFT](https://github.com/nasa-jpl/autoRIFT) packages must be installed in order to run this script.

![velocity_20200505_20200510_200m_S2](https://github.com/julialiu18/SK-surge-mapping/assets/48999537/8a1748c1-573f-4a30-9618-e7e95c424004)
200 meter resolution velocity map of Sít' Kusá during its 2020 surge produced from a Sentinel-2 image pair from May 5 and May 10 2020. Vectors indicate flow direction and colors indicate speed.

**2) calculate_vmap_SSE.ipynb**
This script utilizes a mask of stable surfaces (where velocities should be 0) within the area of interest and calculates the Root Mean Squared Error (RMSE) in vx, vy, and speed as a measure of velocity map accuracy.

**3) evaluate_custom_autoRIFT_vmaps.ipynb**
Extracts velocity time series along glacier centerlines or at specific points on the glacier using input centerline/point shapefiles. 

**4) centerline_elevation_processing.ipynb**
Extracts elevation time series along glacier centerlines from Digital Elevation Models (DEMs) stored in .tif files and visualizes elevation change, surface slope, etc. For the extraction of elevation profiles, the glacier centerline shapefile should consist of evenly-spaced circles along the centerline. Elevations are averaged within each circle.
