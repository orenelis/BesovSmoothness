# BesovSmoothness
measuring smoothness of datasets - tool for the paper "Function space analysis of deep learning
representation layers" to be appeared. for terminology, see http://www.jmlr.org/papers/volume17/15-203/15-203.pdf
this is a very simple tool for measuring Besov smoothness <br />
requirements:<br />
this app is working on native windows platform (was tested on AWS Microsoft Windows Server 2016 Base - with no installations or dependencies, and also on a laptop with windows10 installed)<br />
input:<br />
trainingData.csv - a csv file where each row is a sample with n features<br />
trainingLabel.csv - a csv file that match a label for each sample in the trainingData.csv file note that a label should be denoted as a point in a simplex (see examples in this repository for formats)<br />
config.txt - a config file with the relevant definitions for running the app<br />
running the app:<br />
*make sure that config.txt is at the same level as the exe<br />
*set config and run!<br />
config parameters (follow the attached example):<br />
dbPath				<your input path - where the two csv files are saved><br />
resultsPath			<your output path - where you want to save results><br />
boundLevelDepth		 - you can restrict the depth of the trees of the Wavelets forest to speed up performance (on the expense of taking deeper nodes - if you have a small dataset or enough time and want full trees - restrict to a large depth such as 1024)<br />
nTrees				- number of trees in Wavelets forest<br />
nFeaturesStr		- hyper parameter to select the number of features that are randomized in each node partition - if you want search along all nodes type "all" (without the "") otherwise specify the number of nodes you want<br />
bagginPercent		- bagging parameter for diversity <br />
nCv					- number of cross validation you want to perform (1 is actually without cross validation, 5 is fivefold ...)<br />
Mterm				- number of terms to take in the M term<br />
output:<br />
after the app is done you will have a folder with results saved at "resultsPath" you have defined.
you will find a folder for each cross validation fold (zero indexed) and the result file inside "alpha.txt" containing the alpha smoothness. <br />in addition, you will find the measured error decay in errorByWaveletsTraining.txt and the number of wavelets used for the error decay in NwaveletsInWaveletByWaveletTraining.txt - with this two files you could fit the decay (alpha) in alternative methods if you wish.<br />

