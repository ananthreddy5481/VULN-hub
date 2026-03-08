## Dina: 1.0.1

<img width="1039" height="354" alt="Screenshot 2026-03-07 at 16 51 54" src="https://github.com/user-attachments/assets/abde6edf-a1aa-4d45-9c58-253f23c468e7" />

### nmap -sn <attacker_ip>

<img width="666" height="252" alt="Screenshot 2026-03-07 at 16 53 07" src="https://github.com/user-attachments/assets/f1305fff-426b-49a5-9076-0b6c988681b5" />

### nmap -sV <lab_ip>

<img width="632" height="154" alt="Screenshot 2026-03-07 at 16 53 56" src="https://github.com/user-attachments/assets/e18c1fc5-0eea-43ff-a371-fb4fe2ecd661" />

**In robots.txt**

<img width="623" height="140" alt="Screenshot 2026-03-07 at 16 54 46" src="https://github.com/user-attachments/assets/77327eda-5160-4099-8648-5872f03372bb" />

in the directries mentioned above only the **"nothing"** directory have something in the pagesource.

<img width="718" height="282" alt="Screenshot 2026-03-07 at 17 03 22" src="https://github.com/user-attachments/assets/7514530e-d769-43cf-8fd9-675174f1bef7" />

directory search -- **dirsearch -u <url>**

<img width="692" height="770" alt="Screenshot 2026-03-07 at 18 07 14" src="https://github.com/user-attachments/assets/2c1c4f79-dbef-4720-b962-3986b4896132" />

### endpoints -- /robots.txt : /secure/ : /tmp/ : /uploads/

in the above endpoints we have already seen the tmp and uploads in the robots.txt which is empty.

## /secure/ 

<img width="637" height="260" alt="Screenshot 2026-03-07 at 18 10 36" src="https://github.com/user-attachments/assets/42e042cd-7869-49fc-a4f5-b622a89c5df2" />

the **backup.zip** file is protected with password. one of the above passwords that we got earilier ( pw = freedom )

## strings backup-cred.mp3 

<img width="1292" height="110" alt="Screenshot 2026-03-07 at 18 14 41" src="https://github.com/user-attachments/assets/e80b7daf-af48-46d7-8aa9-f96d12401917" />

going to the endpoint mentioned in the above img :

<img width="2940" height="1912" alt="image" src="https://github.com/user-attachments/assets/e1a66482-acf5-43cb-8ffc-1eb6d46aada3" />

password is **"diana"** as that is the smallest one among those.

also in the page source :

<img width="1368" height="197" alt="Screenshot 2026-03-07 at 18 21 51" src="https://github.com/user-attachments/assets/00dfd8dd-0aa2-4e1a-824d-d2c4847bcb7c" />

which means -- turtle loves you until death.



