# This repository contains the work of Alex Hedquist for his Master's Thesis in Statistics. 

# PLEASE CONSULT THE READ_ME's in each sub-directory to find a more detailed description of the contents

# This repository contains the following sub-directories: 

# 1 -- Player_Data
This subfolder contains all individual player tables for any player who played a game between the 2000-2001 NBA season and the 2019-2020 NBA season. 
The files are named based on the player's reference found at basketball-reference.com/players. One must add the first letter of the players last name
separated by a '/' and the player reference given in the file name to view the player's page. 

Ex: Stephen Curry -- player ref = 'curryst01'
URL = https://www.basketball-reference.com/players/c/curryst01.html

# 2 -- Lineup_Data
This subfolder contains 20 CSV files, one per season from 2000-2001 to 2019-2020. Each table displays all lineup combinations that played during the given season.
The player references have been included in each row for each of the five players in the given lineup. 

# 3 -- Player_Cluster
This sub-directory contains all 20 seasons' player data with their normalized season statistics. All player statistics were normalized using the scale() R function. 
The first column is a concatenated identifier that contains the player reference, the three-letter team abbreviation, and the season. 
The second-to-last column indicates the player's cluster assignment from 1 to 9 for that season. 
The final column indicates the second year of the given season. This column was used for identification purposes in later analyses. 

# 4 -- Mega_Cluster
This sub-directory contains tables related to the mega-cluster analysis. 
The megaclusters.csv file displays the 'highs', 'lows', and 'in-betweens' for each season and cluster across the 21 variables.  

The files named Player_Apps_{1-9}.csv are tables (one for each mega-cluster) that give the player reference and the number of appearances in the given mega-cluster
over the course of their career. The tables are sorted by the highest number of appearances in descending order. 

The files named Player_App_Pct_{1-9}.csv are tables (one for each mega-cluster) that give the player reference, the total number of appearances in any
mega-cluster (n.x) , the total number of appearances in the given mega-cluster (n.y), and the percentage of their total cluster assignments that were in the given
mega-cluster. 
EX from Player_App_Pct_7.csv : 
X = geeal01 (Alonzo Gee) 
n.x = 10 (10 total appearances in any mega-cluster throughout the 20 seasons)
n.y = 8 (Alonzo Gee appeared 8 times in mega-cluster 7)
pct = 0.80 (Alonzo Gee spent 80% of his career in mega-cluster 7

The tables are sorted by the highest percentage of career in the given mega-cluster in descending order. 

# 5 -- R_Code
This sub-folder contains all R code used to obtain, load, process, and analyze the NBA player and lineup data.
NOTE: Some dependencies may exist...you may need to run certain scripts in order to be able to run others. Please consult the READ_ME for the R_Code subfolder for details. 

The Player_Scraping file contains all code needed to scrape all NBA player data used for this analysis. 

The Lineup_Scraping file contains all code that was used to scrape the NBA lineup data. Note that the base URL used to bring in these tables is no longer valid.

The Data_Prep_Player file contains all code used to load the player CSV files and perform any necessary processing and manipulating prior to clustering. 

The Cluster_Validation file contains all code related to data and cluster validation. This file includes code for generating Within Sum of Squares plots, the 
AGNES coefficient for determining the best hierarchical clustering method, the NbClust procedure and the histograms displaying the consensus selection across the 
26 indices, and the Adjusted Rand Inde (ARI) calculations by season along with the random baseline simulations. 

The Cluster_Algs_EDA file contains all code used to cluster the individual seasons of player data as well as the mega-clustering method and clustering assignments. 
The remaining code is provided to show how these mega-clusters were analyzed to see which players appeared in them the most frequently and at the highest percentage. 

The Clustering_Visualization file contains all code used to visualize the individual season clusterings as well as the mega-clustering assignments. Visualizations 
include dendograms, PCA (factoextra and base R), and tSNE. 

# 6 -- Python_Code
This file contains the Python code used to generate the PHATE plots for the individual NBA seasons. 
The user must note that the initial season tables read in for these plots consist of the player rows for a given season and their 21 scaled statistics for that season.
Row names indicating the player, team, and year have been excluded from these tables. The user may read in the new9_smpXXXX.csv files and simply exclude the first 
column to achieve the same outcome as the one presented in this code. 
