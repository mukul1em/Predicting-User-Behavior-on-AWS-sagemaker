# Predicting User Behavior with Tree-Based Methods
## Training on AWS EMR and SAGEMAKER 

Using AWS Elastic MapReduce (EMR) with Apache Spark and the SageMaker XGBoost service to engineer models in the context of big data.

### __AWS EMR__ :
EMR is an AWS service that allows us to run and scale Apache Spark, Hadoop, HBase, Presto, Hive, and other big data frameworks.Let's think of EMR as a service that allows us to launch several interconnected machines with running software, such as Apache Spark, that coordinates distributed processing. EMR clusters have a master and several slaves.

EMR can also host notebook servers that connect to the cluster

# Training on EMR using Pyspark MLib

## Data Uploading using *awscli*:

Data Source - The dataset we will use throughout the rest of the chapter is obtained from Shioji, Enno, 2017, Adform click prediction dataset, https://doi.org/10.7910/DVN/TADBY7, Harvard Dataverse, V2.

- install awscli

```
pip install awscli
```
- Create IAM user and s3 full acess

- upload the data using AWS CLI after downloading locally(4.9gb)
```
aws s3 cp /adform.click.2017.01.json s3://bucket-mukul/adform.click.2017.01.json
```

# Training 
decisionTree classifier is used to train on the dataset using Pyspark MLib

__Training Pipeline__ - 

1 - One Hot Encoding

2 -  ChiQSelector - selecting top 100 features using chi2 

3 - Decision Tree Classifier/Randomforest Classifier

__Evaluating__

ROC/AUC is used to evaluate the classifier using Spark's *BinaryClassificationEvaluator*  to calculate the scores by providing the actual and predicted labels on our test dataset.

__score : 0.62__  
We can see that now we get a ROC greater than 0.5, which means that our model has improved and is now better than random guessing

# Training in Sagemaker using XGBOOST Classifier

1 - Instantiate the SageMaker session, container, and variables with the location of our datasets:

2 - Create a classifier by instantiating a SageMaker estimator and providing the basic parameters, such as the number and type of machines to use (details can be found in the AWS documentation at https://sagemaker.readthedocs.io/en/stable/estimators.html ):

3 - Set the hyperparameters of our trainer.



