# AnsiblePlaybook

Automatisation d'un EC2 avec Ansible et AWS.<br><br>
Automation of a EC2 using Ansible and AWS. A good way to document my works with AWS cloud.<br><br>

# Step 1 - 
Install necessary dependencies: <br>
$ sudo apt-get update <br>
$ sudo apt-get install python3-pip     <br>
$ sudo pip3 install boto boto3 ansible<br> <br><br>
# Step  2 -
Create Three EC2 instances => one Ansible mater (Ansible_Master) and two Ansible targets ( Ansible_Target1 & Ansible_Target2 ). <br>
!!! Download and use the same key when you create your instance !!!


![image](https://user-images.githubusercontent.com/103506746/188097036-e0bd4bea-6a27-4012-9d0b-fe2f33fa7d50.png)


In order to have my logs cleaner, I will use Termius. To install, create an account, and use the command <br>
$ sudo snap install --classic termius-app <br>
If it doesn't work, check if snap is installed with<br>
$ snap version <br>
If it still doesn't work, check if snapd is activated. It is a common issue. To activate is, use <br>
$ sudo systemctl start snapd.service <br>
!!! If you have Kali Linux installed, there are high chances to get errors when you enter your command $ sudo snap run termius-app !!!<br>
Here is the solution:
![image](https://user-images.githubusercontent.com/103506746/188558460-8f43ba27-c331-460c-b2bb-58d6d16cfaa3.png)





Now, connect with termius to you Ansible_Master. The public IPv4 can be found in the instances details.<br>

Once connected, <br>
$ sudo yum install ansible <br>
Won't work because it requires 
$ sudo amazon-linux-extras install ansible2 <br>
![image](https://user-images.githubusercontent.com/103506746/188098281-aca28540-cc4e-4b86-b9a6-f8516a195976.png)


# Step 3

Our goal is to be able to connect to our targets ( Ansible_Target1 & Ansible_Target2 ) with our master (Ansible_Master).<br>
We need to install our key into our Ansible_Master <br>
![image](https://user-images.githubusercontent.com/103506746/188104875-d7b1e026-1ae1-49b3-9407-d36c3e79b3c2.png)

To do so, create the file with vim, and paste the key you obtained from AWS when you created your instances.<br>
!!Don't forget to change the authorisations of your key to be able to use it!!
![image](https://user-images.githubusercontent.com/103506746/188104314-6cdc13f8-c864-45af-87b3-df35c246e91e.png)<br><br><br>

Then, you need to copy your AWS key into the ssh file, so that the key automatically comes with the ssh connection.<br>
To do so, do<br>
![image](https://user-images.githubusercontent.com/103506746/188570576-85d05179-6ef5-4956-b0ff-a7709059f706.png)

<br><br><br>

With vim, create a file with ansible instructions as following: be precise with the syntax, because all instructions will be there.<br>
Take the IPv4 from your aws instances Ansible_Target1 and Ansible_Target2.
![image](https://user-images.githubusercontent.com/103506746/188566528-7d19346b-550d-4b68-8a7b-ba1cfda29984.png)<br><br><br>

Now you can see that the command works, but i still need to manually write instructions yes/no. <br>
We want to automate the whole process, so we don't want to write the instruction manually. <br>
We will change the settings of the file, so that the question doesn't appear.<br>
To open ansible settings:<br>
![image](https://user-images.githubusercontent.com/103506746/188571330-92aca4db-72c5-44ea-beee-9b727cc4ffb6.png)<br><br>
Then, take off the # in front of the line containing host_key_checking
![image](https://user-images.githubusercontent.com/103506746/188566993-39de226e-c090-4b42-9038-ab0c16387697.png)
<br><br><br>
We see that now, we aren't ask to confirm<br>
![image](https://user-images.githubusercontent.com/103506746/188571929-c7403da0-03c8-4057-ba9f-964b05af7dbf.png)<br><br><br>

Then, to be able to automate the two ( or more ) targets, let's create a group in our inventory.txt file. <br>
To create a group, do <br>
![image](https://user-images.githubusercontent.com/103506746/188567709-45b34961-3b02-4144-8b5f-967c5d37f73a.png)

<br><br><br>
Now, with the command to the group [ servers ], let's write the command.

# It Works! All of my servers obey me, my self-esteem increases.  What a great day! <3
![image](https://user-images.githubusercontent.com/103506746/188567620-97a8fcfe-ec57-4b54-9567-bbec6e982301.png)

