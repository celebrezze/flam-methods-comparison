# methods-comparison

*Introductory Statement*
This repository is meant for the storage and sharing of data, scripts, figures, and mixed effects model result tables related to the manuscript titled 'A comparison of a novel hot-plate-based flammability chamber design and an epiradiator-based design' by Joe Celebrezze, Indra Boving and Max Moritz which introduces a hot-plate-based flammability chamber design, comparing it to existing methods with an in-depth comparison to an epiradiator method.

--------------------------------

*Breakdown of Folders*

*Raw Data*
The raw-data folder consists of four dataframes in .csv format. For more comprehensive information regarding each of the dataframes, see the metadata. Below are descriptions for those dataframes:
  lit.review.csv: this exhibits the methods used in the 134 studies identified in the literature review along with identifiers for the studies (authors and year), a description of the size of sample (if included) either in terms of weight (g), length (cm), area (cm2), or volume (cm3)
  lit.review.locations.csv: this accompanies the lit.review, but focuses on the locations (latitude and longitude and notes on the location) that samples were gathered from for each study (if included). The accuracy of the locations vary, as some studies provided specific coordinates while others provided broad regions or stated that samples were in greenhouses near their laboratory and the coordinates for the laboratory were used.
  local_flam_data_all.csv: this includes the flammability testing results for chapparal shrubs, *Adenostoma fasciculatum* and *Ceanothus megacarpus*, reporting a variety of metrics including multiple ways to identify samples, bins of LFM, the method used (either epiradiator -- EPI or hot plate -- HP), live fuel moisture and water potential data along the benchtop drydown, a variety of flammability metrics (flame height (fh), time to first glow (ttfg), glow to ignition (gti), time to ignition (tti), flame duration (fd), glow duration (gd), post-flame glow (pfg), maximum temperature (temp.max), and temperature at ignition (ignition.temp)), sample weight, the proportion of new growth, and a variety of other variables. For more information and a comprehensive breakdown of each variable, see metadata.
  SEKI_flammability.csv: this includes similar variables reported in the local_flam_data_all.csv but for the flammability testing results for the species tested in the Sierra Nevadas, *Arctostaphylos patula*, *Ceanothus cordulatus*, *Abies concolor*, *Pinus jeffreyii*, *Calocedrus decurrens*, and *Quercus kelloggii*. Compared to the local_flam_data_all.csv, this dataset has far fewer variables: ID, species, method, water potential, live fuel moisture, sample weight, proportion new, and flammability metrics to name the most important ones.
  
*Processed Data*
The processed-data folder consists of dataframes manipulated at some stage from the raw-data. The dataframes in this folder primarily are composed of dataframes in different iterations that include data in which both methods were used simultaneously. See 1.data_wrangling_methods.Rmd for more information.

*Scripts*
The scripts folder includes scripts for all of the code we used to wrangle data, complete analyses, and design tables and figures for the main body of the manuscript, the supplementary index, and for exploratory analyses (which are primarily located in the extra-analyses folder inside of the scripts folder). The scripts are numbered in a logical order which follows the order presented in the manuscript. Further details regarding each of the 6 main scripts follow:
  1.data_wrangling_methods: this takes the dataframes from the raw-data folder and cleans them up so that they could be combined into one dataset for further analyses. It removes species with less than 6 ignitions for either of the methods (leaving *Adenostoma fasciculatum*, *Ceanothus megacarpus*, *Arctostaphylos patula*, and *Ceanothus cordulatus*), removes rows with NA values in certain variables, and moves any instances of manual ignitions (where after 7 minutes elapsed, we manually ignited the samples by lifting them into the propane-fueled pilot flame) into a specific dataset, otherwise removing them from the bulk of datasets.
  2.literature_review: this involves all analyses and figures relating to the literature review. This includes the map labelled Figure 2a in the manuscript. For this map, we used global ignitions data readily available from the Global Fire Atlas through ORNL DAAC, Distributed Active Archive Center for Biogeochemical Dynamics (https://daac.ornl.gov/cgi-bin/dsviewer.pl?ds_id=1642). This data was not stored in our GitHub due to the  large file size and the format. Data must be locally requested from the website and then proper urls must be provided into the code for it to run properly.
  3.1.water_content_vs_flam: this involves code necessary for figures that compare water content (or dry weight) to flammability metrics and accompanying mixed effects model selections and statistical tests. It includes a wide variety of iterations to look at the data including iterations not included in the manuscript or supplementary materials.
  3.2.mixed_effects_model_selections: this involves the primary mixed effects model selection discussed in the manuscript and accompanying mixed effects model summary tables
  4.interspecific_differences: this focuses on the section of the manuscript concerned with interspecific differences and involves many iterations of similar analyses (a lot of which were not utilized); otherwise, it contains statistical tests, visualizations and summaary tables
  5.PCA_NMDS: this involves all code necessary for the principal component analysis included in the manuscript as well as code for non-metric multidimensional scaling (NMDS) analyses which were not used in the final product
  extra-analyses: as previously alluded to, any exploratory analyses or scripts which were improved upon or elaborated on by the main 6 scripts described above were placed in the extra-analyses folder
  
*Figures*
The figures folder includes all figures included in the manuscript, supplementary index, as well as figures we did not end up presenting (mostly placed in the extra-figures folder).

*Mixed Effects Model Selection Tables*
These are placed in the mem-model-selection and informed our conclusions regarding this analysis