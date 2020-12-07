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
<a href=https://github.com/yeagercmbpd/HomicideEarlyWarning_UsingCNNandComputerVision/blob/main/Notebooks/TechnicalNotebook.ipynb>Technical Notebook/Report</a>
<a href=https://github.com/yeagercmbpd/HomicideEarlyWarning_UsingCNNandComputerVision/blob/main/Notebooks/Data%20Preparation%20and%20Creation.ipynb>Primary Data Cleaning and Image Generation</a>
<a href=https://github.com/yeagercmbpd/HomicideEarlyWarning_UsingCNNandComputerVision/blob/main/Notebooks/Model%201.ipynb>Model 1</a>
<a href=https://github.com/yeagercmbpd/HomicideEarlyWarning_UsingCNNandComputerVision/blob/main/Notebooks/Model2.ipynb>Model 2</a>
<a href=https://github.com/yeagercmbpd/HomicideEarlyWarning_UsingCNNandComputerVision/blob/main/Notebooks/OneDay_Model_Depoyment_DataGen.ipynb>Model Implimentation Single Day Image Generator</a>


</pre>
---

## The Data
The [primary dataset](https://data.baltimorecity.gov/api/views/wsfq-mvij/rows.csv?accessType=DOWNLOAD) which will be used in this analysis is the victim based part 1 crime table, produced by the Baltimore City Police Department. It reports crimes based upon each victim, rather than occurance, and thus each row can be thought of as a victim. The dataset at the time I accessed it consisted of almost 280,000 records and 22 columns. The data from 01/01/2014 through 10/31/2020 was used to produce over 29,000 individual maps. Each map represents a 2 hour window in time. All crimes which took place within that window are plotted into the map as a color coded point. Additionally, neighborhood outlines within the city are included. Any neighborhood which experienced a crime of any type during this time is highlighted in red, all others are in black. Please find an examples of the map images generated below:

<p align="center">
   <img src=https://github.com/yeagercmbpd/HomicideEarlyWarning_UsingCNNandComputerVision/blob/main/Images/201401_03407.png>
   <img src=https://github.com/yeagercmbpd/HomicideEarlyWarning_UsingCNNandComputerVision/blob/main/Images/201401_0400355.png>
   <img src=https://github.com/yeagercmbpd/HomicideEarlyWarning_UsingCNNandComputerVision/blob/main/Images/201401_0530122.png>
   <img src=https://github.com/yeagercmbpd/HomicideEarlyWarning_UsingCNNandComputerVision/blob/main/Images/Legend.png>
<div align="center">
   <figcaption></figcaption>
</div>
</p>

The neighborhood [shapefile](https://data.baltimorecity.gov/api/views/2ktz-dadz/rows.csv?accessType=DOWNLOAD) used in the plotting of the maps is maintained by Baltimore City.


---

## Summary

**Model 1**
CNN-128mp-64x2mp-Dense-64-32

The validation accuracy measured over 20 epochs only gets to around 60%, not a great result. Also, taking a look at the tensorboard output we see a huge divergence between training loss and validation loss. We also see a decreasing validation accuracy as the epochs go on. I attributed this to the model potentially memorizing the inputs and overfitting the data.

At this point I decided to scrap this model and try again.
   
**Model 2**
CNN-32mp-64mp-218mp-Dense-512

The structure was tweaked and the idea of data augmentation to stretch the effectiveness of a small sample size was employed. Much better results with steady increase of validation and training accuracy, and steady and uniform decrease of losses. After 60 epochs a validation accuracy of .78 was acheived. A holdout test dataset yielded an average  prediciton accuracy of .784 after 50 runs of 15 image batches.
   
## Conclusion / Lessons Learned / Looking Forward
We have managed to acheive our goal and train a model which can look at snapshots of crime in space and time within Baltimore City and make a prediction as to whether or not a homicide/shooting event is likely to occur. Our concept has been proven as being possible.

Moving forward, improvements can certainly be made to this existing model. Fine tuning of model structure and hyperparameters could likely yield a slightly better performing model. This could include tweaking such things as the learning rate, implementing decay in different forms, finding the best activation, optimization, and loss functions, or adjusting the number and structure of the different layers. Training for additional ephocs would also almost certainly help, the model was still steadily improving where we left off. 

Adding additional data to the map images could also help in making more accurate predictions. Calls for service points, demographics, historic crime trends, and narcotics intelligence could all be added and suppliment the model.

experimenting with lagging the model may also allow for an increased amount of warning time before a potential incident. 

As building a neural network is, in the words of Andrew Ng, a "very emprical process" we know that more fine tuning can be done here. Due to time constraints and computing capabilities I was not able to explore all of the possibities available to producing the absolute best model within my working window. What we have come up with is a model which proves our idea is feasible and that can provide the promise of a tool which could help in stemming the violent crime epidemic in Baltimore City.
  
---
## PackagesandCredits
<pre>
By : <a href=https://github.com/yeagercmbpd>Christopher Yeager</a>
Inspiration and coding for data augmentation from: <a href=https://github.com/mguner/UMBC_DATA602/blob/master/lectures/week-12/Convolutional%20Neural%20Networks%20-%20Part%20-%20I.ipynb> Murat Gruner UMBC Data 602</a>
</pre>
[Coding and concept assistance](https://pythonprogramming.net/introduction-deep-learning-python-tensorflow-keras/)
<pre>
Languages    : Python
Tools/IDE    : Jupyter
Libraries    : pandas, numpy, matplotlib, sklearn, seaborn,geopandas, tensorflow, keras,statistics,cv2,shutil,pickle,random,time
</pre>
