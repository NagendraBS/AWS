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
    * User (identity) based policies -> users with permissions to access the AWS resources in their own account
    * Resource-based policies -> Resource-based policies are popular for granting cross-account access.
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

# IAM Identities (users, user groups, and roles)
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
  *Best practice for root accounts:
  * Don’t use the root user credentials.
  * Don’t share the root user credentials.
  * Create an IAM user and assign administrative permissions as required.
  * Enable MFA.

  #### IAM users
 <img width="1000" alt="image" src="https://github.com/user-attachments/assets/c1bd0b54-ae20-4f8d-b96b-9ae8d7afe9e1">

  
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

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/8af808cc-2a4b-4837-80f8-e0a99d7142d5">


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

<img width="800" alt="image" src="https://github.com/user-attachments/assets/9db9298d-000c-4cf4-8666-a8e035fe6e33">


* Roles are created and then “assumed” by trusted entities and define a set of permissions for making AWS service requests
* role is intended to be assumable by anyone who needs it. Also, a role does not have standard long-term credentials such as a password or access keys associated with it. * Instead, when you assume a role, it provides you with temporary security credentials for your role session.
* With IAM Roles you can delegate permissions to resources for users and services without using permanent credentials (e.g. user name and password).
* A role can be assigned to a federated user who signs in using an external identity provider.
* Roles can be assumed temporarily through the console or programmatically with the AWS CLI, Tools for Windows PowerShell, or API.

  Role Delegation:
* Create an IAM role with two policies:
* Permissions policy – grants the user of the role the required permissions on a resource.
* Trust policy – specifies the trusted accounts that are allowed to assume the role.
* Wildcards (*) cannot be specified as a principal.
* A permissions policy must also be attached to the user in the trusted account.

  ##  Federated users
  In AWS (Amazon Web Services), federated users refer to users who are authenticated by an external identity provider (IdP) and granted temporary access to AWS resources without needing to have IAM user accounts in the AWS account. This approach is particularly useful in scenarios where organizations want to allow their existing users (such as employees, partners, or customers) to access AWS resources using their existing credentials.

Here's how federated users work in AWS:

##### 1. **Identity Federation Basics**:
   - **External Identity Provider (IdP)**: This is an external service that manages user identities and authenticates users. Examples include Active Directory Federation Services (AD FS), Okta, Ping Identity, Google Workspace (formerly G Suite), or any SAML 2.0 or OpenID Connect (OIDC) compliant identity provider.

#####  2. **Authentication Process**:
   - **Assume Role API**: When a user from the external IdP wants to access AWS resources, they authenticate with the IdP using their credentials.
   - **Role-Based Access**: AWS IAM roles are preconfigured with permissions specifying what actions federated users can perform and what resources they can access within the AWS account.
   - **Temporary Security Credentials**: Upon successful authentication, the IdP issues temporary security credentials (an IAM role session) to the federated user.

#####  3. **Key Concepts and Components**:
   - **IAM Roles for Identity Providers**: These IAM roles are configured in the AWS account and establish a trust relationship with the external IdP. They define who can assume the role and the permissions associated with it.
   - **Identity Providers (IdP)**: External services that authenticate and manage user identities. They issue assertions (tokens) to AWS, which AWS validates to grant access.

#####  4. **Benefits of Federated Users**:
   - **Single Sign-On (SSO)**: Users can access both AWS and other applications using the same set of credentials, reducing the need for multiple login credentials.
   - **Centralized Management**: Identity and access management can be centralized in the external IdP, making it easier to manage user access across multiple systems.
   - **Security**: Federated users access AWS resources with temporary credentials, reducing the exposure of long-term credentials and improving security posture.

#####  5. **Use Cases**:
   - **Enterprise Applications**: Allow employees to access AWS resources using their corporate credentials managed by the enterprise IdP.
   - **Partner Access**: Grant access to AWS resources to users from partner organizations without requiring them to have AWS IAM user accounts.
   - **Customer Access**: Provide customers with access to specific AWS resources or applications using their existing credentials.

#####  6. **Implementation**:
   - **AWS Identity Federation**: Managed through AWS IAM, which supports various federation standards such as SAML 2.0 and OpenID Connect.
   - **Configuration**: Set up trust relationships between the AWS account and the external IdP, configure IAM roles for identity providers, and define permissions based on organizational policies.



