# Installing AWS-Vault commandline hints

Below are some commond AWS-Vault commands which you may find helpful. 

**Disclaimer:** 

Before attempting these commands, please set your aws config file.  The default locations for your aws config file are:

    a.	Windows: %USER_PROFILE%\.aws\config

    b.	Mac/Linux: ~/.aws/config

An example of an AWS config file for an SSO Login is:


```sh
[profile mycompany-dev]
sso_account_id=728934728934
sso_start_url=https://d-42343242.awsapps.com/start/
sso_region=eu-west-1
region=eu-west-1
output=json
sso_role_name=Administrator

[profile mycompany-production]
sso_account_id=2342342234234
sso_start_url=https://d-42343242.awsapps.com/start/
sso_region=eu-west-2
region=eu-west-1
output=json
sso_role_name=ReadOnly
```


1.	List all of the AWS Accounts registered in the .aws/config file.  This command is also useful for checking which accounts have open sessions.

```sh
aws-vault list
```

2.	List all of the AWS Accounts registered in the .aws/config file.  This command is also useful for checking which accounts have open sessions.

```sh
aws-vault login <profile>
```

3.	Logout of all of the AWS-Vault sessions
```sh
aws-vault clear
```

4.	Execute a commandline tool, such as aws cli using a specific aws-vault session. Do not forget the double minus-sign (--) between the aws-vault profile name and the command you wish to execute.  If you do forget this you may get some odd, error messages.
```sh
aws-vault exec <profile> -- <command>
```

e.g 
```sh
aws-vault exec devAdministratorProfile -- aws s3 ls --region eu-west-1
```

You can also just enter aws-vault session and use the command line as normal (type "exit" to close the aws-vault session):

```sh
aws-vault exec <profile>
```

 
