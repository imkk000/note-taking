# How can users access AWS?
- AWS Management Console: protected by **password + MFA**
- AWS Command Line Interface (CLI): protected by **access keys**
- AWS Software Developer Kit (SDK): for code which protected by **access keys**

# Access Keys
- Generated through the AWS Console
- Users manage their own access keys
- Access Keys are secret, just like a password.
    - **Don't share them**
- Equivalent
    - Access Key ID ~= username
    - Secret Access Key ~= password

# AWS CLI
- A tool that enables you to interact with AWS services using commands in your command-line shell
- Direct access to the public APIs of AWS services
- Can develop scripts to manage the resources
- Alternative to using AWS Management Console
- Repository: https://github.com/aws/aws-cli

# AWS SDK
- Language-specific APIs (set of libraries)
- Enables to access and manage AWS services programmatically
- Embedded within the application
- Supports
    - SDKs (JS, Python, PHP, .NET, Ruby, Java, Go, NodeJS, C++)
    - Mobile SDKs
    - IoT Device SDKs
