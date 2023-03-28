FROM python:3.7-slim-buster

RUN pip install cryptography mlflow boto3 pymysql minio sklearn scikit-learn

WORKDIR /training
COPY ./tests.py .
COPY ./kc_house_data.csv .
COPY ./train.py .