## NETWORKING:

Place both the vms into one network. use the bridged network type for keeping the lab vm and ubuntu vm and mac in the same network.

## SCANNING THE IP :

checking weather both vms are on same network or not.
the ip of the lab vm is given on the home screen of the vm and for finding the ip of the linux :
## ip a

if the first 3 parts of the ip address are same then that means they are on same network.

Scanning the ip address using the nmap on the ip address ::

<img width="2780" height="1306" alt="image" src="https://github.com/user-attachments/assets/5b030bad-676e-42e8-8bf0-dff293602c35" />

-sV -- service detetcion. wihout this the nmap gives the service based on the port and their default service does not search in depth.


## port - 21

command :: ftp <ip> :: ftp 10.190.199.148

common ftp user credentials :: username - "anonymous"  password - "anything" 

<img width="674" height="403" alt="Screenshot 2026-03-01 at 11 03 09" src="https://github.com/user-attachments/assets/27501139-34be-4e3d-aeb8-349c9edcd6bf" />

flag :: Whoa this is unexpected - 10 points 

FTP -- FILE TRANSFER PROTOCOL
      service which provides the connection between two systems to share files by allowing access to the directories and folders.

## port - 22 

**SHH** SECURE SHELL - Used to send send commands from one system to the remote system 

<img width="450" height="120" alt="Screenshot 2026-03-01 at 11 35 31" src="https://github.com/user-attachments/assets/46c86858-7f18-4661-8e1e-3f18fb10322d" />

this connection closes immediately after giving the username that means the server is not allowing users from this port.


## port - 80 

robots.txt -- reveals some files and navigate through the file for more info.

<img width="528" height="82" alt="Screenshot 2026-03-01 at 11 58 53" src="https://github.com/user-attachments/assets/d5b800af-1016-4c93-a466-f1a4fc198083" />

the path **"/cgi-bin/tracertool.cgi"** will take u to a user input function which is taking the user input and running the tracertool function inside the other terminal.

this is having command injection that is the user input is directly going into the shell commands.
exploring the other directories :
ROOT directories :

<img width="86" height="305" alt="Screenshot 2026-03-01 at 12 03 27" src="https://github.com/user-attachments/assets/10d5c45d-c936-4e56-aebd-1bd7ad0fa7fa" />

each directory has one function :

**etc** directory :
most of the configuration files are stored in this directory.
example important files in this directory:
**etc/passwd**   -- this folder stores the information about the users that are loggined into the system. ( will not store the passswords )

**etc/shadow** -- this stores the encrypted passwords of the users ( not accessble to the general users )

**etc/hostname** -- mapped data of ip addresses and hostnames

**etc/ssh** -- stores the configuration files of the ssh like the ports opertating the ssh service etc.

**etc/crontab** -- stores the information about the cron jobs(automated tasks performed on the basis of the time).(like refreshing the files in the var directory)

in the **passwd** directory i can see the usernames :(the users who have bash shell as their default)

<img width="434" height="54" alt="Screenshot 2026-03-01 at 14 18 35" src="https://github.com/user-attachments/assets/6fb68fab-277a-4e5d-aced-20f6bd3b66bf" />

**NIKTO** -- Tool used for scanning the unknown endpoints for a site.

command -- nikto -h http://10.135.36.148/

<img width="925" height="452" alt="Screenshot 2026-03-01 at 14 29 34" src="https://github.com/user-attachments/assets/412929f9-9b5b-4774-b060-7ab464400d3c" />

<img width="445" height="213" alt="Screenshot 2026-03-01 at 14 32 26" src="https://github.com/user-attachments/assets/dad71049-9b50-4f0a-b9bf-cc48eac90f7e" />

**FLAG -- Yeah d- just don't do it.**

<img width="1383" height="203" alt="Screenshot 2026-03-01 at 14 33 58" src="https://github.com/user-attachments/assets/8c1ead1c-d3f1-4e98-b932-d2e08e5c81bc" />

password is **winter** so the user must be summer from the above three users.

**USERNAME :: Summer**

**cgi-bin** -- this file stores the cgi files(the files which are written in python,bash etc languages where the instructions are ran based on the user input)

## PORT - 9090

service -- zeus-admin service that runs over http protocol that is used to manage the zeus-admin webserver.

check the website :
<img width="884" height="744" alt="Screenshot 2026-03-01 at 15 10 49" src="https://github.com/user-attachments/assets/a9126b08-87a9-4f72-8876-1264fced4963" />

## FLAG -- There is no Zeus, in your face!

## PORT - 13337 

the service is unknown to the nmap scan.
using the nc we can

<img width="537" height="74" alt="Screenshot 2026-03-01 at 15 43 47" src="https://github.com/user-attachments/assets/be5e635e-c76d-4c27-8940-e34cea8bceb0" />

## PORT - 22222
ssh -- protocol service 

**Command :: ssh -p 22222 Summer@10.135.36.148**
connecting to the shell using the Summer username and his password winter.

<img width="398" height="85" alt="Screenshot 2026-03-01 at 16 13 23" src="https://github.com/user-attachments/assets/54dd214c-b2ce-49fa-8b55-773a55a13932" />

## FLAG -- Get off the high road Summer!

<img width="1066" height="83" alt="Screenshot 2026-03-01 at 16 23 17" src="https://github.com/user-attachments/assets/191df078-6c22-4864-a110-fd871dadaf82" />

