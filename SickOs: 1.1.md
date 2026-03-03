Unlike the previous RICK box here we are not getting the ip of the box vm.

if we do the **ip a** we get the ip of the linux machine:

<img width="1075" height="361" alt="Screenshot 2026-03-02 at 18 33 49" src="https://github.com/user-attachments/assets/1b41854f-fe46-4985-a5fb-43e800d4d832" />

that means we need to scan the ips from 0 to 255 

## nmap -sn 10.135.36.0/24 

-sn -- ping scan -- host discovery scanning 

the first three parts of the ip address will tell about the network and the last part denote the host that is a system.

/24 -- the subnet -- denotes the size of the no of hosts. this will scan from 0 to 255.

<img width="760" height="210" alt="Screenshot 2026-03-02 at 18 42 22" src="https://github.com/user-attachments/assets/161a27b1-6ffb-4a1b-8523-1438fce34e24" />

## ip(box vm) -- 10.135.36.25

