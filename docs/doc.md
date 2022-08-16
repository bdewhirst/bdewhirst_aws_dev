# AWS2022

## 2022-08-03

### Getting started with AWS in earnest

[This page](https://aws.amazon.com/ec2/getting-started/) lists three steps:

1. Log into AWS
2. Launch Instance
3. Configure Instance.

Logging in:

* [Link ](https://console.aws.amazon.com/)to AWS Mgmt console

First time:

* Click “create a new AWS account”
* Tried my email as username and AWS account name, which is acceptable
* (check email for verification code)
    * Check all mail in case it was filtered out of the inbox
* Provide verification code, strong password
* Indicate business or personal (personal), provide identifying info
* Optional: review [AWS agreement](https://aws.amazon.com/agreement/)
* Agree to AWS agreement
* Provide credit card info (they have a free tier)
* Prove you’re a human, prove you own a cellphone
* Select tier (free)
    * One year?
* Sign in using user and password created above
* (get some emails with some links which may be helpful
* Adjust settings (_e.g._, region) as needed

[AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1#) <strong>← important</strong>

### EC2 Instances

* [Documentation ](https://aws.amazon.com/ec2/instance-types/)on different instance types
    * They recommend “T2.micro” when just getting started

#### Setup:

1. Open [AWS EC2 Dashboard](https://us-east-1.console.aws.amazon.com/ec2/v2/home?region=us-east-1&skipRegion=true#)
2. Click “launch instance”
3. Enter a name
    1. (subsequently deleted)
    2. Select OS, etc.
4. Create a key pair
    3. Give it a name
    4. Select encryption type
        1. Probably a good idea to create a RSA *.pem key
        2. Name: (subsequently deleted)
5. Create a security group under “Network Settings”
    5. ~~Restrict IP to “my IP”~~
    6. (this was why I can’t connect using the suggested web client)
6. Click “launch instance” (bottom) \
 \
(using the provided link, I created a billing alert)

#### “Get In”

1. Open [EC2 Instance Connect](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-connect-methods.html#ec2-instance-connect-connecting-console) web client
    1. This directs you to open [this link to the ec2 dashboard](https://console.aws.amazon.com/ec2/)
2. Select instance
3. Click “connect”
4. Use default user suggested
5. (if you get an error, debug– note that the IP of one’s machine and that of the web client are not the same)

#### Using Putty to Get In

1. Open EC2 dashboard
2. Click on instance
3. Note public IP address

(wasn’t able to get this to work, but [documentation ](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-connect-methods.html#ec2-instance-connect-connecting-console)further down may be able to help)

#### Finally

**Don’t forget to terminate instance** to avoid charges

	Select the EC2 instance, choose "Actions", select "Instance State", and "Terminate".

## 2022-08-12

### From AWS email from Aug. 9

(I’ve since checked these out– see further below)

1. [Setup your account and environment](https://aws.amazon.com/getting-started/guides/setup-environment/)
2. [Install and learn the AWS CDK (cloud development kit)](https://aws.amazon.com/getting-started/guides/setup-cdk/)
3. [Browse tools by programming language](https://aws.amazon.com/developer/tools/)

Plus, with a few hours you can… 

* Compute	 	[Launch A Linux Virtual Machine](https://aws.amazon.com/getting-started/hands-on/launch-a-virtual-machine/)
* Databases	 	[Create Your First Purpose-Built Database](https://aws.amazon.com/products/databases/learn/)
* Mobile	 	[Deploy And Host A ReactJS App](https://aws.amazon.com/getting-started/hands-on/build-react-app-amplify-graphql/)
* Machine Learning	 	[Build, Train, And Deploy A Machine Learning Model](https://aws.amazon.com/getting-started/hands-on/build-train-deploy-machine-learning-model-sagemaker/)
* Storage	 	[Store And Retrieve A File](https://aws.amazon.com/getting-started/hands-on/backup-files-to-amazon-s3/)
* Serverless	 	[Run A Serverless "Hello, World!"](https://aws.amazon.com/getting-started/hands-on/run-serverless-code/)
* Containers	 	[Build And Run A Containerized Web Application](https://www.apprunnerworkshop.com/)
* Budget Alerts	 	[View Guidance For Setting Up Budget Alerts](https://aws.amazon.com/getting-started/hands-on/control-your-costs-free-tier-budgets/)

Per the above:

(starting from “browse tools by programming language → with IDE (pycharm))

“Integrated experience for developing serverless applications…”

### AWS + PyCharm

#### Installation

→ [install the toolkit](https://docs.aws.amazon.com/toolkit-for-jetbrains/latest/userguide/setup-toolkit.html)

1. Create an AWS account (should already be done)
2. They strongly encourage [creating a “special” IAM admin account](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html#getting-started_create-admin-group-console) for use with JetBrains stuff \
 \
_n.b_. “[AWS IAM dashboard](https://us-east-1.console.aws.amazon.com/iamv2/home#/home)” is a thing \
 \
A. click email in upper right \
B, C. find “IAM User and Role Access…” and click “edit” and check “activate iam access”, click “update” button \
D. click “service” (upper left) > IAM to return to the IAM dashboard \

3. Users (left hand side menu, near top) > Add User
    1. Username: Administrator
    2. Check the box for “custom password” and set one. Optionally, un-check “user must reset password…” (etc.) Reference: the “secrets” folder which is local-only in this repo
    3. Click “next: permissions”
4. On the permissions page:
    1. Select “add user to group”
    5. Click ‘create group’
    6. Name it “Administrators”
    7. Check the box for “AdministratorAccess”
    8. Click “create group” (button in lower right)
    9. Click “refresh” (on the earlier screen)
    10. Click “next: tags”
5. Optional– add info (like email)
6. Click “next: review” button
7. Review info, then click “create user”
8. Optionally, you can click a CSV with login info, or email them \
(although the csv has a _field_ for access key, it is blank by default \
(relevant if we’re using this to provision credentials for employees w/i a firm using AWS) \
[This link](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html#getting-started_create-admin-group-console) has add’l resources for access management– search for “complete” \
 \
(there is also a way to do this using the AWS CLI, which is also at the link immediately above) \

9. [Create an access key](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html#Using_CreateAccessKey) for the Administrator account created above
   1. Basically, on the IAM dashboard, click on the username ‘administrator’, click on security credentials, download the csv, etc.

This completes the “AWS Credentials” section of setup



1. Start PyCharm (or another JetBrains IDE)
2. Go to Settings > Plugins
3. Click “marketplace” (defaults to ‘installed’, I think) and enter “AWS Toolkit”
4. Click “install”
5. If/When it asks, accept the 3rd party plugins privacy note
6. Choose “restart IDE” when prompted
7. Install the following in the following order:
    1. [AWS command line interface](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)
    2. [Docker](https://docs.docker.com/install/)
    3. [AWS Serverless application model CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install.html) \
 \
(follow the relevant instructions at each link)
8. [Connect to an AWS account for the first time](https://docs.aws.amazon.com/toolkit-for-jetbrains/latest/userguide/key-tasks.html#key-tasks-first-connect) \
(follow those instructions– but basically, edit a config file with info from the access key generated earlier)

Note: this stuff needs docker running to work

This results in something like the following: \

# ADD IMAGE LINK HERE
<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

(I need add’l info before I can test this)

… I may have some sort of permissions issue (see below-- resolved)

That concludes installation (though I may need to do some debugging of the later steps)


#### Getting started with AWS Toolkit for PyCharm

[Ref](https://docs.aws.amazon.com/toolkit-for-jetbrains/latest/userguide/welcome.html)

Note: I was able to see the S3 object I created in the following section, so this appears to be working well


### Getting started with S3

[ref](https://aws.amazon.com/getting-started/hands-on/backup-files-to-amazon-s3/)

This is pretty simple

* Successfully created a bucket (they need to have **globally** unique names, and there are character restrictions)
* Successfully added a small file
* Successfully saw that bucket and file in PyCharm (per the above AWS IDE plug-in installation)
* Deleted the file and bucket once I was done \
 \
Note: like everything else, this can be done from the CLI

## 2022-08-13

Working on “[Install and learn the AWS CDK (cloud development kit)](https://aws.amazon.com/getting-started/guides/setup-cdk/)

* Confirmed AWS CLI was set up correctly (works in cmd.exe, powershell, pycharm terminal)
* “AWS CDK” – cloud development kit
* NPM – “node package manager”-- not AWS specific

~~The “npm” command is meant to be run in ec2 (or similar)~~

To install npm for windows:

1. [Download the windows installer for Node.js](https://nodejs.org/en/download/) (which brings npm)
2. Run it
3. Accept the terms
4. I opted to allow it to automatically install “other stuff” it needs
5. Otherwise, click next until it is done

Note: the “auto” step installs Chocolatey, which is a general package manager for windows

“npm --version” works as expected, so installation appears to have been successful

6. Run “npm install -g -aws-cdk” in cmd.exe
    1. Initially threw an error, possibly because stuff is still installing \
(nope, that wasn’t it)
    2. Not documented on AWS: \
Run ‘npm init’, click enter a bunch
    3. Re-run the -aws-cdk command above
7. To verify, run cdk --version
    4. After fixing the windows PATH variable to add python and move it up the list, and after retrying a few times, it works as expected


#### Bootstrapping your AWS Account

From getting started, module 2:

    Many AWS CDK stacks that you will deploy, will include assets, external files that are deployed with the stack, 
    such as AWS Lambda functions or Docker images. The CDK uploads these to an Amazon S3 bucket or other containers 
    so they are available to AWS CloudFormation during deployment. Deployment requires that these containers already 
    exist in the AWS account and the region you are deploying into. Creating these containers is called **bootstrapping**.

8. Get the account id by running <code>`aws sts get-caller-identity`</code> <strong>← useful!!!</strong>
9. Bootstrap the account by running `cdk bootstrap aws://ACCOUNT-NUMBER/REGION`
    1. <em>i.e</em>., replace acct# from the previous step and region from the aws console (for example)
    2. For me, this hits a permissions error (related to script permissions and npm) 
    3. [Web-suggested solution](https://www.c-sharpcorner.com/article/how-to-fix-ps1-can-not-be-loaded-because-running-scripts-is-disabled-on-this-sys/):
- In powershell run `set-ExecutionPolicy RemoteSigned -Scope CurrentUser `
- accept 
- try the command again
    1. (this worked)


### Module 3: Create Your First AWS CDK Project

I followed the Instructions [from here](https://aws.amazon.com/getting-started/guides/setup-cdk/module-three/)

(I’ll make a note if anything goes wrong, or if I deviate from the instructions)

* Changed working directory to …\bdewhirst_aws_dev
* _n.b._ The above link does a good job of explaining the file structure it creates
* VPC = “virtual private cloud”
* *.ts files are “transport stream” files (however, this is also an unrelated video format) \
Late in the process, this threw an error. This may be due to version differences/incompatibilities. [This link](https://bobbyhadz.com/blog/aws-cdk-not-assignable-to-type-construct) may have more relevant info (if I need this for something later).
    * Hypothesis: I installed a later version of _something_ than the guide expects. As a demonstration of the _concept_, though, I got what I needed.
    * [Hints towards debugging this?](https://stackoverflow.com/questions/73034493/what-to-do-when-cdk-bootstrap-does-not-work)

#### Fixing Powershell *.ps1 permissions issues

See [this link](https://www.c-sharpcorner.com/article/how-to-fix-ps1-can-not-be-loaded-because-running-scripts-is-disabled-on-this-sys/)

TLDR, run “Get-ExecutionPolicy -list” in powershell

(restart PyCharm if relevant– it’s terminal functionality _does_ leverage powershell on Windows.)

## 2022-08-15

(see list of tutorials from Friday (Aug. 12).

### Compute

“Launch a linux VM with lightsail”

(looks to have more horsepower than EC2, but at higher cost) (Nope! See below.)

(note– this looks like EC2, though, so it may be accessible from that starting point as well– see below)

EC2– high performance computing

Lightsail– lighter weight stuff. (host a webpage, have a wiki or other content management service (CMS), etc.

1. [Go to lightsail](https://lightsail.aws.amazon.com/ls/webapp/home/instances)
2. Click “create instance”
3. Select
    1.  region (if the default isn’t what you want)
    2. OS (linux/Unix) 
- FWIW: Amazon has their own “flavor” of linux, and there are others supported
    3. OS only, choose OS 
- since the demo uses Amazon Linux (one), I will go with that for purposes of the demo working as expected \
- if this was for something else, Amazon Linux 2 or Ubuntu would probably be  good starting points
4. (see several optional options from the demo link in step 1)
5. Click the hamburger (vertical ellipsis) -> Connect \
Or click the orange terminal-shaped icon
6. (do whatever your use case calls for– there are also ‘best practice’ suggestions in the above doc link
7. To get rid of it, hamburger -> Delete -> (confirm)

### Mobile

Create JavaScript UI thing– see 2022-08-12 for link

**(I skipped this one)**

## Create Database

* [link to several options w/ tutorials](https://aws.amazon.com/products/databases/learn/)

Options include (but probably aren’t limited to):

* Amazon RDS database (Relational Database Service– PostgreSQL)
* Amazon Aurora (their thing, with MySQL compatibility)
* DynamoDB (NoSQL)
* ElastiCache cluster (real time, caching, in-memory data store)

I selected the [Amazon RDS](https://aws.amazon.com/getting-started/hands-on/create-connect-postgresql-db/) tutorial

1. Open the AWS management console
2. Find and open RDS (e.g., thru the searchbar)
3. Change region if desired
4. Click “create database”
5. Choose engine (here, PostgreSQL)
6. Choose template (here: free tier eligible)
7. Under settings, select DB name, master username, password, etc
    1. They recommend enabling storage autoscaling when workload is cyclical or unpredictable
8. If you need EC2 (etc.) to be able to access it, select “publicly accessible / Yes”
9. For demo, “create new” VPC security group, and appropriate zone \
(See the above link for more documentation of fields/settings) \
 \
Documentation includes additional information on connecting to the database, but as I’d connect via python (typically), I’m not replicating those steps here. \
 \
Note: “view credential details” shows the username and password created earlier \
 \
[Link to more information](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_CommonTasks.Connect.html) on connecting to AWS databases
10. To delete, select the database in the dashboard and go to Actions > Delete

### Serverless computing

[Run a serverless “hello world”](https://aws.amazon.com/getting-started/hands-on/run-serverless-code/)

1. AWS Management Console > search and open Lambda
2. Click “create a function”
3. Click “use a blueprint”
4. Search for “hello-world-python” and select **the radio button** then click Configure
5. Under basic information:
    1. Name: hello-world-python
    2. Create new role from template
    3. Role name: lambda_basic_execution
6. Click “Create function” \
(review various settings as needed)
7. Click “test” -> “configure test event”
8. Provide event name (_e.g._ HelloWorldEvent), etc.
9. Select “test” \
(see that it says “hello, world!” in the console) \
(note that it monitors metrics, like duration, billed duration, memory used, etc.) \
 \
“You pay for what you use”
10. Go to Lambda > Functions > 
    4. select hello-world-python
    5. Under Actions, select Delete

General idea: “Run some python without thinking about servers”

### Containers

[Build and run a containerized web app](https://www.apprunnerworkshop.com/)

(sidenote: I plugged this tutorial in LinkedIn)

“AWS App Runner” is a new service

(a version of these instructions is used as part of a workshop, but there are also “solo” instructions)

1. Follow instructions for creating a suitably-credentialed user
2. AWS management console > cloud9 (**not** as root)
3. Click “create environment”
    1. Name: apprunnerworkshop
    2. On next screen, select “t3.small” (otherwise leave defaults as-is)
4. On next screen, click “create environment”
5. Close the welcome tab
6. Click green “plus” icon > New Terminal
7. Close the lower terminal
8. Run the indicated code to increase the allocated ec2 space on this Cloud9 instance
    3. Note that the last line is “sudo reboot”, which is necessary to take advantage of the increased memory
9. As indicated, use the “deep link” to IAM to set up another admin user in EC2
    4. (this is to let EC2 call services on my behalf)
10. **Back in the window with the EC2 terminal** click the gray circle in the upper right and select “Manage EC2 Instance
11. Select instance, then select Actions > Security > Modify IAM Role \
(if it is grayed out, make sure an instance was selected)
12. Choose “apprunnerworkshop-admin” from the dropdown and click “update IAM role”

… that completes “setup” (I think)

#### Getting started with AWS APPRUNNER

(See top link of this section for details on what we’re doing– I’ll note gotchas and any changes from screenshots that I notice. If trying to “hop into” this step for something else, look for “Runner > Creating a AWS App Runner Service”

* To create a custom policy with the copy-paste JSON, one needs to click the “other” tab (JSON, not Visual editor) \

* Don’t forget to click “deploy”, especially if it doesn’t seem to be working
* The ‘auto update’ of template/repo.html is visible at the link on default domain, but the ‘default domain’ page \

* All the commands that assume we have a folder called “environment” should be run in the cloud terminal from the beginning of the exercise

### Machine Learning

[Build, Train, and Deploy a ML model with Sagemaker](https://aws.amazon.com/getting-started/hands-on/build-train-deploy-machine-learning-model-sagemaker/)

(My notes here will be brief, though I’ll note any issues or observations– see the above link for more complete documentation.)

1. Sign into [SageMaker Console](https://us-east-1.console.aws.amazon.com/sagemaker/home?region=us-east-1#/)
2. Notebook > Notebook Instances > Create notebook instance
3. IAM Role > New role > Create an IAM role, Any S3 bucket > Create role
4. Once it starts, select ‘open Jupyter’
5. In Jupyter: New, conda_python3
6. (paste code, follow the steps in above-linked documentation, etc.-- standard stuff, using AWS-flavored tools)

(I printed a PDF of the notebook after it finished)

7. Clean up– release s3 resources, delete notebook, delete S3 bucket, etc.