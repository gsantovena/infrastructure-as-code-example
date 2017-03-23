# infrastructure-as-code-example
Example of how to use AWS CodePipeline and AWS CloudFormation together for IaC

[Sample Template](https://s3-us-west-2.amazonaws.com/cloudformation-templates-us-west-2/WordPress_Multi_AZ.template)

## Requirements

We need to create two roles, one for CodePipeline and one for CloudFormation:

```
aws iam create-role \
    --role-name MyPipelineRole \
    --assume-role-policy file://pipeline-trust-policy.json

aws iam put-role-policy \
    --role-name MyPipelineRole \
    --policy-name MyPipelinePolicy \
    --policy-document file://pipeline-role-policy.json
```

```
aws iam create-role \
    --role-name MyCloudFormationRole \
    --assume-role-policy file://cfn-trust-policy.json

aws iam put-role-policy \
    --role-name MyCloudFormationRole \
    --policy-name MyCloudFormationPolicy \
    --policy-document file://cfn-role-policy.json
```

