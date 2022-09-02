# AnsiblePlaybook

Automatisation d'un EC2 avec Ansible et AWS.<br><br>
Automation of a EC2 using Ansible and AWS. A good way to document my works with AWS cloud.<br><br>

Step 1 - 
Install necessary dependencies: <br>
$ sudo apt-get update <br>
$ sudo apt-get install python3-pip     <br>
$ sudo pip3 install boto boto3 ansible<br>
Step  2 -
Create Three EC2 instances => one Ansible mater (Ansible_Master) and two Ansible targets ( Ansible_Target1 & Ansible_Target2 ). <br>
![image](https://user-images.githubusercontent.com/103506746/188097036-e0bd4bea-6a27-4012-9d0b-fe2f33fa7d50.png)


In order to have my logs cleaner, I will use Termius. To install, create an account, and use the command
$ sudo snap install --classic termius-app <br>
If it doesn't work, check if snap is installed with
$ snap version <br>
If it still doesn't work, check if snapd is activated. It is a common issue. To activate is, use <br>
$ sudo systemctl start snapd.service 

Now, connect with termius to you Ansible_Master. The public IPv4 can be found in the instances details.

Once connected, 
$ sudo yum install ansible <br>
Won't work because it requires 
$ sudo amazon-linux-extras install ansible2 <br>
![image](https://user-images.githubusercontent.com/103506746/188098281-aca28540-cc4e-4b86-b9a6-f8516a195976.png)


