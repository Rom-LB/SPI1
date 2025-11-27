## Merge_Imaris_Tables_All_Spots
### This script quantifies the distribution of foci relative to a segmented surface (inside & outside).

1.	First this script generate a main table by extracting and concatenating colums fom different tables exported from Imaris analysis.
  Column “Red_Channel_Mean_Intensity” : the intensity of the red fluorescence measured at the foci location
  Column “Distance_Inside » : value of the distance map generated inside the objects (bacteria) underlying each foci
  Column “Distance_Outside » : value of the distance map generated outside the objects (bacteria) underlying each foci
2.	Estimation of the threshold for the mCherry negative population by Gaussian mixing approach
  In order to identify the threshold between the SPI-1ON and SPI-1 OFF populations, a Gaussian Mixture Model based on two components (Python, Scikit-learn library) was employed on a histogram presenting spot intensities in the mCherry channel. The Gaussian of the lowest population (comprising 90% of the spots) was used to determine the threshold with precision by calculating the mean of the Gaussian fit plus twice its standard deviation.
3.	Statistical test between the two populations 
  Following the splitting of the data into two populations, the spot distances from the DNA-dense regions were subjected to a statistical analysis using the Wilcoxon-Mann-Whitney test.
4.	Figure generation	
  For each population (mCherry positive and negative) a dot plot is generated. Each detected foci is plotted with its relative distance to the segmented surface (positive values are inside the objects while negative once are outside).
  A box plot is also generated to compare the distribution of the foci distribution in both the positive and negative populations
