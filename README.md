# Simple MLOps Pipeline

This directory contains files to setup local MLOps services. See [here](https://towardsdatascience.com/a-simple-mlops-pipeline-on-your-local-machine-db9326addf31) to follow along with instructions from the blog post.

cd experiment-tracking
docker-compose --env-file ./.env up -d

##

shivam@IN-79GZ9K3:~/mlops-pipeline$ docker exec -it mlflow_server bash

root@a3893c97aae1:/training# python train.py 

##

shivam@IN-79GZ9K3:~/mlops-pipeline$ pwd
/home/shivam/mlops-pipeline

# download from minio/mlflow ui, if there is a folder instead of a file for model.pkl
cp experiment-tracking/buckets/mlflow/1/dc9930e586654cdbbbe09f2ab06c810c/artifacts/rf-regressor/model.pkl ml-app
 
#
shivam@IN-79GZ9K3:~/mlops-pipeline/ml-app$ pwd
/home/shivam/mlops-pipeline/ml-app

docker build -t seldon-app .
docker run -p 5001:5000 -it seldon-app # port 5001 in case of mlflow

##

shivam@IN-79GZ9K3:~/mlops-pipeline/ml-app$ pwd
/home/shivam/mlops-pipeline/ml-app

shivam@IN-79GZ9K3:~/mlops-pipeline/ml-app$ python3 tests.py 
b'{"data":{"names":[],"ndarray":[264184.8]},"meta":{"metrics":[{"key":"mycounter","type":"COUNTER","value":1},{"key":"mygauge","type":"GAUGE","value":100},{"key":"mytimer","type":"TIMER","value":20.2}]}}\n'
shivam@IN-79GZ9K3:~/mlops-pipeline/ml-app$ 



