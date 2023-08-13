# IAM: Users and Groups
- IAM = Identity and Access Management, Global Services
- Root account created by default, shouldn't be used or shared
- Users are people within your organization, and can be grouped
- Users don't have to belong to a group, and user can belong to multiple groups
![iam](./Images/iam_users_groups.png =500x)

# IAM: Permissions
- Users or Groups can be assigned JSON documents called policies
- These policies define the permissions of the users
- In AWS you apply the least privilege principle
    - **Don't give more permissions than a user needs**

![iam](./Images/iam_policies.png =300x)

# IAM Policies inheritance
- Policies from group that can be overridden directly policies

![iam](./Images/iam_policies_inheritance.png =450x)

## IAM Policies Structure
- Consists of
    - Version: policy language version
    - Id: an identifier for the policy (optional)
    - **Statement**: one or more individual statements (required)
- Statements consists of
    - Sid: an identifier for the statement (optional)
    - Effect: whether the statement allows or denies access (Allow, Deny)
    - Principal: account/user/role to which this policy applied to
    - Action: lost of actions this policy allows or denies
    - Resource: list of resources to which the actions applied to
    - Condition: conditions for when this policy is in effect (optional)

![iam](./Images/iam_policies_structure.png =350x)

## IAM Password Policy
- Strong passwords = higher security for the accounts
- Allow all IAM users to change their own passwords
- Require users to change their password after some period time (password expiration)
- Prevent password re-use
- A password policy:
    - Set a minimum password length
    - Require specific character types:
        - uppercase letters
        - lowercase letters
        - numbers
        - non-alphanumeric characters

![ iam ](./Images/iam_password_policy.png =500x)

### Multi Factor Authentication (MFA)
- Users have access to the account and can possibly change configurations or delete resources
- Want to protect **Root Accounts and IAM users**
- MFA = known password + security devices
- Benefit: if a password is stolen or hacked, the account is not compromised
- Types
    - Virtual MFA Device: support for multiple tokens on a single device
        - Google Authenticator
        - Authy
    - Universal 2nd Factor (U2F) Security Key
        - YubiKey
    - Hardware Key Fob MFA Device
    - Hardware Key Fob MFA Device for AWS GovCloud (US)
