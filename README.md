# Footprint Benchmark of models

Here is the code I used in my master's thesis to create a model benchmark of popular machine learning classification algorithms in terms of their energy consumption.

## Idea and Methology
While it is possible to estimate within Deep Learning via the model size and number of parameters (unoptimized!) to a certain extent straight-forward, which models consume more energy, classical methods of Machine Learning can be estimated more poorly. In the following benchmark, these models are therefore compared with each other. 

*The goal is to make a ranking of the selected calssification algorithms accorings to the energy consumption of a) the training and b) the interference.* 

The following paper served as inspiration, from which the steps for data preparation were taken.

> Manuel Fernández-Delgado, Eva Cernadas, Senén Barro, and Dinani Amorim. 2014. Do we need hundreds of classifiers to solve real world classification problems? J. Mach. Learn. Res. 15, 1 (January 2014), 3133–3181.

**Data preparation** 

The datasets come from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets.php?format=&task=cla&att=&area=bus&numAtt=&numIns=&type=&sort=instDown&view=table). Since the main focus is on the use of the model in a business context, datasets are considered that carry the label "business". First, classification models are to be tested, which is why the dataset should describe a classification problem. Furthermore, only datasets with more than 5000 entries are used.

Since there is no concern about the performance of the models, the data is prepared in the same way for all models and all data sets.  Also all available features of the datasets are used.

The following steps are performed as preparation:
- sort out ID columns
- fill missing values by most frequent ones
- convert text columns via one hot encoding
- standardize dataset (mean 0, standard deviation 1)
- separating features and target value

**Machine Learning models**

Since no hyperparameter optimization is to take place either, the default setting is used. For some models, however, the parameters have an effect on the runtime and thus also on the energy consumption. The number of models in an ensemble, the used kernel technique with the Support Vector Machines or the depth of a decision tree are mentioned here as examples. The following models are evaluated:
* Logistic Regressing
* Naive Bayes
* K-Nearest_Neighbours
* Decision Tree
* Random Forest
* Adaboost
* Bagging Ensemble
* Support Vector Machines
* Neuronal Network


**Carbon footprint**

The footprint is recorded using the [codecarbon](https://codecarbon.io/#howitwork) tool. Here, the process or machine-dependent footprint of the model is determined via the power consumption of the processor used. With a stored energy mix for the region, a extrapolation of the emissions can also be made.


**Required libraries**
- `sklearn`
- `numpy`
- `pandas`
- `codecarbon`
- `matplotlib`
- `seaborn`
