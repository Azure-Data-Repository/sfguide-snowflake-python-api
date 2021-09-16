# A Simple API Powered by Snowflake

Technologies used: [Snowflake](https://snowflake.com/), [Python](https://www.python.org/), [Flask](https://palletsprojects.com/p/flask/), [AWS API Gateway](https://aws.amazon.com/api-gateway/), [AWS Lambda](https://aws.amazon.com/lambda/), [Serverless Framework](https://www.serverless.com/)

Requirements: 
* Snowflake.com and Serverless.com account
* node.js, python 3, virtualenv installed
* Citibike data loaded into Snowflake
* Snowflake user authorized to access citibike data with key pair authentication

This project demonstrates how to build and deploy a custom API powered by Snowflake. It uses a simple Python Flask API service running on AWS Lambda using Serverless Framework. Connectivity to Snowflake is made via key pair authentication.

## Configuration

Copy the config-template.py to config.py and modify the parameters according to your Snowflake configuration.

Install serverless and other required node packages and configure serverless (sls) for the project.

```bash
npm install
sls login
```

Create a virtualenv locally and install python packages.

```bash
virtualenv venv --python=python3
source ./venv/bin/activate
pip install -r requirements.txt
```

## Local Development

For local development you will want to use the venv previously created. This will run a local application server and connect to your Snowflake account for data access.

Start the local serverless server.

```bash
sls wsgi serve
```

### Invocation

After successful startup, you can call the created application via HTTP:

```bash
curl http://localhost:5000/
```

Which should result in the following response:

```json
{"result":"Nothing to see here", "time_ms": 0}
```

## Deployment

Build and deploy the application to AWS. For your first time, you will have to run sls without deploy to configure the project.

```bash
sls deploy
```

### Invocation

After successful deployment, you can call the created application via HTTP:

```bash
curl https://xxxxxxx.execute-api.us-west-2.amazonaws.com/dev/
```

Which should result in the following response:

```json
{"result":"Nothing to see here", "time_ms": 0}
```

