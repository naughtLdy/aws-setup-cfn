# AWS インフラ管理
AWSの全サービス共通のインフラを管理する

# Create Package
```bash
$ aws cloudformation package \
  --template-file src/cfn.template.yml \
  --s3-bucket naughtldy-artifact \
  --s3-prefix template/all-infra \
  --output-template-file .cfn/packaged.yml
```

# Create Stack
```bash
$ aws cloudformation create-stack \
  --stack-name all-infra \
  --template-body .cfn/packaged.yml \
  --capabilities CAPABILITY_NAMED_IAM
```

# Update Stack
```bash
$ aws cloudformation update-stack \
  --stack-name all-infra \
  --template-body .cfn/packaged.yml \
  --capabilities CAPABILITY_NAMED_IAM
```
