#verify the template syntax 

aws cloudformation validate-template --template-body file://example.yaml

#create stack

aws cloudformation create-stack \
  --stack-name my-infra-stack \
  --template-body file://example.yaml \
  --parameters ParameterKey=KeyName,ParameterValue=cwinkp ParameterKey=InstanceType,ParameterValue=t2.micro \
  --capabilities CAPABILITY_NAMED_IAM \
  --region us-west-1

#describe stack

aws cloudformation describe-stacks \
  --stack-name my-infra-stack \
  --region us-west-1

#update stack

aws cloudformation update-stack \
  --stack-name my-infra-stack \
  --template-body file://example.yaml \
  --parameters ParameterKey=KeyName,ParameterValue=cwinkp ParameterKey=InstanceType,ParameterValue=t2.micro \
  --capabilities CAPABILITY_NAMED_IAM \
  --region us-west-1

#delete stack

aws cloudformation delete-stack \
  --stack-name my-infra-stack \
  --region us-west-1

#note

Make sure ami-040ff3f52a5f9a7bb is valid for your region (us-west-1)

Use GetAZs to dynamically fetch Availability Zones

Customize tags to fit your team/environment
