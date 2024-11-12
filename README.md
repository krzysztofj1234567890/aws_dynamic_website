# aws_dynamic_website

Very nice tutorial: https://developer.hashicorp.com/terraform/tutorials/aws/lambda-api-gateway and https://github.com/aws-samples/serverless-patterns/blob/main/apigw-lambda-dynamodb-terraform/variables.tf

## Setup

Check aws configration

```
cat ~/.aws/*
```

## Deploy

```
terraform init
terraform plan
terraform apply
```

### Test

Test lambda
```
aws lambda invoke --region=us-east-1 --function-name=$(terraform output -raw function_name) response.json
cat response.json
```

Test lambda and API gateway
```
curl "$(terraform output -raw base_url)/hello"
curl "$(terraform output -raw base_url)/hello?Name=Terraform"
```

## Destroy

```
terraform destroy
```