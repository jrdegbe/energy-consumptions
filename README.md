# energy-consumptions


**Build a production-ready ML batch system**. 


Its primary focus is to engineer a scalable system using MLOps good practices. 

You will implement an ML system for forecasting hourly energy consumption levels across Denmark.

You will **learn how to build, train, serve, and monitor an ML system** using a batch architecture. 

We will show you how to integrate an experiment tracker, a model registry, a feature store, Docker, Airflow, GitHub Actions and more!

# Table of Contents
1. [Data](#data)
2. [Code Structure](#structure)
3. [Set Up Additional Tools](#tools)
4. [Usage](#usage)
5. [Installation & Usage for Development](#installation)


--------

# 🤔 1. What You Will Learn <a name=learn></a>
**At the end of this bootcamp, you will know how to:**
* design a batch-serving architecture
* use Hopsworks as a feature store
* design a feature engineering pipeline that reads data from an API
* build a training pipeline with hyper-parameter tunning
* use W&B as an ML Platform to track your experiments, models, and metadata
* implement a batch prediction pipeline
* use Poetry to build your own Python packages
* deploy your own private PyPi server
* orchestrate everything with Airflow
* use the predictions to code a web app using FastAPI and Streamlit
* use Docker to containerize your code
* use Great Expectations to ensure data validation and integrity
* monitor the performance of the predictions over time
* deploy everything to GCP
* build a CI/CD pipeline using GitHub Actions


# 📊 2. Data <a name=data></a>

We used an open API that provides hourly energy consumption values for all the energy consumer types within Denmark.

They provide an intuitive interface where you can easily query and visualize the data. You can access the data [here](https://www.energidataservice.dk/tso-electricity/ConsumptionDE35Hour).

The data has 4 main attributes:
* **Hour UTC**: the UTC datetime when the data point was observed. 
* **Price Area**: Denmark is divided into two price areas: DK1 and DK2 - divided by the Great Belt. DK1 is west of the Great Belt, and DK2 is east of the Great Belt.
* **Consumer Type**: The consumer type is the Industry Code DE35, owned and maintained by Danish Energy.
* **Total Consumption**: Total electricity consumption in kWh

**Note:** The observations have a lag of 15 days! But for our demo use case, that is not a problem, as we can simulate the same steps as it would be in real time.

### IMPORTANT OBSERVATION

The API will become obsolete during 2023. Its latest data points are from June 2023, and the API will become unavailable during 2023. We created a copy of the data from 2020-07-01 and 2023-06-30 to bypass this issue. Thus, there are 3 years of data to play with. More than enough for the purpose of this course. 

The file is stored in Google Drive accessible [at this link](https://drive.google.com/file/d/1y48YeDymLurOTUO-GeFOUXVNc9MCApG5/view?usp=drive_link).

Thus, instead of querying the API, we will mock the same behaviour by loading the data from the file. Therefore, you don't have to download your file yourself. The code will download it and load the data from the file instead of the API, simulating 100% the same behavior.

**---> All Rights Reserved to: www.energidataservice.dk**


# 🧬 3. Code Structure <a name=structure></a>

The code is split into two main components: the `pipeline` and the `web app`.

The **pipeline** consists of 3 modules:
- `feature-pipeline`
- `training-pipeline`
- `batch-prediction-pipeline`

The **web app** consists of other 3 modules:
- `app-api`
- `app-frontend`
- `app-monitoring`

**Also,** we have the following folders:
- `airflow` : Airflow files | Orchestration
- `.github` : GitHub Actions files | CI/CD
- `deploy` : Build & Deploy
<br/>
<br/>

To follow the structure in its natural flow, read the folders in the following order:
1. `feature-pipeline`
2. `training-pipeline`
3. `batch-prediction-pipeline`
4. `airflow`
5. `app-api`
6. `app-frontend` & `app-monitoring`
7. `.github`


