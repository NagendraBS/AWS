# IAM SERVICES
# What is IAM
* AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources.
* With IAM, you can manage permissions that control which AWS resources users can access.
* You use IAM to control who is authenticated (signed in) and authorized (has permissions) to use resources.


* IAM stands for Identity and Access Management. 
* It is a foundational service provided by AWS (Amazon Web Services) for managing ```users, groups,  roles,``` and ```their permissions``` within AWS cloud infrastructure. That enables you to manage access to AWS InfraStructure Services and resources securely.
* However IAM will be having Least Privileged principle.

Exp : (IAM will Recognise any User in the way that, Weather that user is an Identified user or Not, If USER is an identified user then the IAM will Provide the permission to user for Accessing any available AWS Infrastructure Service , thats why it is Called as  "```IDENTITY``` and ```ACCESS MANAGEMENT```".)

----


# Root user
* When you create an AWS account, you begin with one sign-in identity that has complete access to all AWS services and resources in the account.
* This identity is called the AWS account root user and is accessed by signing in with the email address and password that you used to create the account.


* Root User :
* The root user has unlimited permissions by default, including the ability to create and manage AWS resources,
* manage billing information, and manage IAM users and their permissions.

* The root user is typically considered the owner of the AWS account and has full control over billing, subscription management, and overall account settings.

```Important Considerations:```
* AWS strongly recommend that you don't use the ```root user``` for the Professional operations. Even though if you want to Use Root Users itself Means,
* ```AWS strongly recommends securing the root user account with multi-factor authentication (MFA) to add an additional layer of protection against unauthorized access.```

### Characteristics of the Root User :
* Created Automatically 
* Default Administrative Access Permissions 
* Highly Privileged



----  
# Why should I use IAM
* AWS Identity and Access Management is a powerful tool for securely managing access to your AWS resources.
* One of the primary benefits of using IAM is the ability to grant shared access to your AWS account.

### Advantages of using IAM (Identity and Access Management) 
* We Can Restrict the Access Permissions to the Required Users as per our organizational Requirements.
* We can define specific access policies based on roles and responsibilities within our organizations.
* IAM users support the best practice of ```least privilege```, which limits users to only the actions necessary for their specific tasks.
 

------
# How IAM works
<img width="1000" alt="image" src="https://github.com/sumanthrao04/Learning/assets/68411350/ebc8f8cb-2101-438b-b793-cca7eca510ea">

* First, a human user or an application uses their sign-in credentials to authenticate with AWS. 
* Authentication is provided by matching the sign-in credentials to a principal (an IAM user, federated user, IAM role, or application) trusted by the AWS account.
* when you first sign in to the console and are on the console Home page, you aren't accessing a specific service.
* When you select a service, the request for authorization is sent to that service and it looks to see if your identity is on the list of authorized users, what policies 
  are being enforced to control the level of access granted, and any other policies that might be in effect.
* Authorization requests can be made by principals within your AWS account or from another AWS account that you trust.
* Once authorized, the principal can take action or perform operations on resources in your AWS account.
* For example, the principal could launch a new Amazon Elastic Compute Cloud instance, modify IAM group membership, or delete Amazon Simple Storage Service buckets

# IAM Elements

### Principal
* Principal is a person or application that uses the AWS account wheater it may be root account,Iam user, federated users and assumed roles
*  Principal can make a request for an action or operation on an AWS resource.
*  Your administrative IAM user is your first principal.
*  After authentication,depending on the principal type the principal can be granted either permanent or temporary credentials to make requests to AWS

### Authentication
* A principal must be authenticated (signed in to AWS) using their credentials to send a request to AWS
  
#### Authentication Methods
<img width="1000" alt="image" src="https://github.com/user-attachments/assets/ad37fa00-9776-42be-b188-c98a96ea8fd5">

*  To authenticate from the console as a root user, you must sign in with your email address and password.
*  As a federated user(third party or user from outside company or application), you are authenticated by your identity provider and granted access to AWS resources by 
  assuming IAM roles. 
*  As an IAM user, provide your account ID or alias, and then your user name and password.
*  To authenticate workloads from the API or AWS CLI, you might use temporary credentials through being assigned a role or you might use long-term credentials by  
   providing  your access key and secret key.
*  AWS recommends that you use multi-factor authentication (MFA) and temporary credentials to increase the security of your account. 

 ### Request
* When a principal tries to use the AWS Management Console, the AWS API, or the AWS CLI, that principal sends a request to AWS.
* The request includes the following information:
* Principals send requests via the Console, CLI, SDKs, or APIs.
* Actions (or operations) that the principal wants to perform on aws resources and This can be an action in the AWS Management Console, or an operation in the AWS CLI or AWS API
*  Resources upon which the actions are performed.
*  Principal Information about the principal includes the policies that are associated with the entity that the principal used to sign in
*  Environment data – Information about the IP address, user agent, SSL enabled status, or the time of day.
* Resource data – Data related to the resource that is being requested. This can include information such as a DynamoDB table name or a tag on an Amazon EC2 instance.

### Authorization
* You must also be authorized (allowed) to complete your request.
* During authorization, AWS uses values from the request context to check for policies that apply to the request. 
* It then uses the policies to determine whether to allow or deny the request
* IAM policies are stored in IAM as JSON documents and specify the permissions that are allowed or denied.
* IAM policies can be:
    *User (identity) based policies -> users with permissions to access the AWS resources in their own account
    *Resource-based policies -> Resource-based policies are popular for granting cross-account access.
* IAM checks each policy that matches the context of your request.
*If a single policy has a deny action IAM denies the request and stops evaluating (explicit deny).

