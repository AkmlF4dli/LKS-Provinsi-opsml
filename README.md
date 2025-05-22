# This project using Python and deployment with AWS EKS

## Form Data
Input your data in here:<br/>
Name : Muhammad Akmal Fadli <br/>
YourCity : Jakarta Selatan

## Application Port
`Port application running on 2000`

## Environment Variable for Apps

- AWS_ACCESS_KEY_ID="ASIATDGNWCDP7DSHS5ZT"
- AWS_SECRET_ACCESS_KEY="a1FA5TugzlXaiBQ+5/EcWuO4QpzbI/1WQ+Mqzezh"
- AWS_SESSION_TOKEN="IQoJb3JpZ2luX2VjEBEaCXVzLXdlc3QtMiJGMEQCIF8sCjFa5RUvKolKs/dw8gpFpPrOss7mLT5gFi0n/RMQAiBPRaeSl7agRcQnPXTH3Pg3R991CcrdOG9fpLBs5wosaCq9AgjK//////////8BEAAaDDIxMzAzMjI0MzQyMyIM6RSbV5cF/C/4//EIKpECqL/PTiDNQz4dzccpwPh0THdxBjDl+d1QHACkE8LSavmM3K8BwA7tBkBPGyl8weqw4T+cLhvDgKID7NYe01M0WyuiFi2FIxM3weFhDb/LvTSPihBCKhho1xJmjkxSFAGR3SHq36T152BrWZzX38G1tTc5VgPfNm0y24svImhLuldIddlzJdgF/cogPyXDhDyLim/G81jlJzn57vDh99VBf/70y7HfoyfxyypzjXdL8lFONJkXVkRRsnFTidBfBk9LccCHILd4QMpCLg1lV6VD2TmbhWgVMvGF+I2Nvm7oT+88wcXbgM94zc3kQamLqhB0C+o4iv8IdTiw2PaGbhvUnasIZHMGllR5ZiJx5zHip5TmMMfyucEGOp4Bn07HS7xauONpFHmBwJ9sRQ94l2fmFj+MqQ+yuAf7hG9vky+vYvuXJp/BKenUntM7SPaEPsbgOYKxcPQGpnaBy4982hgnbhLUay7cG9+KK27KU1a9ZY3mzSoRHVYE6BLUXcXcXY52Byb/oS0BEwuIRo7VKDg+ZayQAwmmelxaU8AMEQuMjihJLCii3LCLKEmpsCP6el3vPNIIZSifHps="
- AWS_REGION="us-east-1"
- ATHENA_DB=your db athena
- S3_STAGING_DIR="storage"
- FLASK_SECRET_KEY=lks
- API_GATEWAY_URL="https://3xcvoqzhw3.execute-api.us-east-1.amazonaws.com/"
- SNS_TOPIC_ARN=your sns topic
- ATHENA_SCHEMA_NAME=your db athena


## Environment for Github Action
- AWS_ACCESS_KEY_ID=your access key id
- AWS_SECRET_ACCESS_KEY=your secret access key
- AWS_SESSION_TOKEN=your session token
- AWS_REGION=your default region
- ECR_REGISTRY= your ecr registry id
- ECR_REPOSITORY = your ecr name
- CLUSTER_NAME = your name cluster EKS

## Install Dependencies
`pip install -r requirements.txt`

## 📊 Query Athena


```sql
CREATE EXTERNAL TABLE IF NOT EXISTS rekognition_results_db.rekognition_results_table (
  image_key string,
  labels array<struct<Name:string, Confidence:double>>
)
ROW FORMAT SERDE 'org.openx.data.jsonserde.JsonSerDe'
WITH SERDEPROPERTIES (
  'serialization.format' = '1'
)
LOCATION 's3://your-destination-bucket/results'
TBLPROPERTIES ('has_encrypted_data'='false');
