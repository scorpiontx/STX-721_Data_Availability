# STX-721_Data_Availability

Author: Dr. Jack Henderson

Date: 01/02/25

This README file is for the data availability of the AACR Journal Entry Titled "STX-721, a covalent EGFR/HER2 exon 20 inhibitor, takes advantage of exon 20 mutant dynamic protein states and achieves unique mutant-selectivity across human cancer models."

[Link to Publication Pending]

## Raw Data (Metadynamics Simulation Trajectories)

The first step is to download the data directory from our AWS S3 Bucket following these CLI steps:

TAR_FILE_URL="https://stx721-data-availability.s3.us-east-1.amazonaws.com/data.tar.gz"

curl -o data.tar.gz ${TAR_FILE_URL}

tar -xvf data.tar.gz -C ./data


In the data directory, trajectory files are in dcd format and have been converted from desmond trajectories.

- Trajectory Directories:
    - WT_*
    - ASV_*
    - NPG_*
    - SVD_*

## Scripts for Analysis and Figure Generation

Here, you will find all the scripts used to run the analysis and generate the plots for the paper.

-- Requirements --

- Python Libraries:
    - mdanalysis                2.6.1
    - matplotlib                3.9.2
    - numpy                     1.26.4
    - seaborn                   0.13.2
    - tqdm                      4.66.6
    - scipy                     1.14.1

- Other Software:
    - Fpocket is required for the pocket volume calculation in step 2 below. https://github.com/Discngine/fpocket

- To re-analyze and re-generate the figure in the paper, please run the following scripts in the specified order.

1. C-Helix_Transition_Calculation.ipynb
   - This script calculates the RMSD with respect to C-Helix 'In' and 'Out' state crystal structures and some additional C-Helix angle information.
   - Once completed, this script will create Supplementary Fig. S1C and Fig. 1C found in the main text.
   - Data from this script will be stored in the C-Helix_Transition_Data directory as simple text files.
   - Plots from this script will be stored in the plots directory.
   - The REF_structures directory includes EGFR In- and Out-state structures used for alignments. Resid numbering in these structures has been modified to account for changes in resid numbering from insertion mutations.

2. Pocket_Volume_Calculation
   - Here, there are two scripts: Step1_pocket_vol_calc.ipynb and Step2_Plotting.ipynb
   - Step1_pocket_vol_calc.ipynb is used to remake all the data from the trajectories in the data directory.
   - Step2_Plotting.ipynb helps with some initial plotting of the fpocket analysis.
   - To save on file size, only the results of the fpocket calculation have been included and not the remade trajectories required for the calculation.

3. Plot_Pocket_Volume_and_C-Helix_RMSD_Correlations.ipynb
   - finally, this script will generate correlation plots between the RMSD and pocket volume calculation results.
   - This script produces Supplementary Fig S1D and Fig 1E from the main text.
