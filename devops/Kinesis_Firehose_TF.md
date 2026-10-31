# Provisioning AWS Kinesis and Firehouse for Streaming Data Pipeline using Terraform
> Create an AWS Kinesis Firehose delivery stream that receives streaming records, appends a newline delimiter after each one, and delivers batched data to an S3 bucket. The Firehose must securely access the S3 bucket by assuming an IAM role via STS, following the principle of least privilege.

## Architecture Components
* `aws_s3_bucket`:The final destination for all Firehose records
* `aws_iam_role`: Grants Firehose the identity it needs via STS Assume Role
* `aws_iam_policy`: Scoped `s3:PubObject` permission on the bucket's ARN profile
* `aws_iam_role_policy_attachment`: Binds the policy to the role
* `aws_kinesis_firehose_delivery_stream`: The core pipeline resource. Uses `extended_s3_configuration` for buffering and the `AppendDelimiterToRecord` processor for newline formatting