## Steps to install Ansible on Master Server and ping Target Servers

1. SSH to master server
2. Install ansible 

> sudo apt-get ansible install

3. Copy private key to user folder

![image](https://user-images.githubusercontent.com/12914385/110407632-ccb03500-8049-11eb-88b8-9aff9e818d28.png)

4. Add identity to ping target servers

![image](https://user-images.githubusercontent.com/12914385/110407856-41836f00-804a-11eb-84a3-d1aa48e891cb.png)

5. Create inventory file with target servers

![image](https://user-images.githubusercontent.com/12914385/110407943-67a90f00-804a-11eb-9b78-d5377072d21e.png)

6. Host Key Checking is set to false in ansible config file

> sudo vim /etc/ansible/ansible.cfg

![image](https://user-images.githubusercontent.com/12914385/110408116-af2f9b00-804a-11eb-9f40-dc1d942a5a19.png)

7. Ping servers using individual target server or group name

![image](https://user-images.githubusercontent.com/12914385/110408035-8e674580-804a-11eb-989c-4bda972bfba4.png)
