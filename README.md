# flam-methods-comparison

## A GitHub Repository for: 

## Tissue-level flammability testing: A review of existing methods and a comparison of a novel hot plate design to an epiradiator design

## Joe Celebrezze, Indra Boving, and Max Moritz

--------------------------------

## Introductory Statement
This repository is meant for the storage and sharing of data, scripts, figures, and mixed effects model result tables related to the paper titled *Tissue-level flammability testing: A review of existing methods and a comparison of a novel hot plate design to an epiradiator design* by Joe Celebrezze, Indra Boving, and Max Moritz which introduces a hot-plate-based flammability chamber design, comparing it to existing methods using a literature review and an in-depth comparison to an epiradiator method in which we simultaneously burned samples using both the novel hot-plate-based method and an epiradiator method.

--------------------------------

## Table of Contents

[Breakdown of Folders](https://github.com/celebrezze/flam-methods-comparison#breakdown-of-folders)

[- Raw Data](https://github.com/celebrezze/flam-methods-comparison#raw-data)

[- Processed Data](https://github.com/celebrezze/flam-methods-comparison#processed-data)

[- Scripts](https://github.com/celebrezze/flam-methods-comparison#scripts)

[- Figures](https://github.com/celebrezze/flam-methods-comparison#figures)

[- Mixed Effects Model Selection Tables](https://github.com/celebrezze/flam-methods-comparison#mixed-effects-model-selection-tables)

[Metadata](https://github.com/celebrezze/flam-methods-comparison#metadata)

[Contact Information](https://github.com/celebrezze/flam-methods-comparison#contact-information)

--------------------------------

## Breakdown of Folders

### Raw Data:
The **raw-data** folder consists of five datasets in .csv format. For more comprehensive information regarding each of the datasets, see the metadata. Below are descriptions for those datasets:
  
  *lit.review.csv*: this exhibits the methods used in the 134 studies identified in the literature review along with identifiers for the studies (authors and year), a description of the size of sample (if included) either in terms of weight (g), length (cm), area (cm2), or volume (cm3), and a description of the heating temperature or irradiance of the method used.
  
  *lit.review.locations.csv*: this accompanies the *lit.review.csv*, but it focuses on the locations (latitude and longitude and notes on the location) that samples were gathered from for each study (if included). The accuracy of the locations vary, as some studies provided specific coordinates while others provided broad regions or stated that samples were in greenhouses near their laboratory and the coordinates for the laboratory were used. This was used to make *Fig2a.lit.review.locations.all.ignitions*
  
  *lit.review.drydown.csv*: this also accompanies the *lit.review.csv*, but it focuses on the drydown method implemented in the studies. This was used to inform how common the laboratory benchtop drydown is as a drydown method in tissue flammability studies.
  
  *local_flam_data_all.csv*: this includes the flammability testing results for chapparal shrubs, *Adenostoma fasciculatum* and *Ceanothus megacarpus*, reporting a variety of metrics including multiple ways to identify samples, bins of LFM, the method used (either epiradiator (EPI) or hot plate (HP)), live fuel moisture and water potential data along the benchtop drydown, a variety of flammability metrics (flame height (fh), time to first glow (ttfg), glow to ignition (gti), time to ignition (tti), flame duration (fd), glow duration (gd), post-flame glow (pfg), maximum temperature (temp.max), and temperature at ignition (ignition.temp)), sample weight, the proportion of new growth, and a variety of other variables. For more information and a comprehensive breakdown of each variable, see the metadata.
  
  *pv_summary_df_timing.csv*: this includes data from pressure-volume (PV) curves conducted on the species we were interested from the Sierra Nevadas and chapparal sites. PV curves were conducted using the protocol identified in Tyree and Hammel 1972. We did not use the PV curve data in the main analyses or supplemental analyses; however, we did end up using them in the exploratory analyses, hence why this dataset remains in the repository. For a more comprehensive description of the columns or the protocol followed to gather the data, see the metadata.
  
  *SEKI_flammability.csv*: this includes similar variables reported in *local_flam_data_all.csv* but for the flammability testing results for the species tested in the Sierra Nevadas, *Arctostaphylos patula*, *Ceanothus cordulatus*, *Abies concolor*, *Pinus jeffreyii*, *Calocedrus decurrens*, and *Quercus kelloggii*. Compared to the local_flam_data_all.csv, this dataset has far fewer variables: ID, species, method, water potential, live fuel moisture, sample weight, proportion new, and flammability metrics to name the most important ones. This .csv was significantly wrangled in a different script located in the extra-analyses folder (*data_wrangling_SEKI.Rmd*) and the dataset in the processed-data folder was used in the analyses (*seki_flam_data_all.csv*). This wrangled dataset was far more similar to the *local_flam_data_all.csv*.
  
### Processed Data:
The **processed-data** folder consists of datasets manipulated/wrangled at some stage from the *raw-data*. This folder primarily includes datasets of different iterations that include data in which both methods were used simultaneously. See the metadata for more information. Otherwise, see *1.data_wrangling_methods.Rmd* (for the combined datasets as described in the metadata or *data_wrangling_SEKI.Rmd* (in *extra-analyses*; for *seki_flam_data_all.csv*) for details on data wrangling.

### Scripts:
The **scripts** folder includes scripts for all of the code we used to wrangle data, complete analyses, and design tables and figures for the main body of the paper, the supplementary index, and for exploratory analyses (which are primarily located in the *extra-analyses* folder inside of the **scripts** folder). The scripts are numbered in a logical order which follows the order presented in the paper. Further details regarding each of the 6 main scripts follow:

  *1.data_wrangling_methods.Rmd*: this takes the datasets from the *raw-data* folder and cleans them up so that they could be combined into one main dataset for further analyses. It removes species with less than 6 ignitions for either of the methods (leaving *Adenostoma fasciculatum*, *Ceanothus megacarpus*, *Arctostaphylos patula*, and *Ceanothus cordulatus*), removes rows with NA values in certain variables, and moves any instances of manual ignitions (i.e., after 7 minutes elapsed, we manually ignited the samples by lifting them into the propane-fueled pilot flame) into a specific dataset, otherwise removing them from the bulk of datasets.
  
  *2.literature_review.Rmd*: this involves all analyses and figures relating to the literature review. This includes the map labelled Figure 2a in the paper. IMPORTANT NOTE: For this map, we used global ignitions data readily available from the Global Fire Atlas through ORNL DAAC, Distributed Active Archive Center for Biogeochemical Dynamics (https://daac.ornl.gov/cgi-bin/dsviewer.pl?ds_id=1642). This data was **not** stored in our GitHub due to the large file size. Due to this, data must be locally requested from the website and then proper urls must be manually inputted into the code by whoever may be running the script for it to run properly.
  
  *3.1.water_content_vs_flam.Rmd*: this involves code necessary for figures that compare water content (or dry weight) to flammability metrics and accompanying mixed effects model selections and statistical tests. It includes a wide variety of iterations to look at the data including iterations not included in the paper or supplementary materials.
  
  *3.2.mixed_effects_model_selections.Rmd*: this involves the primary mixed effects model selection discussed in the paper and accompanying mixed effects model summary tables.
  
  *4.interspecific_differences.Rmd*: this focuses on the section of the supplementary index concerned with interspecific differences and involves many iterations of similar analyses (a lot of which were not utilized); otherwise, it contains statistical tests, visualizations and summary tables that relate to interspecific differences.
  
  *5.PCA.Rmd*: this involves all code necessary for the principal component analyses included in the paper.
  
  *extra-analyses*: as previously alluded to, any exploratory analyses or scripts which were improved upon or elaborated on by the main 6 scripts described above were placed in the *extra-analyses* folder. This folder includes analyses not mentioned above such as variance decomposition, classification and regression trees, segmented regressions, using the flammability index developed in Essaghi et. al. 2017, and an investigation into manual ignitions (mostly for *Ceanothus cordulataus*). Importantly, it also contains the *data_wrangling_SEKI.Rmd* file dedicated to wrangling the *SEKI.flammability.csv* into a more usable format in *seki_flam_data_all.csv*.
  
### Figures:
The **figures** folder includes all figures included in the main text of the paper and the supplementary index, as well as figures we did not end up presenting (mostly placed in the *extra-figures* folder). All main and supplementary figures were labelled appropriately with FigX. or FigSX. preceding the description of the figure. Note that *Fig1.methods.images.png* is not made in any script, but instead consists of two pictures taken by Indra Boving and Joe Celebrezze.

### Mixed Effects Model Selection Tables:
These are placed in the **mem-model-selection** folder and informed our conclusions regarding this analysis.

## Metadata:
This is located in *METADATA.Rmd* and *METADATA.html* (made from knitting *METADATA.Rmd*).

## Contact Information

Joe Celebrezze*: celebrezze@ucsb.edu

Indra Boving: bovingi@ucsb.edu

**correspondence*