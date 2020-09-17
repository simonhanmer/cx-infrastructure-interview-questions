# Scenario 1

## Cloudformation Issues:
* IAM Role: Python code isn't using XRay, and no reference to EC2 manipulation so using principle of least priviledge, change role to reference AWSLambdaBasicExecutionRole managed policy, allowing lambda to publish logs
* Missing parameters
* Lambda Function:
  * mismatch between python code and CFN function handler - changed CFN to match
  * No runtime specified
  * CFN needs ARN so change to use !GetAtt instead of !Ref
  * To use DeploymentPreference (and later alarms), we need a code alias. We could define a new resource AWS::Lambda::Alias, but for simplicity go with AutoPublishAlias referencing a parameter