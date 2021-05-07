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
