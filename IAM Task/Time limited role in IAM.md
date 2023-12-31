•	Create IAM roles with time-limited permissions for EC2 instances.

1.	Click on roles tab in IAM services.
2.	Click on “Click role”, it will open a window.
3.	Select “AWS service” as a entity type and for Use Case select “EC2” and then press Next.
4.	Then click “Create Policy” it will open a new tab of the policy.
5.	Click on JSON tab as we want a custom policy. 
6.	Custom policy code – 

```
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Effect": "Allow",
			"Action": [
				"ec2:*"
			],
			"Resource": "*",
			"Condition": {
				"DateGreaterThan": {
					"aws:CurrentTime": "2023-09-01T00:00:00Z"
				},
				"DateLessThan": {
					"aws:CurrentTime": "2023-09-15T14:59:59Z"
				}
			}
		}
	]
}
```

7.	The above policy states that this policy has full access of EC2 instance that is been created on 1 September 2023 at midnight and the policy will be expired on 15 September 2023 before 16 September 2023
8.	Give proper name and Description of the policy, Click Create Policy.
9.	The policy creation notification would be shown above.
