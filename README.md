# AWS Lambda simple functionality written in Go


# Requirements
- [go](https://go.dev/doc/tutorial/getting-started)
- [AWS](https://aws.amazon.com/)

# Quickstart
```
git clone https://github.com/Nedick/go-aws-lambda.git
cd go-aws-lambda
GOARCH=amd64 GOOS=linux go build main.go
zip function.zip main
```

# Usage
```
aws iam create-role --role-name your-role-name --assume-role-policy-document file://trust-policy.json

aws iam attach-role-policy --role-name your-role-name --policy-arn arn:aws:iam::aws:policy/service-role/AWSLambdaBasicExecutionRole

aws lambda create-function --function-name your-function-name \
--zip-file fileb://function.zip --handler main --runtime go1.x \
--role arn:aws:iam::yourTwelveDigitIdGoesHere:role/your-role-name

aws lambda invoke --function-name your-function-name --cli-binary-format raw-in-base64-out --payload '{"What is your name?": "YourName","How old are you?": 32}' output.txt --log-type Tail
```
