[![CircleCI](https://circleci.com/gh/Dewalade1/cloud--deployml-microservice-with-kubernetes/tree/main.svg?style=svg)](https://circleci.com/gh/Dewalade1/cloud--deployml-microservice-with-kubernetes/tree/main)

## Project Overview

In this project, you will apply the skills you have acquired in this course to operationalize a Machine Learning Microservice API. 

You are given a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project tests your ability to operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.


## Setup the Environment

* Create a virtualenv with Python 3.7 and activate it. Refer to this link for help on specifying the Python version in the virtualenv. 
```bash
python3 -m pip install --user virtualenv
# You should have Python 3.7 available in your host. 
# Check the Python path using `which python3`
# Use a command similar to this one:
python3 -m virtualenv --python=<path-to-Python3.7> .devops
source .devops/bin/activate
```
* Run `make install` to install the necessary dependencies

### Running `app.py`

1. Standalone:  

```python app.py```

2. Run in Docker:  

```./run_docker.sh```

3. Run in Kubernetes:  

```./run_kubernetes.sh```

### Kubernetes Steps

* Setup and Configure Docker locally

```docker build --tag=latest .```

* Setup and Configure Kubernetes locally

```minikube start```

* Create Flask app in Container

```docker run -it -p 8000:80 latest```

* Run via kubectl

```kubectl run housing-price-prediction-app --image=$dockerpath --port=80```

* Check pod status 

```kubectl get pod```

* Stop Kubernetes Clusters

```minikube close```

* Delete Kubernetes Clusters 

```minikube delete```
