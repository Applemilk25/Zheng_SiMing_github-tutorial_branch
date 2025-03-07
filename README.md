## Si Ming's github-tutorial README

# Wildfire Fuel Classification with LiDAR Data

## Project Overview
This project integrates LiDAR-based metrics into wildfire fuel classification to improve accuracy and enhance wildfire management strategies. By refining fuel type classification, this research supports:

- More effective wildfire risk assessments for emergency response teams.
- Improved land management policies to reduce fire hazards.
- Enhanced resource allocation for fire suppression efforts.

## Why This Research Matters
Wildfires are increasing in frequency and intensity due to climate change, posing significant risks to communities, ecosystems, and infrastructure. Traditional wildfire risk mapping methods often rely on expert interpretation and aerial photography, which can lead to classification errors. This project enhances wildfire fuel classification by leveraging LiDAR technology, providing:

- More accurate fire behavior predictions through high-resolution fuel maps.
- Improved wildfire response and mitigation strategies.
- Better-informed forest management and policy decisions to reduce risk in high-priority areas.

## Research Objectives
- Enhance VRI fuel type classification with LiDAR data.
- Identify spatial patterns in forest fuel distribution.
- Improve wildfire management through more accurate fuel type mapping.
- Validate the effectiveness of LiDAR augmentation using comparative analysis.

## Study Area
The study is focused on the Resort Municipality of Whistler (RMOW), which spans 245 km², featuring mountainous terrain, dense forests, and fire-prone ecosystems. The study area has a history of significant wildfire events, and this project aims to improve fuel classification to mitigate future risks.

## Methodology
### 1. Data Acquisition & Preprocessing
- Processed LiDAR point cloud data using the `lidR` package in R.
- Removed noise, duplicates, and outliers.
- Converted the dataset to EPSG:26910 (NAD83 / UTM zone 10N).

### 2. Terrain Normalization & CHM Generation
- Created a 2m resolution Digital Terrain Model (DTM).
- Generated a Canopy Height Model (CHM).
- Filtered vegetation below 2m to remove understory noise.

### 3. Tree Detection & Feature Extraction
- Used a local maximum filter (LMF, 5m window) for tree detection.
- Extracted tree metrics, including:
  - Tree Height
  - Canopy Area
  - Aspect Ratio (height to width)
  - Canopy Curvature (surface curvature measurement)
- Integrated LiDAR-derived tree attributes into an enhanced VRI dataset.

### 4. Augmenting VRI Fuel Types
- Applied the Canadian Fire Behavior Prediction (FBP) System fuel classification.
- Mapped conifer percentage across RMOW.
- Created a geodatabase for wildfire risk assessment.

## Key Steps in the R Pipeline
### Data Processing & Normalization
- **Read LAS catalog** and ensure correct CRS (EPSG:26910).
- **Remove duplicate points** and **normalize height** using the DTM.
- **Filter extreme outliers** by dropping heights below 0m and above 100m.

### Canopy Height Model & Curvature Analysis
- **Compute CHM** and remove vegetation below 2m.
- **Calculate canopy curvature** to assess tree structure.

### Tree Detection & Segmentation
- **Detect tree tops** using a local maximum filter.
- **Apply Watershed Segmentation** to delineate tree crowns.
- **Compute tree metrics** including height, area, and aspect ratio.
- **Extract curvature within tree crowns** to analyze canopy structure.

### Visualization & Output
- Generate and save **canopy area maps**.
- Generate and save **tree height maps**.
- Generate and save **aspect ratio maps**.
- Export tree statistics to a CSV file for further analysis.

## Challenges & Limitations
- **Lack of ground-truth validation data**.
- **Potential misclassification in open-canopy conifer stands**.
- **Computational complexity** of tree segmentation.

## Results & Interpretation
- **Higher resolution mapping** provides more detailed tree and canopy detection.
- **Improved classification accuracy** enhances fuel type differentiation.
- **Enhanced VRI maps** correct previous classification errors.
- **Visualization outputs** show the spatial distribution of fuel types and tree metrics.

## Dependencies
This project requires the following R packages:
```r
library(spatialEco)
library(lidR)
library(terra)
library(sf)
library(data.table)
library(ggplot2)
library(scales)
```

## Running the Project
1. **Set file paths** for LAS input and output directories.
2. **Run the preprocessing pipeline** to normalize terrain and generate CHM.
3. **Extract tree metrics** and analyze tree canopy features.
4. **Run visualization scripts** to generate maps and statistics.

## Acknowledgments
This research builds on methodologies from LiDAR-based forest analysis and wildfire risk assessment. The study contributes to improved wildfire management and land-use planning strategies.

For more details, visit the project site: [Si Ming’s E-Portfolio](https://applemilk25.github.io/E-Portfolio/).

this is the file structure

RMOW Fueltyping with LiDAR/
│
├── docs/             
│   ├── index.md     
│   ├── proposal.docx  
│   └── FinalReport.docx 
│
├── data/            
│   ├── .LAZ LiDAR files
│
├── scripts/         
│   ├── RMOWFueltypingV5.Rmd
│   └── generate_resultsV2.R  
│
├── figs/             
│   └── boxplot.png
│
├── .gitignore       
├── README.md        
├── LICENSE          
