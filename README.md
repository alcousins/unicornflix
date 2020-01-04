<p align="center">
  <img src="https://www.amplify-video.com/unicornflix/logo.png" width="450">
</p>

Welcome to UnicornFlix. As the first developer here at UnicornFlix it's your mission to bring humanity closer to the unicorn kingdom by serving up premium videos to subscribers. You've been asked by the founders to develop a minimum-lovable-product to begin serving videos to users as soon as possible. They've also asked you to keep operational overhead at a minimum and to keep the API design flexible as the business model could pivot at any moment.

In this workshop we will build the video on demand streaming platform that allows you to upload, process, and serve videos to authenticated users.

The workshop is split into three primary sections with a collection of optional extensions:

![3 steps to UnicornFlix](https://www.amplify-video.com/unicornflix/steps.png)

**Backend Deployment with Amplify CLI** - Use the Amplify CLI to deploy the API, Authentication, and Video Streaming infrastructure.

**Web Client Admin View** - Build a web application to add videos and associate basic metadata.

**Web Client User View** - Stream videos to users who have signed into the service.

**Optional Extensions** - An optional section containing a collection of tutorials to extend the application functionality.

## Setting up Development Environment


### Option 1: Using a local development environment

You just started at UnicornFlix and they hooked you up with a brand new laptop - _sweeeet!_ Now let's configure your development environment. 

1. Clone the UnicornFlix workshop by running `git clone https://github.com/awslabs/UnicornFlix.git` or by downloading the zip [here](https://github.com/awslabs/unicornflix/archive/master.zip)
1. Download and install Node and Node Package Manager (NPM) if you don't already have it from [nodejs.org](https://nodejs.org/en/download/). Select **LTS** for the node version.
1. Install/update AWS Amplify CLI using this command `npm install -g @aws-amplify/cli`
1. Install Amplify Video, a custom AWS Amplify CLI plugin for creating our video resource, by running `npm install -g amplify-category-video`


### Option 2: Using a cloud based development environment with AWS Cloud9

1. From the Cloud9 Management Console, launch a new Environment. When prompted for settings, we suggest launching with a **t3.small** instance-type for this workshop. 
1. Connect to the Cloud9 IDE once it has launched. 
1. From the Terminal, clone the UnicornFlix workshop by running `git clone https://github.com/awslabs/UnicornFlix.git`
1. Install AWS Amplify CLI using this command `npm install -g @aws-amplify/cli`
1. Install Amplify Video, a custom AWS Amplify CLI plugin for creating our video resource, by running `npm install -g amplify-category-video`
1. By default, AWS Cloud9 manages AWS credentials for accessing AWS APIs via the CLI and SDKs. For this workshop, you will need to disable this feature and manually configure your AWS credentials. To disable managed temporary credentials:
    1. Click on the **AWS Cloud9** menu in the top left corner of the screen and select **Preferences**
    1. Click on **AWS Settings** from the list of preference categories on the left
    1. Use the toggle to disable **AWS Managed Temporary Credentials** 


## Configure Access Credentials

The Amplify framework, used in this workshop, will provision resources in your AWS account to support the features you enable in the project. In order to create and configure these resources, the Amplify CLI requires an IAM User or Role to be able to call the relevant service APIs. 

### Event Engine

If you are running this workshop at an AWS event and are using Event Engine to access an AWS account:

<details>
    <summary>Click here to expand instructions</summary>

1. Obtain your hash from the event lead and visit https://dashboard.eventengine.run/login
1. Login in using your hash and click on the use console button
1. A popover will appear with your AWS console access federation link and AWS CLI profile links
1. In a terminal (either on your laptop or in Cloud9, depending on how you are deploying the workshop) run the command `aws --profile ee configure`
1. Copy and paste the Access Key and Secret Access Key values from the Event Engine popover into the terminal when prompted. 
1. Set the default region to the region you are deploying this workshop in to.
1. Leave the default output format as default.
1. Open up your AWS profile folder on your computer ( `~/.aws/` for Mac and Linux and `C:\Users\USERNAME \.aws\` for windows)
1. Edit the `credentials` file in this folder, adding in the **aws_session_token** field to the ee profile, like so (copying the values from the popover in event engine). Please note that the credentials file is all lowercase (in Event Engine it is uppercase).
    ```
    [ee]
    aws_access_key_id = XXXXXXXXXXXXXXXX
    aws_secret_access_key = XXXXXXXXXXXXXXXXXXXXXXXXX
    aws_session_token = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
    ```
1. Edit your `config` file by adding default values (changing your region to the assigned region of your event)
    ```
    [ee]
    region = us-west-2
    output = json
    ```
1. When running `amplify init` choose the newly created profile called `ee` (**Note:** please don't select default)
</details>

### Running in your own AWS Account

If you are running this workshop in your own AWS account:

<details>
    <summary>Click here to expand instructions</summary>

1. To operate this workshop, you will need an IAM User with access to the base services supported by Amplify. A sample policy is included here: https://aws-amplify.github.io/docs/cli-toolchain/usage#iam-policy-for-the-cli .
In addition to these services, the Amplify Video VOD component also uses **AWS Elemental MediaConvert**. To add support for this service, attach the IAM Managed Policy **AWSElementalMediaConvertFullAccess to your IAM User, along with the above policy for the base Amplify functionality. 
1. Once you have created an IAM User for use in the workshop, open a terminal (either on your laptop or in Cloud9, depending on how you are deploying the workshop) and run the command `aws --profile ee configure`
1. Enter the Access Key and Secret Access Key for the IAM User you just created
1. Set the default region to the region you are deploying the UnicornFlix environment into
1. Leave the default output format to the default value


</details>





[Click Here to begin implementing the back end!](./documentation/Backend.md)
