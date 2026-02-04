
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.8306855.svg)](https://doi.org/10.5281/zenodo.8306855)

# Mapping environmental injustices within the U.S. prison system

This is the working repository for NASA-funded research mapping
environmental injustices within the U.S. prison system. The project is
currently in Phase 2, building on the initial Phase 1 analysis (see
Project Versions below).

This repository hosts the workflow used to carry out the spatial
analysis, from data retrieval to producing the final dataset that is
hosted (here)[<https://doi.org/10.5281/zenodo.8306892>]. Below are
further details on the repository structure, how to use the code base,
and data sources.

Forward any questions reguarding this project and code base to Caitlin
Mothes ([ccmothes\@colostate.edu](mailto:ccmothes@colostate.edu))

<br/>

## Project Versions

This repository contains analyses from two phases of NASA-funded
research:

**Phase 1 (v2023-1)** - NASA ROSES-21 A.49 (Award No 80NSSC22K1465) -
Published: August 31, 2023 - DOI:
[10.5281/zenodo.8306856](https://doi.org/10.5281/zenodo.8306856) -
Status: Initial environmental justice analysis for U.S. state and
federal prisons - Archived code: [GitHub Release
v2023-1](https://github.com/GeospatialCentroid/NASA-prison-EJ/tree/v2023-1)

**Phase 2 (in progress)** - NASA ROSES-23 A.47 (Award No 80NSSC25K7033) -
Updated datasets and extended analyses - *Release and DOI forthcoming*

**Citation:** For the overall project, use the concept DOI:
[10.5281/zenodo.8306855](https://doi.org/10.5281/zenodo.8306855). For
specific versions, cite the version-specific DOI listed above.

<br/>

## File Organization

NASA-prison-EJ/
├── README.md
├── setup.R
├── LICENSE
├── .gitignore
├── NASA-prison-EJ.Rproj
├── process_indicators.R          
├── process_indicators.Rmd        
├── process_components.Rmd       
│
├── R/                            
├── python/                       
├── process_data/                 
├── analysis/                     
├── figures/                     
├── outputs/                     
├── jobs/                        
├── docs/                         
├── working_scripts/             
│
├── phase1/                       # ARCHIVED - Phase 1 complete
│   ├── R/
│   ├── python/
│   ├── process_data/
│   ├── analysis/
│   ├── figures/
│   ├── outputs/
│   ├── jobs/
│   ├── docs/
│   ├── process_indicators.R
│   ├── process_indicators.Rmd
│   ├── process_components.Rmd
│   └── README.md                 
│
└── data/                         # Local only (not in git)
    ├── phase1/
    │   ├── raw/
    │   └── processed/
    └── phase2/
        ├── raw/
        └── processed/


## Folder Descriptions

-   `docs/` Project-specific references and metadata.

-   `data/` This folder is stored locally (see Github_Collab_Guide.docx
    in `docs/` for methods on how to set up a local data folder that
    syncs to a cloud-hosted folder). All raw, unprocessed data lives in
    `raw/` and all datasets processed throughout the workflow (using
    code in `process_data/`) go to `processed/` . GEE-processed datasets
    also live in this `processed/` folder.

-   `process_data/` Scripts to process raw data (when needed). Outputs
    of these scripts go into `data/processed/`

-   `R/` R code for analysis, each formatted as an individual function
    for each indicator calculation (i.e., all indicators not requiring
    Earth Engine data sets).

-   `python/` Python code for Google Earth Engine analyses.

-   `jobs/` Job scripts to run background jobs for each component
    function (See 'process_components.Rmd' for executing these).

-   `outputs/` Where all outputs from each indicator function, component
    function and final data frame calculation are stored. Each file is
    set up to include the date of creation when saved to this folder.

-   `analysis/` R code for all post-hoc analysis of final data set.

-   `figures/` Figures produced from analysis scripts.

-   `working_scripts/` Old or in progress scripts outside of current
    workflow. External collaborators can disregard this folder.

## File Descriptions

There are a few important files in the root directory:

-   `setup.R` Executing this script will install and load all necessary
    packages, source all functions, and create a local 'outputs/'
    directory if it does not already exist.

-   `process_indicators.R / .Rmd` This file (saved as both an R script
    and R Markdown for user preference) works through executing
    indicator calculations individually.

-   `process_components.Rmd` This file walks the user through
    calculating indicators as grouped component scores. It also has an
    option for executing the component functions as background jobs (as
    some may take days to full execute due to large datasets and scale
    of processing).

## General workflow

The main files described above give users the option to run individual
indicators or process the entire component scores all at once, and each
work through creating a final data frame as the last step.

This workflow is designed to work on ANY spatial polygon `sf` object.
While this project specifically studies state and federal US prisons,
the code can be applied to any other boundary shapefile, greatly
expanding the utility of this code base and allowing for future
researchers to analyze other areas of interest (e.g., extend to jails
and juvenile detention centers, or calculate measures for other
communities/neighborhoods to assess comparisons with risks faces by
prisoners).

While some functions and scripts retrieve the datasets directly from the
code base, some need to be downloaded manually. The table below provides
links to download each of the datasets used in this project, and direct
users to the processing script used to clean the raw data download (if
necessary).

## Data sources and indicator methods

A full metadata table with data sources, links, indicator methods and
data metadata can be found in
[docs/indicator_metadata.md](https://github.com/GeospatialCentroid/NASA-prison-EJ/blob/main/docs/indicator_metadata.md)
