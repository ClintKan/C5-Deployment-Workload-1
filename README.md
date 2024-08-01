**_WORKLOAD 1 DOCUMENTATION_**

**OBJECTIVE/PURPOSE**

This is a workload/assignment to put into practice the use of Git in Ubuntu (Linux) and GitHub and how to use them both in the CI/CD pipeline deployment of a webapp located via Jenkins’ build stage.


**SYSTEM DESIGN DIAGRAM**


<img width="540" alt="image" src="https://github.com/user-attachments/assets/9c43e9ef-308c-40e0-8bd0-99a030f8cc72">


 

**STEPS**

_Step 1_
-	Cloning - This is to download the repo from GitHub to the local machine’s directory.
<img width="445" alt="image" src="https://github.com/user-attachments/assets/79a44367-01bc-4f19-bdcf-13ea9ce0c298">

 
This step helps create a local copy of the files hosted in github for easy manipulation.
 

_Step 2_
-	Removing the “.git” folder prior to uploading the folder to GitHub since the said folder holds the owner’s rights and account details to the application files. So by removing it, it strips the ownership issues when time for uploading arrives.
<img width="540" alt="image" src="https://github.com/user-attachments/assets/9095033e-abdc-4524-b565-14ce18c8010f">

 

_Step 3_
-	Navigated into the directory downloaded and then initialized git.
-	Made first commit of the files locally for proper documentation about the changes made on the app files.
 <img width="540" alt="image" src="https://github.com/user-attachments/assets/f9674b2d-ea8f-4664-9e4d-e930c44c0811">


-	Attempting to push the local commits to personal GitHub
<img width="540" alt="image" src="https://github.com/user-attachments/assets/24fb5af2-77d1-4962-a41a-401353c3db5e">
 


-	Failed due to wrong password – used GitHub password. Used the GitHub token. See screenshot below…
 <img width="335" alt="image" src="https://github.com/user-attachments/assets/441913e4-8e0d-42e1-b63d-05c41f342020">

_Step 4_
-	Creating an EC2 – as per the instructions. EC2 Name = “ProjectCKC5”
<img width="540" alt="image" src="https://github.com/user-attachments/assets/20e6626b-cab3-4290-abf4-a80ec8ff46f4">

 



_Step 5_
-	Installing Jenkins on to EC2 successfully – hence “Service Running”.
 <img width="540" alt="image" src="https://github.com/user-attachments/assets/74bebbe6-cd32-4b09-a890-ea1f6de2be3f">



_Step 6_
-	Logged into Jenkins using an internet browser via the public IP address of the Jenkins EC2.
-	Using the initial admin password, filled in the user/developer’s details/names.
-	Then, created the first admin account that would be used to log into the Jenkins web UI and then configure both the initial repo server and the Jenkins server. 


_Step 7_
-	This about the creation of the pipeline. The pipeline is setup between the EC2 and the initial repo server so as to push/upload updates made to the account (in this case mine).
-	Configuring of the pipeline in Jenkins in preparation for step #6
-	It was successfully linked…but without a “Stage View”
<img width="299" alt="image" src="https://github.com/user-attachments/assets/cdd86314-68bc-4bfc-bf88-27c657bb3389">

 


Note: To have the “Stage View” you need to add the Stage View Plug-In.
<img width="540" alt="image" src="https://github.com/user-attachments/assets/55841e3d-7259-46c0-88d0-08de567564ab">

 

_Step 8_
-	This is about creating AWS Elastic BeanStalk instance and environment.
 <img width="540" alt="image" src="https://github.com/user-attachments/assets/886a87fa-6ae4-4b79-90bc-01b5a3e5d8c5">



-	Upon following the instructions here, I ran into the following issue when completing the configuration of the AWS Elastic BeanStalk.
<img width="540" alt="image" src="https://github.com/user-attachments/assets/e3405dc9-caae-41b1-aad1-ab4f995b5e3c">

 

-	The solution to the above issue was to uncheck the Managed Updates – that was activated by default.
 <img width="484" alt="image" src="https://github.com/user-attachments/assets/9830b452-596a-441f-9cf7-c9a6cdca6d3c">


-	The screenshots below are the “Review page” of the AWS Beanstalk Configuration

<img width="443" alt="image" src="https://github.com/user-attachments/assets/128b6134-68fa-4cab-941f-3d189f21ade9">




<img width="432" alt="image" src="https://github.com/user-attachments/assets/904b3ea0-6ffd-4a87-b380-c63462692438">



 
<img width="382" alt="image" src="https://github.com/user-attachments/assets/356b9e99-0d49-4b2c-94d8-46419c685548">



 
<img width="454" alt="image" src="https://github.com/user-attachments/assets/27d02a9c-27b0-4b2e-969d-05f9b39913f8">

 


_Step 9_

-	Upon deployment in Step 7 of the WebApp, AWS BeanStalk environment provided that the WebApp was accessible via the link below; 
http://wd1c5ckapp-env.eba-beihhqp8.us-east-1.elasticbeanstalk.com/dashboard

Unfortunately, the WebApp was not accessible via the above link – despite the attempts to recreate the AWS BeanStalk environment/EC2.
<img width="540" alt="image" src="https://github.com/user-attachments/assets/f3e17380-dbaf-4769-bc52-e2d2f0d5268b">

 

-	Upon research and consultation, the issue was down to line 16 – that was written as application = Flask(__name__). But when corrected to as the screenshot below, it fixed the WebApp.
 <img width="540" alt="image" src="https://github.com/user-attachments/assets/39d0b162-4403-48f1-98b1-d62a5410ed06">

 <img width="540" alt="image" src="https://github.com/user-attachments/assets/b197f1cb-2f0b-4ce6-8329-07ecab71d1f2">

 

-	Below is the WebApp upon fixing the issue.
 <img width="453" alt="image" src="https://github.com/user-attachments/assets/360cbb84-cad2-4436-baa4-40d54759d070">


**_CONLCUSION_**

While the WebApp was successfully deployed in a partially automated way, the whole CI/CD process can be fully automated. Additionally, the how-to step-by-step documentation can be a bit clearer – spelling out the configurations that have to be done in AWS Elastic BeanStalk environment.
