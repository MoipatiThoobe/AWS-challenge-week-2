# AWS-challenge-week-2
Week 2 of the 12 weeks of AWS challenge

The second week of this challenge focused of AWS IAM. AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources. You use IAM to control who is **authenticated** (signed in) and who is **authorized** (has permissions) to use resources. With IAM, you define who can access what by specifying fine-grained permissions, IAM then enforces those permissions for every request. 

## IAM Users

An IAM user is an entity that you create in AWS to represent the person or application that uses it to interact with AWS, a user in AWS consists of a name and credentials. There are 2 types of users in AWS, **account owner (root user)** or an **AWS Identity and Access Management (IAM) user. The root user is created when the AWS account is created and IAM users are created by the root user or IAM administrator for the account. All AWS users have security credentials. 

In the Hands On lab, I did the following: 
* Created an IAM user
* Created a password for the user
* Attached permissions to the IAM user that gave them administrator privileges
* Used Multi factor authentication to secure the user

1. Create of the Administrator user

<img width="946" alt="2" src="https://github.com/user-attachments/assets/678174a1-e087-4698-b59b-0f5b8705c626" />

2. Login in to the AWS Management console as the Administrator user

<img width="940" alt="3" src="https://github.com/user-attachments/assets/a9f3bec2-5800-4678-9493-2a43ee4a79f9" />

Multi-Factor authentication (MFA) is used to help protect your AWS resources. You can enable MFA for IAM users or the AWS account root user. When you enable MFA for the root user, it affects only the root user credentials. IAM users in the account are distinct identities with their own credentials, and each identity has its own MFA configuration. 

There are different types of MFA devices:
* Virtual MFA
* U2F Security key
* Hardware MFA

3. virtual MFA device being setup to secure the Administrator user

<img width="956" alt="1" src="https://github.com/user-attachments/assets/68924447-990f-4ed1-9b78-a4900fe6bc7a" />

## IAM User groups

An IAM user group is a collection of IAM users. User groups let you specify permissions for multiple users which can make it easier to manage the permissions for those users. The following are important characteristics of user groups:
* A user group can contain many users, and a user can belong to multiple user groups
* User groups cannot contain other user groups
* There is no default user group that automatically includes all users in the AWS account. If you want to have a user group like that, you must create it and assign each new user to it

In the Hands on lab, I did the following:
* Created a new user with no permissions called PowerUser
* Created a new user group called Developers and attached permissions to the user group
* Added PowerUser user to the Developers group. Doing this granted them permissions to manage EC2 Server resources.

1. Create a new user

<img width="953" alt="1" src="https://github.com/user-attachments/assets/07318160-2472-46d5-adc2-71f6aeb3a3a2" />

2. Create a new user group

<img width="949" alt="2" src="https://github.com/user-attachments/assets/8e94486f-bd38-40a8-b3c0-7141342ae986" />

3. List the users inside of the user group

<img width="953" alt="4" src="https://github.com/user-attachments/assets/4aa5cfd0-7cce-4048-b02d-855ded836a13" />

4. Remove one user from the user group

<img width="953" alt="5" src="https://github.com/user-attachments/assets/e6685c63-70da-4212-8f67-56bd8b240127" />

5. Attach a new policy to the user group

<img width="955" alt="6" src="https://github.com/user-attachments/assets/211abf5f-7116-4398-aacf-d9149d13706e" />

 6. Edit the user group details. The name of the user group was updated from 'Developers' to 'Developer'.

<img width="950" alt="7" src="https://github.com/user-attachments/assets/9af95452-d494-4588-85ff-e69617e9afe4" />

7. Delete the user group

<img width="953" alt="8" src="https://github.com/user-attachments/assets/258c9abe-6a15-44fa-845f-2cc58fed5fe1" />

## IAM Roles

An IAM Role is similar to a user, in that it is an AWs identity with permission policies that determine what the identity can and cannot do in AWS. A role does not have any credentials (password or access keys) with it, that is how it is different from IAM Users. Instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it. An IAM role user can assume a role to temporarily takes on different permissions for a specific task. 

The hands on labs are seperated into the following sections:
1. Creating an IAM role
2. IAM Service Role
3. IAM Service Linked role

### Creating an IAM role hands on lab

1. Create a new IAM role

