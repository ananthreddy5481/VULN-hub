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




