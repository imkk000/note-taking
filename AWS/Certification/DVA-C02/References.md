# Amazon Resource Names
- ARNs
- Uniquely identify AWS resources
- Require an ARN when need to specify a resource unambiguously across all of AWS

## Format
- partition: the resource is located (`aws`, `aws-cn`, `aws-us-gov`)
- service: the service namespace that identifies the AWS product
- region: the region code. (`ap-southeast-2`)
- account-id: the id of the AWS account that owns the resource, without the hyphens
- resource-type: the resource type (`VPC`, `iam`)
- resource-id: the resource identifier which is the name of the resource, the id of the resource, or a resource path
    - IAM user: `arn:aws:iam::123456789012:user/johndoe`
    - SNS topic: `arn:aws:sns:us-east-1:123456789012:example-sns-topic-name`
    - VPC: `arn:aws:ec2:us-east-1:123456789012:vpc/vpc-0e9801d129EXAMPLE`

```
arn:partition:service:region:account-id:resource-id
arn:partition:service:region:account-id:resource-type/resource-id
arn:partition:service:region:account-id:resource-type:resource-id
```

# Path
- Resource ARNs can include a path
    - For example, in Amazon S3, the resource identifier is an object name that can include slashes (/) to form a path. Similarly, IAM user names and group names can include paths.
- Path can include a wildcard character, namely an asterisk (*)

```json
{
    "Resource": "arn:aws:iam::123456789012:user/*",
    "Resource": "arn:aws:iam::123456789012:group/*"
}
```

# Reference
- https://docs.aws.amazon.com/IAM/latest/UserGuide/reference-arns.html
