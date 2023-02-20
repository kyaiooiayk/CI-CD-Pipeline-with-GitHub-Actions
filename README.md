# From jupyter notebook to ML production pipeline
***

- Following a nice 3-series article published on Medium:
    - [Back to the Machine Learning fundamentals: How to write Pipeline for Model deployment (Part 1/3)](https://ivannardini.medium.com/back-to-the-machine-learning-fundamentals-how-to-write-code-for-model-deployment-part-1-3-4b05deda1cd1)
    - [Back to the Machine Learning fundamentals: How to write Pipeline for Model deployment (Part 2/3)]()
    - [Back to the Machine Learning fundamentals: How to write Pipeline for Model deployment (Part 3/3)]()
 ***
 
 ## ML Pipeline
 - A typical Machine learning pipeline for production is mainly composed of four (give or take) steps:
    - Data Gathering
    - Features engineering
    - Features selection
    - Model Building
***
 
 ## Step 0
 - Download the two notebooks published on Kaggle mentioned in the article. These will be considered the baseline and the code published under the ML productin pipeline is based on these two notebooks. I have downloaded and saved them in this repository ()
     - [Notebook #1 by OmkarReddy Kaggle user]()
     - [Notebook #2 by Bunty Shah Kaggle user]()
- When it comes to replicating the result, this is not possible because the two authors have not fix the seed the `train_test_split` sklearn function making their model training essentially random.
***

## Step #1 - Procedural pipeline
- Procedural pipeline is here used to differentiate it from OOP pipeline.
- The first rule while trying to create a model deployment pipeline is to always set the random seed in oder to make sure your cod e is reproducible.
- The re-organised codes can be found [here](https://github.com/kyaiooiayk/ETL-and-ML-Pipelines-Notes/tree/main/tutorials/from_jupyter_notebook_to_ML_production_pipeline/ml_pipeline_procedural_code/notebooks/GitHub_MD_rendering) where there is a notebooks for each steps, hence the name procedural):
    - 1.0-insurance-Data_Analysis.ipynb
    - 2.0-insurance-Feature_Engineering.ipynb
    - 3.0-insurance-Feature_Selection.ipynb
    - 4.0-insurance-Model-Building.ipynb
    - 5.0-insurance-Model-Deployment.ipynb
*** 

## Step #3 - write the .py files
- Under folder `src` create the following three python files:
    - `preprocess.py` containing all the steps necessary to pre-process the data.
    - `train.py` containing all the steps to train the model.
    - `score.py` containig all the steps to evaluate the model.
***

## Step #4 - create a test script
- Under folder `test` copy the following files:
    - `preprocess.py`
    - `train.py`
    - `score.py`
- Create a Bash Shell Script File called `run.sh` that can be run by the GitHub action
***


## Step #5 - push the code
- Push the code to your Github repository
- Be aware that bulding the Docker image on GitHub action would take over 30 minutes.
***