<img width="956" alt="1" src="https://github.com/user-attachments/assets/17ace6f0-ed52-4f6e-8cc8-30a883434e05" />

<img width="957" alt="2" src="https://github.com/user-attachments/assets/00c4bf39-99ec-4c14-84c1-9b8147dc7dae" />

### IAM Service Roles hands on lab

1. Create a new S3 bucket

<img width="946" alt="3" src="https://github.com/user-attachments/assets/c37cdbd8-adc9-4a11-81f6-2b7753461e51" />

2. Create an AWS Policy that allows reading (List) access to  S3 bucket

<img width="958" alt="4" src="https://github.com/user-attachments/assets/5250707b-c655-4f65-a56b-e0f8104d3f46" />

3. Create an AWS Service role that allows Lambda to access the S3 bucket

<img width="950" alt="5" src="https://github.com/user-attachments/assets/a81e6dea-6735-45ff-bddd-143d92b910d7" />

4. Create a new Lambda function

<img width="955" alt="6" src="https://github.com/user-attachments/assets/a38e2ad0-88f4-440e-866e-43318a37a1e4" />

5. Update the Lambda function code

<img width="952" alt="7" src="https://github.com/user-attachments/assets/ef1ad152-44b1-4e58-b096-db54512a00a3" />

6. Create a new test event for the function code

<img width="955" alt="8" src="https://github.com/user-attachments/assets/abdf6f77-a2d0-413a-afe5-b49bf023f61b" />

7. The execution of the Lambda function failed because Lambda does not have the required permissions to put an object into the S3 bucket

<img width="956" alt="9" src="https://github.com/user-attachments/assets/3617428a-7100-4833-9179-2d1b719b294a" />

8. To fix the error shown above, the Policy had to be updated to allow the Lambda function to put an object into the bucket

<img width="959" alt="10" src="https://github.com/user-attachments/assets/5346461d-0c21-45b0-b3d1-59c49ceef783" />

9. The execution of the Lambda function is now successful

<img width="954" alt="11" src="https://github.com/user-attachments/assets/1eff0049-a4c2-4bbb-aec9-66a15e96946f" />

10. A text file was successfully added to the S3 bucket using the Lambda function

<img width="957" alt="12" src="https://github.com/user-attachments/assets/4d5ad87a-0368-45ff-97ed-557c7e5825e8" />


### IAM Service linked role

A service-linked role is a unique type of IAM role that is linked directly to an AWS service. Service-linked roles are predefined by the service and include all the permissions that the service requires to call other AWs services on your behalf. Service-linked roles make setting up a service easier because you don't have to manually add the necessary permissions for the service to complete actions on your behalf. 

1. Create a target group for the load balancer

<img width="956" alt="1" src="https://github.com/user-attachments/assets/9c42ee82-d3c7-4598-a45c-42c557c20034" />

2. Create an application load balancer 

<img width="955" alt="2" src="https://github.com/user-attachments/assets/38dd2761-88f6-4e6e-a0a7-1d9b47817d5f" />

3. A new service linked role is created for the load balancer

<img width="959" alt="3" src="https://github.com/user-attachments/assets/5a77ef95-9934-464a-9309-45e046b940d1" />


## IAM Policies

A policy is an object in AWS that, when associated with an identity or resource, defines their permissions. You manage access in AWS by creating policies and attaching them to IAM identities (users, groups of users or roles) or AWs resources. AWS evaluates these policies when an IAM principal (user or role) makes a request. Permissions in the policies determine whether the request is allowed or denied. Most policies are stored in AWS as JSON documents. 

### Creating a custom policy hands on lab
In the hands on lab, we are going to create an AWS Identity policy to access to S3. We will then use the policy to test our access in our new account.

1. Specify the permissions of the policy, the policy gives the user "List" and "Read" permissions for S3 resources

<img width="956" alt="1" src="https://github.com/user-attachments/assets/fba855cb-9a11-4594-8af4-9aacc41b3f3a" />

2. Create the policy

<img width="953" alt="3" src="https://github.com/user-attachments/assets/d772f867-d48d-4420-8553-b0ab88b1ef3b" />

3. Create a new s3 bucket

<img width="951" alt="4" src="https://github.com/user-attachments/assets/cfe0bb5a-abc4-40b4-962d-5f7e2d09751b" />

