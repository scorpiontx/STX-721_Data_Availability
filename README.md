# STX-721_Data_Availability

Author: Dr. Jack Henderson
Date: 01/02/25

This README file is for the data availabiilty of the AACR Journal Entry Titled "STX-721, a covalent EGFR/HER2 exon 20 inhibitor,
takes advantage of exon 20 mutant dynamic protein states and achieves unique mutant-selectivity across human cancer models"

The trajectories from the metadynamics simulations are included in a data directory located on S3 while analysis scripts
are included in a code directory located on GitHub.

In the data directory, trajectory files are in dcd format and have been converted from desmond trajectories.

- Trajectory Directories:
    - WT_*
    - ASV_*
    - NPG_*
    - SVD_*

The code directory includes all scripts used to run the analysis and generate the plots for the paper.

-- Requirements --
Python Libraries:
    - mdanalysis                2.6.1
    - matplotlib                3.9.2
    - numpy                     1.26.4
    - seaborn                   0.13.2
    - tqdm                      4.66.6
    - scipy                     1.14.1

Other Software:
    - fpocket is required for the pocket volume calculation in step 2 below.
      https://github.com/Discngine/fpocket

- To re-analyze the and re-generate the figure in the paper please run the following script in the specified order.

    1.) C-Helix_Transition_Calculation.ipynb
        - This script calculates the RMSD with respect to C-Helix 'In' and 'Out' state crystal structures
          as well as some additional C-Helix angle information.
        - Once completed this script will create Extended Data Fig. 1A and Fig 1C found in the main text.
        - Data from this script will be stored in the C-Helix_Transition_Data directory as simple text files.
        - Plots from this script will be stored in the plots directory.

    2.) Pocket_Volume_Calculation
        - Here there are two scripts Step1_pocket_vol_calc.ipynb and Step2_Plotting.ipynb
        - Step1_pocket_vol_calc.ipynb is used to remake all the data from the trajectories in the data directory.
        - Step2_Plotting.ipynb helps with some initial plotting of the fpocket analysis.
        - To save on file size only the results of the fpocket calculation have been included and not the remade
          trajectories required for the calculation.

    3.) Plot_Pocket_Volume_and_C-Helix_RMSD_Correlations.ipynb
        - finally running this script will generate correlation plots between the RMSD calculation results and
          the pocket volume calculation results.
        - This script produces Extended Data Fig 1B and Fig 1E from the main text.