giving some clue. a message for the rick to use teh command line arguments.

explore the other two directories :

<img width="710" height="386" alt="Screenshot 2026-03-01 at 16 27 26" src="https://github.com/user-attachments/assets/213cb12e-738e-4f8e-a0a5-f6e2e2540f67" />

in the NotAFlag.txt file also there i nothing.

<img width="656" height="211" alt="Screenshot 2026-03-01 at 16 29 26" src="https://github.com/user-attachments/assets/5dc758ec-2e10-4ed6-844b-65a6a2ea4bcd" />

in the Morty directory there is ziped journal to unzip this we need the password. may the password may be there in the safe_password.zip file.

<img width="656" height="116" alt="Screenshot 2026-03-01 at 16 40 42" src="https://github.com/user-attachments/assets/ebda15d0-0fa8-4bea-9d35-a263a0f45e7a" />

needed spl tools to view the images called imagemagick
<img width="778" height="144" alt="Screenshot 2026-03-01 at 16 42 01" src="https://github.com/user-attachments/assets/9527f9f2-a193-46be-9735-6a2a647ab66f" />

## sudoers file

the file which will list the users who have the sudo root user privilages.

this user is not in the sudoers list so cannot download the tool.

instead copy the file using the **secure copy(scp)** command and copy that to your system.

**command :: scp username@remote_host:/path/to/source/file.txt /path/to/local/destination/**

**payload :: scp -P 22222 Summer@10.135.36.148:/home/Morty/Safe_Password.jpg .**

<img width="974" height="226" alt="Screenshot 2026-03-01 at 16 46 57" src="https://github.com/user-attachments/assets/de35f799-b066-4beb-b7c0-cd0bc53401b9" />

## binwalker command -- can be used to find the details about the image file 
## strings -- command can be used to get the output of the readble text from a file.

<img width="765" height="97" alt="Screenshot 2026-03-01 at 16 50 01" src="https://github.com/user-attachments/assets/1937af20-435c-4981-9b83-7b3d256f9b92" />

##Password(zip file) -- Meeseek

as the Summer usr does not have permissions to create a new files or folders so copy that also to your system.

<img width="1314" height="80" alt="Screenshot 2026-03-01 at 16 55 07" src="https://github.com/user-attachments/assets/0ab306cd-a660-44fe-8ca4-25db45ae8959" />

after that unzip and open the journal file :
<img width="1386" height="320" alt="Screenshot 2026-03-01 at 17 02 35" src="https://github.com/user-attachments/assets/2bdd5c6a-666b-4d52-b2bd-6077ce1f0d8e" />

## FLAG -- 131333

here the clue is that "131333" is the payload for the previous clue that command line argument.

in the RickSanchez directory :

<img width="393" height="104" alt="Screenshot 2026-03-01 at 17 11 42" src="https://github.com/user-attachments/assets/b2a55008-b515-49d6-a34d-40715328fc89" />
cannot execute the file "safe" as the Summer does not have the permissions. so copy that to the "summer" user using the cfollowing command:

## scp -P 22222 Summer@10.135.36.148:/home/RickSanchez/RICKS_SAFE/safe .

the clue is saying that Rick should pass the arguments for the executing file "safe"

## ./safe 131333 

<img width="1384" height="293" alt="Screenshot 2026-03-02 at 00 51 07" src="https://github.com/user-attachments/assets/328833e2-c924-4752-81c3-2fb5427c3fc1" />

## FLAG - And Awwwaaaaayyyy we Go!

from the clues :
1) the last band The Flesh Curtains -- one of the three words 
2) for the other two first charecters we need to brute force using ssh brute forcing tools

## brute forcing using the hydra and crunch tool

**Hydra** : used for brute forcing the ssh protocols .
**crunch** : used for making the wordlist for brute forcing

making wordlist : 

## crunch 7 7 -t ,%Flesh -o wordlist.txt
## crunch 10 10 -t ,%Curtains >> wordlist.txt**

**brute forcing**
## hydra -l RickSanchez -P wordlist.txt ssh://10.135.36.148 -s 22222

<img width="1387" height="332" alt="Screenshot 2026-03-02 at 01 09 56" src="https://github.com/user-attachments/assets/188919e0-fe72-448e-90a0-bc4a0dc5c0fb" />
## username : RickSanchez  password : P7Curtains

login into the new user :

<img width="847" height="162" alt="Screenshot 2026-03-02 at 01 11 51" src="https://github.com/user-attachments/assets/52bad27d-7fe4-40ff-ac41-4b518abc1843" />

we can check weather he can escalate the privialges or not using the **sudo -l** if the user is able to execute the sudo then that means he has the root user permissions.

<img width="1387" height="268" alt="Screenshot 2026-03-02 at 01 14 26" src="https://github.com/user-attachments/assets/46a574f7-6846-405a-be27-a86f9a2bc250" />

## sudo -i 
initial login mode that is treat this as the first login that is root login.

<img width="391" height="120" alt="Screenshot 2026-03-02 at 01 17 48" src="https://github.com/user-attachments/assets/e7040436-b18e-4386-ba86-e21a7caef3ed" />

this is how we get the root user.

## FLAG -- Ionic Defibrillator


## POST - 60000

<img width="447" height="255" alt="Screenshot 2026-03-01 at 15 47 22" src="https://github.com/user-attachments/assets/57809ce4-c0ac-4c83-ba13-6ca15d646f52" />