## How  Federated users works  

<img width="500" alt="image" src="https://github.com/user-attachments/assets/abd8f915-bb58-4b1d-bd81-f5ab43483fa8">

AWS Identity and Access Management (IAM) is the service within AWS that helps you manage access to AWS services and resources securely. The AWS Management Console serves as a centralized place to manage IAM identities and access permissions.

When it comes to federated users, AWS supports identity federation, which allows you to grant temporary access to your AWS account to users authenticated through an external identity provider (IdP) such as Active Directory, Okta, or others that support Security Assertion Markup Language (SAML) 2.0 or OpenID Connect (OIDC). This process is facilitated through IAM roles.

Here's how AWS Identity and the federated user concept are linked:

1. **Identity Provider (IdP)**: The federated user is authenticated by an external identity provider (IdP) that supports SAML 2.0 or OIDC.

2. **Federation Process**: When a user attempts to access AWS resources via the AWS Management Console or programmatically using AWS API/CLI, they are redirected to the IdP's login page for authentication.

3. **Role Assertion**: Upon successful authentication, the IdP sends a SAML 2.0 assertion or OIDC token to AWS STS (Security Token Service).
                        AWS STS validates the SAML assertion or OIDC token against the configured trust relationship between the AWS account and the IdP. This trust 
                        relationship ensures that AWS can verify the authenticity of the federated user's identity and the assertions made by the IdP.

5. **IAM Role Creation**: In AWS IAM, you create IAM roles that define the permissions federated users will have when authenticated. These roles specify what the federated users can do and access within your AWS account.

6. **Temporary Credentials**: AWS STS validates the assertion/token and issues temporary security credentials (access key, secret key, session token) for the federated user based on the permissions defined in the IAM role.

7. **Access to AWS Resources**: Using these temporary credentials, federated users can then access AWS resources according to the permissions defined by the IAM role.

The AWS Identity Center (typically referred to as AWS Management Console for IAM) is where you manage IAM users, roles, groups, policies, and identity providers. It allows you to configure and administer federated access, roles, and permissions for federated users who authenticate via external IdPs.

In summary, the AWS Identity Center (IAM Management Console) is the central place to configure IAM roles and permissions, including those for federated users authenticated via external identity providers. It plays a crucial role in defining and managing access controls for users accessing AWS resources using federated identities.

---
---
# Access management for AWS

<img width="500" alt="image" src="https://github.com/user-attachments/assets/942eb5d9-de3a-490b-8d72-1305bab9edf8"> 



* AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources.
*  When a principal makes a request in AWS, the AWS enforcement code checks whether the principal is authenticated (signed in) and authorized (has permissions).
*  ``` You manage access in AWS by creating policies and attaching them to IAM identities or AWS resources.```
*  ``` Policies are JSON documents in AWS , when attached to an identity or resource, define their permissions. ```

 <img width="500" alt="image" src="https://github.com/user-attachments/assets/4d1dd49f-9309-4566-bbbb-740e13dfcf1f">

 * During authorization, the AWS enforcement code uses values from the request context to check for matching policies and determine whether to allow or deny the request.
 * AWS checks each policy that applies to the context of the request.
 * If a single policy denies the request, AWS denies the entire request and stops evaluating policies. This is called an explicit deny.
 *  Because requests are denied by default, IAM authorizes your request only if every part of your request is allowed by the applicable policies.
 *  The evaluation logic for a request within a single account follows these rules:
 *  By default, all requests are implicitly denied. (Alternatively, by default, the AWS account root user has full access.)
      - An explicit allow in an identity-based or resource-based policy overrides this default.
      - If a permissions boundary, Organizations SCP, or session policy is present, it might override the allow with an implicit deny.
      - An explicit deny in any policy overrides any allows.
 * After your request has been authenticated and authorized, AWS approves the request.
 * If you need to make a request in a different account, a policy in the other account must allow you to access the resource.
 *  In addition, the IAM entity that you use to make the request must have an identity-based policy that allows the request.

   ## Policy types
   ### Identity-based policies
  * Identity-based policies are JSON permissions policy documents that control what actions an identity (users, groups of users, and roles) can perform, on which 
    resources, and under what conditions.
  * Identity-based policies – Identity-based policies are attached to an IAM identity (user, group of users, or role) and grant permissions to IAM entities (users and 
     roles).  
  * Identity-based policies can be further categorized:
      * ``` AWS Managed policies```
         - Created and administered by AWS.
         - Managed policies that are created and managed by AWS.
         - Save you having to create policies yourself.
         - Can be attached to multiple users, groups, or roles within and across AWS accounts.
         - Cannot change the permissions assigned.
       
      * ```Customer managed policies```
          - Standalone policy that you create and administer in your own AWS account.
          - Can be attached to multiple users, groups, and roles – but only within your own account.
          - Can be created by copying an existing managed policy and then customizing it.
          - Recommended for use cases where the existing AWS Managed Policies don’t meet the needs of your environment
          - Customer managed policies provide more precise control over your policies than AWS managed policies.
       
       * ```Inline Policy```
            - Policies that you add directly to a single user, group, or role.
            - Inline policies maintain a strict one-to-one relationship between a policy and an identity.
            -  They are deleted when you delete the identity.
            -  When you delete the user, group, or role in which the inline policy is embedded, the policy will also be deleted.
            -  In most cases, AWS recommends using Managed Policies instead of inline policies.

     ### Resource-based policies

      * Resource-based policies are JSON policy documents that you attach to a resource such as an Amazon S3 bucket.
      *  These policies grant the specified principal permission to perform specific actions on that resource and defines under what conditions this applies.
      *  Resource-based policies are inline policies.
      *  There are no managed resource-based policies.
      *  ```Resource-based policies grant permissions to the principal (account, user, role, or federated user) specified as the principal.```
      *  To enable cross-account access, you can specify an entire account or IAM entities in another account as the principal in a resource-based policy.
      *  The IAM service supports only one type of resource-based policy called a role trust policy, which is attached to an IAM role.
      *  An IAM role is both an identity and a resource that supports resource-based policies.
      *   For that reason, you must attach both a trust policy and an identity-based policy to an IAM role.
      *   Trust policies define which principal entities (accounts, users, roles, and federated users) can assume the role.
   
    ### IAM permissions boundaries

      *  A permissions boundary is an advanced feature in which you set the maximum permissions that an identity-based policy can grant to an IAM entity.
      *  When you set a permissions boundary for an entity, the entity can perform only the actions that are allowed by both its identity-based policies and its 
          permissions boundaries
      *  Resource-based policies that specify the user or role as the principal are not limited by the permissions boundary.
      *   An explicit deny in any of these policies  overrides the allow.
      *   Identity-based policies grant permission to the entity, and permissions boundaries limit those permissions.
   
    ###  Service control policies (SCPs)
     *  AWS Organizations is a service for grouping and centrally managing the AWS accounts that your business owns.
     *   If you enable all features in an organization, then you can apply service control policies (SCPs) to any or all of your accounts.
     *  SCPs are JSON policies that specify the maximum permissions for an organization or organizational unit (OU).
     *  The SCP limits permissions for entities in member accounts, including each AWS account root user. An explicit deny in any of these policies overrides the allow
   
    ### Access control lists (ACLs)
      * Access control lists (ACLs) are service policies that allow you to control which principals in another account can access a resource.
      * ACLs cannot be used to control access for a principal within the same account.
      * ACLs are similar to resource-based policies, although they are the only policy type that does not use the JSON policy document format
      *  Amazon S3, AWS WAF, and Amazon VPC are examples of services that support ACLs.
   
    ### Session policies
      *  Session policies are advanced policies that you pass as a parameter when you programmatically create a temporary session for a role or federated user.
      *  The permissions for a session are the intersection of the identity-based policies for the IAM entity (user or role) used to create the session and the session p 
         policies.
      *   Permissions can also come from a resource-based policy. An explicit deny in any of these policies overrides the allow.
   


   ## JSON policy document structure
    * You can use the visual editor in the AWS Management Console to create and edit customer managed policies without ever using JSON.
    * However, if you use inline policies for groups or complex policies, you must still create and edit those policies in the JSON editor using the console.

   ### Examples of JSON policy syntax


    

     
         
    




  






