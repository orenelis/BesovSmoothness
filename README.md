# BesovSmoothness
measuring smoothness of datasets - tool for the paper "Function space analysis of deep learning
representation layers" to be appeared. for terminology, see http://www.jmlr.org/papers/volume17/15-203/15-203.pdf
this is a very simple tool to measure Besov smoothness
requirements:
this app is working on any native windows platform (was tested on AWS Microsoft Windows Server 2016 Base - with no installations or dependencies)
input:
trainingData.csv - a csv file where each row is a sample with n features
trainingLabel.csv - a csv file that match a label for each sample in the trainingData.csv file note that a label should be denoted as a point in a simplex (see examples in this repository for formats)
config.txt - a config file with the relevant definitions for running the app
running the app:
*make sure that config.txt is at the same level as the exe
*set config and run!
config parameters (follow the attached example):
dbPath				<your input path - where the two csv files are saved>
resultsPath			<your output path - where you want to save results>
boundLevelDepth		 - you can restrict the depth of the trees of the Wavelets forest to speed up performance (on the expense of taking deeper nodes - if you have a small dataset or enough time and want full trees - restrict to a large depth such as 1024)
nTrees				- number of trees in Wavelets forest
nFeaturesStr		- hyper parameter to select the number of features that are randomized in each node partition - if you want search along all nodes type "all" (without the "") otherwise specify the number of nodes you want
bagginPercent		- bagging parameter for diversity 
nCv					- number of cross validation you want to perform (1 is actually without cross validation, 5 is fivefold ...)
Mterm				- number of terms to take in the M term
output:
after the app is done you will have a folder with results saved at "resultsPath" you have defined.
you will find a folder for each cross validation fold (zero indexed) and the result file inside "alpha.txt" containing the alpha smoothness. in addition, you will find the measured error decay in errorByWaveletsTraining.txt and the number of wavelets used for the error decay in NwaveletsInWaveletByWaveletTraining.txt - with this two files you could fit the decay (alpha) in alternative methods if you wish.

