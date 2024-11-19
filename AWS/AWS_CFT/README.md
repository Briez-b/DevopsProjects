With AWS CFT we can create resources on AWS. It is IaC tool as terraform, but only for AWS.
To create CFT I can use **Json** or **Yaml**.

Let's talk about Iac. Iac tools should be **declaritive** and **versioned** in nature. What does that mean? 
**Versioned** means you can versioned the code, place it to s3 bucket or git repository and have a different versions of the code.
**Declaritive** means what you see is what you have. It means we defining in the script what we want the infrastracture to look like, rather than describing _how_ to achieve that state.

One of the great functions of CFT is **Drift detection**. With this function we can notice(just press drift detection button in console) what was changed in our infrastructure and take some action immediately. 


# PRACTICE

To write templates you can use official documentation. It is very well written and you can find there many examples.
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html

The example of the EC2 instance creation:

``` YAML
AWSTemplateFormatVersion: 2010-09-09
Description: A sample CloudFormation template with YAML comments.
# Resources section
Resources:
  MyEC2Instance: 
    Type: AWS::EC2::Instance
    Properties: 
      # Linux AMI
      ImageId: ami-1234567890abcdef0 
      InstanceType: t2.micro
      KeyName: MyKey
      BlockDeviceMappings:
        - DeviceName: /dev/sdm
          Ebs:
            VolumeType: io1
            Iops: 200
            DeleteOnTermination: false
            VolumeSize: 20
```

### Let's create some templates.

To create template and execute go to CloudFormation service and create stack. There are several oprions:

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241107123933.png)

For example I can choose "Build from infrastructure Composer"

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241107125409.png)

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241107125448.png)

If I want to add some properties, I can check what they can be in the sample template page for example. Everything can be found there or with chat gpt:

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241107125634.png)

So I added a bucket name to the s3 config:

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241107125950.png)

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241107130050.png)
![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241107130201.png)

And submit

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241107130324.png)

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241107130408.png)

Bucket created, and one additional bucket also created to store all templates.

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241107130510.png)

I deleted the bucket manually. Now I can use the drift option to see this change in CFT

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241107130818.png)

Now I can see that the resource was deleted:

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241107131013.png)

Create the stack again, but enable Versioning.

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241107132009.png)

If I disable it manually, with drift detection I can see this change and understand what exactly was changed.

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241107132251.png)
![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241107132316.png)

### I created a template with simple EC2 instance

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241107135919.png)

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241107135952.png)
