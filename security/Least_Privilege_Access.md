# Understand Least Privilege by Denying Access


## How IAM Policies are evaluated
* Actions - What can be done?
* Resources - Which resource?
* Conditions - When can it be done?
* Explicit Deny - Always takes precedence and overrides any allow

## Example policy evaluation
* Scenario: User tries to get a file from S3 Bucket

```json
{
    "Effect":"Allow",
    "Action":"s3:GetObject",
    "Resource":"arn:aws:s3::my-bucket/*"
}
```