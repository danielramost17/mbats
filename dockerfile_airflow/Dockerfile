FROM puckel/docker-airflow

COPY requirements.txt /requirements.txt

ENV PYTHONPATH "${PYTHONPATH}:/usr/local/airflow/dags/q_pack"
# For airflow container defining the environment variables in the docker compose doesnt work except for the airflow variables
ENV MLFLOW_S3_ENDPOINT_URL "http://minio-image:9000"
ENV AWS_ACCESS_KEY_ID "minio-image"
ENV AWS_SECRET_ACCESS_KEY "minio-image-pass"
ENV MLFLOW_TRACKING_URI "http://mlflow-image:5500"

# Upgrade key dependencies
RUN pip install --no-cache-dir \
    'requests>=2.26.0' \
    'urllib3>=1.26.7,<1.27' \
    'typing-extensions>=3.7.4.3'

# Install your extras
RUN pip install --no-cache-dir \
    databricks-cli==0.18.0 \
    docker==6.1.3 \
    gitpython
