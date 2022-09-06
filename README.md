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
To do so, create the file with vim, and paste the key you obtained from AWS when you created your instances.<br>
!!Don't forget to change the authorisations of your key to be able to use it!!
![image](https://user-images.githubusercontent.com/103506746/188104314-6cdc13f8-c864-45af-87b3-df35c246e91e.png)
![image](https://user-images.githubusercontent.com/103506746/188104875-d7b1e026-1ae1-49b3-9407-d36c3e79b3c2.png)

