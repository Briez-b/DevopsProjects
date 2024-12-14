# Example of ECS cluster

### 1) Create ECS cluster:

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241212113903.png)

### 2) Create ECR repository to push the build to there:

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241212120245.png)

Login to it in cli to be able to push own images:

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241212121000.png)

Build and push the image:

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241212121855.png)

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241212122559.png)

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241212122626.png)


### 3) Create a task definition with this image (it is like yaml file for pods in kubernetes).

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241212131010.png)

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241212131030.png)

Now we have created task definition, so we can run it to execute our container.

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241212131145.png)


Choose the cluster we created before:

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241212131228.png)

Now we have container run in ECS cluster:

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241212131713.png)

I also added inbound rule to access the app using public IP of this task:


![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241212135648.png)

And now app accessible

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020241212135721.png)
