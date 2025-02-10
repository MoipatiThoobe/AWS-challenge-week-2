# AWS-challenge-week-2
Week 2 of the 12 weeks of AWS challenge

The second week of this challenge focused of AWS IAM. AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources. You use IAM to control who is **authenticated** (signed in) and who is **authorized** (has permissions) to use resources. With IAM, you define who can access what by specifying fine-grained permissions, IAM then enforces those permissions for every request. 

## IAM Users Hands On Lab

An IAM user is an entity that you create in AWS to represent the person or application that uses it to interact with AWS, a user in AWS consists of a name and credentials. There are 2 types of users in AWS, **account owner (root user)** or an **AWS Identity and Access Management (IAM) user. The root user is created when the AWS account is created and IAM users are created by the root user or IAM administrator for the account. All AWS users have security credentials. 

In the Hands On lab we did the following: 
1. Created an IAM user
2. Created a password for the user
3. Attached permissions to the IAM user that gave them administrator privileges
4. Used Multi factor authentication to secure the user

A screenshot of the successful creation of the Administrator user

<img width="946" alt="2" src="https://github.com/user-attachments/assets/678174a1-e087-4698-b59b-0f5b8705c626" />

A screenshot of the AWS console after logging in as the Administrator user

<img width="940" alt="3" src="https://github.com/user-attachments/assets/a9f3bec2-5800-4678-9493-2a43ee4a79f9" />

Multi-Factor authentication (MFA) is used to help protect your AWS resources. You can enable MFA for IAM users or the AWS account root user. When you enable MFA for the root user, it affects only the root user credentials. IAM users in the account are distinct identities with their own credentials, and each identity has its own MFA configuration. 

There are different types of MFA devices:
* Virtual MFA
* U2F Security key
* Hardware MFA

A screenshot of a virtual MFA device being setup to secure the Administrator user

<img width="956" alt="1" src="https://github.com/user-attachments/assets/68924447-990f-4ed1-9b78-a4900fe6bc7a" />

## IAM User groups

An IAM user group is a collection of IAM users. User groups let you specify permissions for multiple users which can make it easier to manage the permissions for those users. The following are important characteristics of user groups:
* A user group can contain many users, and a user can belong to multiple user groups
* User groups cannot contain other user groups
* There is no default user group that automatically includes all users in the AWS account. If you want to have a user group like that, you must create it and assign each new user to it

In the Hands on lab, we did the following:
1. Created a new user with no permissions called PowerUser
2. Created a new user group called Developers and attached permissions to the user group
3. Added PowerUser user to the Developers group. Doing this granted them permissions to manage EC2 Server resources.

A screenshot showing that the new user was successfully created

<img width="953" alt="1" src="https://github.com/user-attachments/assets/07318160-2472-46d5-adc2-71f6aeb3a3a2" />

A screenshot showing that the new user group was successfully created

<img width="949" alt="2" src="https://github.com/user-attachments/assets/8e94486f-bd38-40a8-b3c0-7141342ae986" />

A screenshot showing the users inside of the user group

<img width="953" alt="4" src="https://github.com/user-attachments/assets/4aa5cfd0-7cce-4048-b02d-855ded836a13" />

A screenshot showing the removal one user from the user group

<img width="953" alt="5" src="https://github.com/user-attachments/assets/e6685c63-70da-4212-8f67-56bd8b240127" />

A screenshot showing the attachment of a new policy to the user group

<img width="955" alt="6" src="https://github.com/user-attachments/assets/211abf5f-7116-4398-aacf-d9149d13706e" />

A screenshot showing the editing of user group details. The name of the user group was updated from 'Developers' to 'Developer'.

<img width="950" alt="7" src="https://github.com/user-attachments/assets/9af95452-d494-4588-85ff-e69617e9afe4" />

A screenshot showing the deletion of the user group

<img width="953" alt="8" src="https://github.com/user-attachments/assets/258c9abe-6a15-44fa-845f-2cc58fed5fe1" />

