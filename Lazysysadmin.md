<h1 align="center"> LazySysAdmin </h1>

## nmap scanning 

<img width="979" height="345" alt="Screenshot 2026-03-13 at 20 19 17" src="https://github.com/user-attachments/assets/32f8679a-2510-4a0f-97b7-56ca0431b3d6" />

## port 80 

<img width="2940" height="1912" alt="image" src="https://github.com/user-attachments/assets/d3f09a09-c662-48f9-ac3f-44c3d0343df4" />

dirsearch implementation 

<img width="775" height="413" alt="Screenshot 2026-03-13 at 21 07 34" src="https://github.com/user-attachments/assets/99bdac8e-6545-42dd-b33e-529ac0867ddb" />

going into **wordpress** endpoint 

<img width="1470" height="961" alt="Screenshot 2026-03-13 at 18 10 43" src="https://github.com/user-attachments/assets/2d227775-3d01-47a8-b9ce-d11a2cb77783" />

## port 139 and 445 

**netbios** -- the service which is used by the samba for finding the computers that are sharing files on the local network like finding the listening port of the file sharing computer. 

**samba** -- application which is used for sharing files along a local network in the form of shares.

**smb** -- a protocol in the application layer which is used to share files across the local network.

**smbd** -- a deamon that runs the samba application in the background that uses the smb protocol.

**Difference b/w 139 and 445** 

139 port uses the netbios over tcp/ip connection for file sharing and finding the file sharing device.
445 port does not use the netbios for finding the computer instead that directly use tcp/ip protocols.

## Connecting to port 139 or 445 

### smbclient -L // ip -N

<img width="727" height="202" alt="Screenshot 2026-03-14 at 11 17 21" src="https://github.com/user-attachments/assets/1ecbd0db-8440-49e6-b79d-a867a566aa0f" />

listing all the shares(directory) that the computer is sharing in the LAN.

### smbclient // ip -N

<img width="772" height="394" alt="Screenshot 2026-03-14 at 11 18 17" src="https://github.com/user-attachments/assets/e3d3084a-abe4-4b9b-b164-c751e2c8c794" />

connecting to the samba application using smbclient command tool.

<img width="844" height="170" alt="Screenshot 2026-03-14 at 11 20 29" src="https://github.com/user-attachments/assets/e19a3950-e447-452f-a71f-17e5d5f259f5" />

here we got a password **12345**

todolist.txt output :

<img width="799" height="54" alt="Screenshot 2026-03-14 at 11 21 51" src="https://github.com/user-attachments/assets/1efd8614-64f2-4601-a452-ebe20d4147a5" />

initially he said that **togie** is his name and here is a password of something that he is storing.

try to ssh :

### ssh togie@<ip> -p 22  and password : 12345

check for the privilages for the togie user 

<img width="1122" height="157" alt="Screenshot 2026-03-14 at 11 34 09" src="https://github.com/user-attachments/assets/e89f21ee-fd50-4393-bed6-aba7767413b5" />

he is a root user. essentially he can run any command like normal root user without restrictions.

## gaining root access

### sudo -i 

<img width="536" height="596" alt="Screenshot 2026-03-14 at 11 36 13" src="https://github.com/user-attachments/assets/731f2861-7d0d-4df1-8f06-6b048988707c" />


in the wordpress directory of the smbclient we got the credentials of the mysql database of the users like he is sharing the website database related files also :

<img width="1470" height="944" alt="Screenshot 2026-03-13 at 17 43 30" src="https://github.com/user-attachments/assets/de34ed71-d3e4-47c6-8f2c-dbe054183d9e" />

but unable to connect to the mysql server through the credentials :

<img width="888" height="117" alt="Screenshot 2026-03-14 at 11 41 18" src="https://github.com/user-attachments/assets/3c7b77d0-83f1-4a93-85bd-5cf581259798" />