4. Create a new text file named "test" and upload the file into the S3 bucket

<img width="958" alt="5" src="https://github.com/user-attachments/assets/11c8db0c-e1bc-42d8-89aa-5d14692007b0" />

5. Create a new IAM user and attach the policy that we previously created to the user

<img width="953" alt="6" src="https://github.com/user-attachments/assets/46f16330-f960-48a7-9920-9108fb1a7b49" />

6. Open an incognito tab/window and sign into the AWS management console using the credentials of the new user

<img width="950" alt="7" src="https://github.com/user-attachments/assets/98c0a413-288e-41c2-b3e1-1b561e887e78" />

7. Because of the policy the IAM user is able to access the S3 bucket and download its objects

<img width="955" alt="9" src="https://github.com/user-attachments/assets/89876698-ef48-4b54-900a-3960c0d3192f" />

8. An error occurred when trying to delete the object because the IAM user does not have permissions to delete S3 objects

<img width="956" alt="10" src="https://github.com/user-attachments/assets/b85c6fac-c69b-4af4-972f-f97b98e99f83" />

## Programmatic access

Programmatic access is used when service applications and operational tools require non-human access in order to make requests to AWS services. There are twp ways to grant access to AWS resources:
* IAM User Access keys
* Delegating IAM rules

### IAM User Access keys
Access keys are a type of IAM User credential consisting of an Access Key ID and a Secret access key. These keys can be used to together for programmatic access to AWS resources. Command line scripts and applications that access AWS can use these credentials without any need for a human user. 

In the hands on lab, I will do the following:
* Create a new IAM user with Access keys
* Configure the AWS command line interface (CLI) with the new credentials to gain programmatic access to AWS resources

1. Create a new IAM user and attach a policy with read only access to S3
   
<img width="953" alt="1" src="https://github.com/user-attachments/assets/0db193c3-a749-4c0e-b80f-f4ebd8acd039" />

2. Create an access key for the user

<img width="958" alt="2" src="https://github.com/user-attachments/assets/cd03285e-1196-4457-bd4e-ffb52da4a467" />

3. Download the access key and modify the .csv file to include a User Name header. You can do this by opening the file in a text editor like Notepad or TextEdit. Export/Save the file with the UTF-8 encoding. 

<img width="445" alt="3" src="https://github.com/user-attachments/assets/a65d8f90-1bc6-4814-8f7e-b0030f26913b" />

4. Open a command line terminal, import the .csv that was downloaded. Use the AWs configure import command with the --csv option as follows: aws configure import --csv file://CLIUser_accessKeys.csv

<img width="720" alt="4" src="https://github.com/user-attachments/assets/c5d108ee-a338-4474-a085-e9e6c0270ab1" />

5. Verfiy that the credentials have been properly imported by running a command to list all profiles: aws configure list-profiles

<img width="513" alt="5" src="https://github.com/user-attachments/assets/01a7fd3d-c7b6-450c-b734-0e866398c024" />

6. Verify that the credentials were set up properly by running a command to list S3 buckets: aws s3 ls --region us-east-1 --profile CLIUser

<img width="641" alt="6" src="https://github.com/user-attachments/assets/3cb02b1b-852b-4edf-91b8-478a1d084036" />

7. Open CloudShell in AWS management console and configure a new profile called 'testUser'

<img width="242" alt="7" src="https://github.com/user-attachments/assets/1d2119d7-e4b0-4028-a203-67a0093f0de3" />

8. Attempt to print out the S3 buckets, this command will fail because the profile we are using does not have any valid credentials associated wih it

<img width="722" alt="8" src="https://github.com/user-attachments/assets/ace453c0-77ca-470d-99a9-a987793c65fc" />

9. Reconfigure the profile with the Access key ID and Secret Access key

<img width="446" alt="9" src="https://github.com/user-attachments/assets/f7479217-fb1f-4ade-85fc-86308613066c" />

10. Verify that the profile and credentials were set up properly by running the command to list the S3 buckets

<img width="415" alt="10" src="https://github.com/user-attachments/assets/5108e0fc-ebcd-499d-a9d4-b6f96da30a87" />


### Delegating IAM roles

As there are no credentials associated with IAM roles, there is no risk of anyone taking the credentials and accessing your resources. For this reason, delegating roles is considered best practice for providing access to AWS resources. 






