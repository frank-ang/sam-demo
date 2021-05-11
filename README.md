# SAM Serverless Lambda pipeline demo

## Setting up.

### First deployment

```bash
sam init
# wizard: select Python 3.8 hello template
cd sam-hello
sam build
sam deploy --guided
```
### Setup CodePipeline, CodeBuild

Create buildspec.yaml

Push to repo and observe CodePipeline and CodeBuild success.

### CodeDeploy

```bash
sam package --template-file template.yaml --output-template-file package.yaml --s3-bucket sandbox00-sam-hello
sam deploy --template-file package.yaml --stack-name sam-hello --capabilities CAPABILITY_IAM
```

### Unit Test

```bash
python -m pytest tests/unit/ -v
```

### Integration Test

```bash
export AWS_SAM_STACK_NAME="sam-hello"
python -m pytest tests/integration/ -v

```

### Run API Gatewway Locally

Requires Docker to be running.
```bash
sam local start-api &
curl http://localhost:3000/hello 
```