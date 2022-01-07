---
  title: "AWS Cloud"
---
# Intro
# Background
# Techniques
# Resources

Amazon s3 object storage servce, objects are stored in buckets

#### discovering bucket names
example links
http://BUCKETNAME.s3.amazonaws.com/FILENAME.ext
http://s3.amazonaws.com/BUCKETNAME/FILENAME.ext

#### list the contents of buckets with curl and amazon cli
`curl http://irs-form-990.s3.amazonaws.com/`

`aws s3 ls s3://irs-form-990/ --no-sign-request`
The option --no-sign-request allows you to request data from S3 without being an AWS Customer. 

Downloading an object from S3 is also easy. You can use curl:
`curl http://irs-form-990.s3.amazonaws.com/201101319349101615_public.xml`
`aws s3 cp s3://irs-form-990/201101319349101615_public.xml . --no-sign-request`

#### find the acount id belonging to access key
`aws sts get-access-key-info --access-key-id AKIAEXAMPLE `
`aws sts get-access-key-info --access-key-id AKIAQI52OJVCPZXFYAOI`
#### determining the username the access key belongs to
`aws sts get-caller-identity --profile PROFILENAME`

Listing all the EC2 instances running in an account
`aws ec2 describe-instances --output text --profile PROFILENAME`
`aws ec2 describe-instances --output table --profile PROFILENAME`

Listing all the EC2 instances running in an account in a different region
`aws ec2 describe-instances --output text --region us-east-1 --profile PROFILENAME`

# secretsmanager

`aws secretsmanager list-secrets --profile test`
`aws secretsmanager get-secret-value --secret-id HR-Password --profile test --region eu-north`
