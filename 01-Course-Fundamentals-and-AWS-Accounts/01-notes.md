### 1.1 Course Fundamentals & AWS Accounts
![accounts](https://github.com/xPuffball/AWS-SAA-NOTES/blob/main/01-Course-Fundamentals-and-AWS-Accounts/01-visual-aids/VA-aws-accounts.JPG)
#### 1.1.1 Creating an AWS Account
An AWS account is a container for identities (users, roles) and resources.

When creating an AWS, you need:
- A unique email address
- A credit card/payment method

The email used for registration is used to create a special type of identity within the account, known as the **ACCOUNT ROOT USER**.

This root user has full control over the AWS account and all resources created within it - it also **CANNOT** be restricted. 

When services consume resources, a bill is sent to the Account Payment Method (credit card) as they are consumed, as AWS is a pay-as-you-go system.

#### 1.1.2 The IAM
IAM, or Identity & Access Management, can be used to create *users*, *groups* and *roles* and give them FULL or LIMITED permissions. 

#### 1.1.3 Separating AWS Accounts & Why That's a Good Thing
AWS cccounts can contain the impacts of admin errors or exploits - by using separate accounts for separate things (DEV, TEST, PROD) or separating AWS accounts for different teams/products, the impact of a bad actor or mistake can be minimized to a single account. 

Since AWS is good at containing these events within a single account, you probably shouldn't run your business on a single account - just in case something goes horribly wrong. 

By default, access to an AWS account is denied except for the Account Root User (but external identities can be granted access)

#### 1.1.4 Creating AWS Accounts
After creating an AWS account: 
- secure the account with **Multi-Factor Authentication (MFA)**
- create billing alarms in case of financial emergencies ([don't spend 700 USD on a cloud service by accident](https://nwong.xyz/))
- generally avoid using the Account Root User - it's unrestricted and there's only one per account therefore NOT SAFE!!!
    - the best practice is to create IAM identities inside the AWS Account with administrative access(IAMADMIN)

#### A Cool Gmail Trick (kind of related?)
AWS accounts need *unique* email addresses to be initialized - this means that while payment methods can be reused between AWS accounts, email accounts can't be - so to get around the hassle of making a new email for every account, you can simply:
- add a "+" sign after your email username (e.g. j4emin.han@gmail.com => j4emin.han+AWSStudy1@gmail.com)
- theoretically, this lets you create *infinite* gmail accounts for your AWS account needs!

#### 1.1.5 Multi-Factor Authentication & Securing your Account
![security](https://github.com/xPuffball/AWS-SAA-NOTES/blob/main/01-Course-Fundamentals-and-AWS-Accounts/01-visual-aids/VA-securing-account.JPG)
If your username & password are leaked, anyone can be you!
Factors are different pieces of evidence which prove... well, the fact that you are indeed you. Factors can be divided into 4 categories of evidence:
- Knowledge - Something you know (e.g. username, password, your mother's second cousin's pet's brother's middle name)
- Posession - Something you have (e.g. your phone, a MFA device)
- Inherent - Something you are (e.g. your fingerprint, retinal scan)
- Location - Somewhere you are (e.g. coordinates, access points in certain locations only')

AWS' MFA kinda works like:
aws => key, info => QR Code => Scan QR Code => MFA Application => Generated, shifting code

#### 1.1.6 The Billing Alert
To monitor your spending on AWS and to make sure not to go over a certain billing limit, set a billing alarm in the event you leave a service on overnight by accident or something. 
***Setting it up***
1. Enable Billing Alarms in Settings
2. Cloudwatch
3. All Alarms
4. Create Alarm
5. Select Metric
6. Set Billing Limit
7. Create SNS Topic for Billing
8. Set Alarm
