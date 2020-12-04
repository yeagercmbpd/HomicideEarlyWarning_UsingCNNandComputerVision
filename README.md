<p align="center">
   <img src=https://github.com/yeagercmbpd/Identifying_Victim_Clusters_In_Baltimore_CIty_Police_Data/blob/main/patch.png>
<div align="center">
   <figcaption></figcaption>
</div>
</p>

A Homicide and Shooting Early Warning System 
---
using Baltimore Police Crime Data, Computer Vision, and Convolutional Neural Networks

---
### Overview and Project Goals
Historically, the majority of the violent crime which plagues Baltimore City has occured as a byprodict of the illicit drug trade and conflicts stemming from the distribtion of those drugs. A majority of these incidents of homicide and shooting are tied to outside, open air "drug shops" throughout the city. The goal of this model will be to find hidden  patterns in the flow of reported crime throughout the city, in an attempt to be able to provide a warning of a potential impending violent event. Using images which consist of 2 hour snapshots of crime within the city, plotted to a map, the model will attempt to classify what it sees upon that map as a distribution that is likely to include a homicide/shooting or one that is not. A model like this, if deployed to a real time environment, could sound a warning within the police department when a homicide is likely. Officers could then be rapidly deployed to known violence hotspots, in an attempt to prevent potential homicides. 

---
### Repository Navigation
<pre>
Technical Notebook: <a href=https://github.com/yeagercmbpd/Identifying_Victim_Clusters_In_Baltimore_CIty_Police_Data/blob/main/Detecting%20Victim%20Groupings%20in%20Baltimore%20Crime%20Data.ipynb>Technical Notebook/Report</a>

</pre>
---

## The Data
The [primary dataset](https://data.baltimorecity.gov/api/views/wsfq-mvij/rows.csv?accessType=DOWNLOAD) which will be used in this analysis is the victim based part 1 crime table, produced by the Baltimore City Police Department. It reports crimes based upon each victim, rather than occurance, and thus each row can be thought of as a victim. The dataset at the time I accessed it consisted of almost 280,000 records and 22 columns. The data from 01/01/2014 through 10/31/2020 was used to produce over 29,000 individual maps. Each map represents a 2 hour window in time. All crimes which took place within that window are plotted into the map as a color coded point. Additionally, neighborhood outlines within the city are included. Any neighborhood which experienced a crime of any type during this time is highlighted in red, all others are in black. Please find an example map below:

<p align="center">
   <img src=https://github.com/yeagercmbpd/HomicideEarlyWarning_UsingCNNandComputerVision/blob/main/Images/201401_03407.png>
   <img src=https://github.com/yeagercmbpd/HomicideEarlyWarning_UsingCNNandComputerVision/blob/main/Images/201401_03407.png>
<div align="center">
   <figcaption></figcaption>
</div>
</p>

The neighborhood [shapefile](https://data.baltimorecity.gov/api/views/2ktz-dadz/rows.csv?accessType=DOWNLOAD) used in the plotting of the maps is maintained by Baltimore City.


---

## Summary

**Part 1: Crime data only**

  Clusters found with moderate density and variation. Looking strictly at the data available within this set did not yield much in the way of insight.
   
**Part 2: Incorporating demographic data into the victim data**

   Much more distinct clusters identified. interesting patterns which fall in line with outside analysis identified. Basic victim profiles could be generated.
   
## Lessons Learned / Looking Forward
Dimensionality reduction became neessary to complete the analysis and model upon adding all of the additional features within the census based data set.
Having access to individual victim information rather than generalizing it basd on census data would lead to an incredibly more specific result and allow for a very powerful clustering model. 
  
---
## PackagesandCredits
<pre>
By : <a href=https://github.com/yeagercmbpd>Christopher Yeager</a>
</pre>

<pre>
Languages    : Python
Tools/IDE    : Jupyter
Libraries    : pandas, numpy, matplotlib, sklearn, seaborn,geopandas, tensorflow, keras
</pre>
