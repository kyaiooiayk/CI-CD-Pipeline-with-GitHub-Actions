# From jupyter notebooks to ML production pipelines
The scope of this repository is to show how one can go from creating a series of notebookes to creating several production pipelines with the help of GitHub Actions.
***

## GitHub Actions
- **CI/CD** is a coding philosophy and set of practices with which you can continuously build, test, and deploy iterative code changes.
- **CI** is about how the project should be built and tested in various runtimes, automatically and continuously. 
- **CD** is needed so that every new bit of code that passes automated testing can be released into production with no extra effort.
- If you are using GitHub to version control your code, you can use GitHub Actions right off the bat without having the need to setup another tool.
- GitHub Actions are just a set instructions declared using `yaml` files.
- These files needs to be in a specific folder: `.github/workflows` and this has to be in the root directory (where `.git` hidden folder is present).
- There are 5 main concepts in GitHub Actions:
    - **Event** which is an event that triggers for workflow.
    - **Job** defines the steps to run when a workflow is triggered. A workflow can contain multiple jobs.
    - **Runner** defines where to run the code. By default, github will run the code in it's own servers.
    - **Step** contains actions to run. Each job can contains multiple steps to run.
    - **Action** contains actual commands to run like installing dependencies, testing code, etc.
 
![image](https://user-images.githubusercontent.com/89139139/220193508-774b645e-664d-49ee-89a8-8d83442ac879.png)
***

## Artifacts and dependency caching
- Artifacts and caching are similar because they provide the ability to store files on GitHub, but each feature offers different use cases and cannot be used interchangeably.
    - **Use caching** when you want to reuse files that don't change often between jobs or workflow runs, such as build dependencies from a package management system.
    - **Use artifacts** when you want to save files produced by a job to view after a workflow run has ended, such as built binaries or build logs.
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
- The first rule while trying to create a model deployment pipeline is to always set the random seed in oder to make sure your code is reproducible.
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

## References
- [Back to the Machine Learning fundamentals: How to write Pipeline for Model deployment (Part 1/3)](https://ivannardini.medium.com/back-to-the-machine-learning-fundamentals-how-to-write-code-for-model-deployment-part-1-3-4b05deda1cd1)
- [Back to the Machine Learning fundamentals: How to write Pipeline for Model deployment (Part 2/3)](https://ivannardini.medium.com/back-to-the-machine-learning-fundamentals-how-to-write-code-for-model-deployment-part-2-3-9632d5a43f98)
- [Back to the Machine Learning fundamentals: How to write Pipeline for Model deployment (Part 3/3)](https://ivannardini.medium.com/back-to-the-machine-learning-fundamentals-how-to-write-code-for-model-deployment-part-3-3-fb85102bebb2)
- [MLOps Basics [Week 6]: CI/CD - GitHub Actions](https://www.ravirajag.dev/blog/mlops-github-actions)
- [Build Reliable Machine Learning Pipelines with Continuous Integration](https://towardsdatascience.com/build-reliable-machine-learning-pipelines-with-continuous-integration-ea822eb09bf6)
- [Storing workflow data as artifacts](https://docs.github.com/en/actions/using-workflows/storing-workflow-data-as-artifacts)
 ***