#### Evaluation logic: ( will learn in  Policy evaluation logic section in detail )
* By default all requests are denied (implicit deny).
* An explicit allow overrides the implicit deny.
* An explicit deny overrides any explicit allows.
* Only the root user has access to all resources in the account by default.  

### Actions or operations
* After your request has been authenticated and authorized, AWS approves the actions or operations in your request.
* Actions are defined by a service.
* Actions are the things you can do to a resource such as viewing, creating, editing, deleting.
* Any actions on resources that are not explicitly allowed are denied.
* To allow a principal to perform an action you must include the necessary actions in a policy that applies to the principal or the affected resource.
* example,IAM supports approximately 40 actions for a user resource, including the following actions:
- CreateUser
- DeleteUser
- GetUser
- UpdateUser

 ### Resources
* A resource is an object that exists within a service.
* E.g. EC2 instances, S3 buckets, IAM users, and DynamoDB tables.
* Each AWS service defines a set of actions that can be performed on the resource.
* After AWS approves the actions in your request, those actions can be performed on the related resources within your account.

### Another example for how IAM works
<img width="1000" alt="image" src="https://github.com/user-attachments/assets/cb85c07a-518e-4462-bd8d-4757f8d7bb3c">
<img width="1000" alt="image" src="https://github.com/user-attachments/assets/017e7cd2-7b6b-4a11-be1b-06ce05cd4799">
----  

### IAM Identities (users, user groups, and roles)
In AWS IAM (Identity and Access Management), users, user groups, and roles are fundamental concepts used to manage access to AWS services and resources securely. Here's a breakdown of each:

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/4ff931ae-8e9d-4d7d-b5be-cfefe91db1d0">


1. **Users**:
   - **Definition**: Users represent individual entities (people, applications, or services) within your organization who interact with AWS resources.
   - **Attributes**: Each user has a unique name and security credentials (such as password or access keys) associated with them.
   - **Usage**: Users are granted permissions directly, allowing them to perform actions and access resources based on those permissions.

2. **User Groups**:
   - **Definition**: User groups are collections of IAM users. By organizing users into groups, you can more easily manage permissions for multiple users simultaneously.
                     by appliying policies to the group, who were all part of that group means users in that group can access that polices 
   - **Attributes**: Groups have policies attached to them, defining what actions members of the group can perform on which AWS resources.
   - **Usage**: Assigning permissions to a group simplifies permissions management, especially in larger organizations where users have similar job roles or permissions 
                requirements.

3. **Roles**:
   - **Definition**: Roles are AWS identities with permissions policies attached. They are not associated with a specific user or group but are assumed by IAM users, AWS 
                     services, or other entities such as applications.
   - **Attributes**: Roles define what actions are allowed or denied when the role is assumed. They do not have their own credentials; instead, they are assumed using 
                     temporary security tokens.
   - **Usage**: Roles are used to delegate(Delegation, in a general sense, refers to the act of assigning tasks, responsibilities, or authority to another person or group 
                  of people.) access to AWS resources securely.

#### Key Points:
- **Permissions**: Users, groups, and roles all have permissions policies that specify what actions they can perform on which AWS resources.
- **Flexibility**: IAM allows you to finely control permissions by creating custom policies and attaching them to users, groups, or roles.
- **Security**: Roles are often used for cross-account access or granting permissions to AWS services, enhancing security by reducing the exposure of long-term 
                credentials.

  ---
  ### Users
  #### AWS account root user
  * When you first create an AWS account, you begin with one sign-in identity that has complete access to all AWS services and resources in the account.
  * This identity is called the AWS account root user and is accessed by signing in with the email address and password that you used to create the account.
  * The root account has full administrative permissions, and these cannot be restricted
    **** Best practice for root accounts:
  * Don’t use the root user credentials.
  * Don’t share the root user credentials.
  * Create an IAM user and assign administrative permissions as required.
  * Enable MFA.

  #### IAM users
  <img width="446" alt="image" src="https://github.com/user-attachments/assets/3b8076ad-59db-4586-af84-afe0345abf22">

  
 * An IAM user is an identity within your AWS account that has specific permissions for a single person or application.
 * An access key ID and secret access key for programmatic access to the AWS API, CLI, SDK, and other development tools.
 * A password for access to the management console.
 * IAM users can be created to represent applications, and these are known as “service accounts”.
 * You can have up to 5000 users per AWS account
 * Each user account has a friendly name and an ARN which uniquely identifies the user across AWS.
 * An Amazon Resource Name (ARN) for the IAM user ->  ```arn:aws:iam::account-ID-without-hyphens:user/Richard```
 * A unique ID is also created which is returned only when you create the user using the API, Tools for Windows PowerShell, or the AWS CLI.
 * The Access Key ID and Secret Access Key are not the same as a password and cannot be used to login to the AWS console.
 * The Access Key ID and Secret Access Key can only be generated once and must be regenerated if lost.
 * A password policy can be defined for enforcing password length, complexity etc. (applies to all users).
 * You can allow or disallow the ability to change passwords using an IAM policy.

   
#### IAM user groups


 * An IAM group is an identity that specifies a collection of IAM users. 
 * You can't use a group to sign-in. You can use groups to specify permissions for multiple users at a time.
 * Groups make permissions easier to manage for large sets of users.
 * A group is not an identity and cannot be identified as a principal in an IAM policy.
 * Use groups to assign permissions to users.
 * Use the principal of least privilege when assigning permissions.
 * A user group can contain many users, and a user can belong to multiple user groups.
 * User groups can't be nested; they can contain only users, not other user groups
 * There is no default user group that automatically includes all users in the AWS account. If you want to have a user group like that, you must create it and assign each 
   new user to it.

#### IAM roles


  






