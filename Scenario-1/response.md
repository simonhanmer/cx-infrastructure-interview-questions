# Scenario 1

## Issues:
* IAM Role: Python code isn't using XRay, and no reference to EC2 manipulation so using principle of least priviledge, change role to reference AWSLambdaBasicExecutionRole managed policy, allowing lambda to publish logs