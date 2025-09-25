#After creating the VM.
#ssh into VM.
```
sudo adduser opsadmin
```
#Creates a new user named opsadmin. You’ll be prompted to set a password and optionally fill in details (e.g., full name, phone). This user starts with a home directory (/home/opsadmin) and basic shell access.
```
sudo usermod -aG sudo opsadmin
```
#Adds opsadmin to the sudo group, granting administrative privileges to run commands with superuser rights using sudo.
##Purpose: Establishes a dedicated administrative user to replace the default ubuntu user, enhancing security by moving away from a well-known account.
#STEP-2
#Imagine this scenario
You have a locker (the VM) far away.
Normally, you need a password to open it. But passwords can be guessed by hackers.
Instead, you can use a special key that only you have.
This key is on your computer.
You give a copy of your key to the locker (VM).
Now, whenever you visit the locker, it recognizes your key and opens without needing a password.
1.Check if you have a key
Your computer usually keeps keys in:
```
~/.ssh/id_rsa.pub
```
#If you don’t have it, create it with:
```
ssh-keygen -t rsa -b 4096
```
#Press Enter for everything, no password needed (simple for now).
#Copy the key to the VM
Use this command:
```
ssh-copy-id -i ~/.ssh/id_rsa.pub opsadmin@<VM_PUBLIC_IP>
```
#Example:
```
ssh-copy-id -i ~/.ssh/id_rsa.pub opsadmin@203.0.113.10
```
#It will ask the opsadmin password once.
This copies your key to the VM’s “locker list” (~/.ssh/authorized_keys).

#Log in without a password
Now try:
```
ssh -i ~/.ssh/id_rsa opsadmin@<VM_PUBLIC_IP>
```
#If done right, you enter the VM automatically without typing a password.
