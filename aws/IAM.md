### Basic information about IAM
- IAM stands for Identity and Access Management, it's a Global service
- Users are people within your organization, and can be assigned to groups
- Groups only contain users, not other groups
- Users is not enforced to be in any group, and can be in multiple goups at once

### IAM: Permissions
- Users or groups can be assigned to JSON documents called policies
- Theses policies define permissions of the users
- In AWS we need to apply the **least privilege principle**
- A policy defined directly to the user is called **inline policy**

### IAM Policies Structure

- Policy Structure example:
```json
{
	"Id": "SuperCoolPolicy",
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
	            "AWS": ["arn:aws:iam::123456789012:root"]
            },
            "Action": "service-prefix:action-name",
            "Resource": "*",
            "Condition": {
                "DateGreaterThan": {"aws:CurrentTime": "2024-04-01T00:00:00Z"},
                "DateLessThan": {"aws:CurrentTime": "2024-06-30T23:59:59Z"}
            }
        }
    ]
}
```

- The policy consists in the `Version`that contains the policy language version, an `Id (optional)` that contains an identifier to the policy, and one or more `Statements` that define the policy
- Statements structure:
	- `Sid (optional)`: Identifier of the statement
	- `Effect`: Informs if the statement allow or disallow certain action
	- `Principal`: account/user/role to which this policy is applied to
	- `Action`: list of actions this policy allows or denies
	- `Resource`: List of resources to with the actions applied to
	- `Condition (optional)`: Conditions to when the policy will be in effect (In the example, the policy will only be enabled from 2024-04-01 and 2024-06-30)

### IAM Password Policy
- In AWS we can setup a password policy that can enable any of these rules:
	- Set a minimum password length
	- Require specific character types:
		- Uppercase letters
		- Lowercase letter
		- Number
		- Non-alphanumeric characters
	- Allow all users to change their own passwords
	- Enable password expiration
	- Prevent password re-use
- Multi Factor Authentication
	- Virtual MFA Device (e.g. Google Authenticator) - Support for multiple tokens on sigle device
	- Universal 2nd Factor (U2F) Security Key (e.g. Yubikey) - Support for multiple root and IAM users using a single security key
	- Hardware Key Fob MFA Device (e.g. Gemalto) - Fisical token that displays the current pin on the screen
	- Hardware Key Fob MFA Device for AWS GovCloud (US) (Provide by SurePassID) - Same as Hardware Key Fob, but specific to the GovCloud

### Options to Access AWS
- To access AWS we have three options:
	- AWS Management Console: Protected by password + MFA
	- AWS Command Line Interface (CLI): Protected by access keys
	- AWS Software Developer Kit (SDK): Protected by access keys
- Access Keys are generated through the AWS Console
- Users manage their own access keys

### IAM Roles for Services
- Services in AWS may do actions in the account
- For that, they need to have a role that allows then to execute the required actions
- Example: EC2 may need to read messages from SQS, so it will need a role that has the permission to do that (policy attached to the role)

### IAM Security Tools
- IAM Credentials Report (accont-level)
	- A report that lists all your account's users and the status of their various credentials
- IAM Access Advisor (user-level)
	- Access advisor shows the service permissions granted to a user and when those services were last accessed