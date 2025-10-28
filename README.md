# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system

## OUTPUT:


<img width="1273" height="441" alt="Screenshot 2025-10-28 200202" src="https://github.com/user-attachments/assets/11bc124b-8a4f-4f12-b6f7-f9f35d79bbed" />

Invoke msfconsole:
## OUTPUT:

<img width="1275" height="789" alt="Screenshot 2025-10-28 200217" src="https://github.com/user-attachments/assets/6c002efb-9b65-4eb8-bfe4-f8c25a2f08da" />

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

<img width="1012" height="645" alt="Screenshot 2025-10-28 204236" src="https://github.com/user-attachments/assets/2a96ef64-c2ee-44e0-acad-c02253525b52" />



Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="1273" height="511" alt="Screenshot 2025-10-28 200340" src="https://github.com/user-attachments/assets/bfba15a7-73d8-4f48-8150-c916f94fc4d8" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:

<img width="1281" height="463" alt="Screenshot 2025-10-28 200424" src="https://github.com/user-attachments/assets/bc752a62-a001-4f05-93ea-3bed9f423372" />


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

<img width="704" height="75" alt="Screenshot 2025-10-28 201129" src="https://github.com/user-attachments/assets/d15e87b2-7460-414f-9970-effd4daf0fc0" />


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:
<img width="1268" height="798" alt="Screenshot 2025-10-28 203405" src="https://github.com/user-attachments/assets/6dfd095e-22f9-4175-ae64-1556f169207a" />



The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:

<img width="732" height="213" alt="Screenshot 2025-10-28 205008" src="https://github.com/user-attachments/assets/1d903f84-004e-407f-b3f4-210c0700e04b" />



## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
<img width="1145" height="289" alt="Screenshot 2025-10-28 203544" src="https://github.com/user-attachments/assets/a9b9d121-a47d-468e-ac64-8727a8a7ed10" />

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
<img width="1260" height="546" alt="image" src="https://github.com/user-attachments/assets/d2287d17-4321-4759-894c-824978694946" />


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="1269" height="592" alt="Screenshot 2025-10-28 203640" src="https://github.com/user-attachments/assets/ee2c6676-06b9-4a72-902f-c05a88655616" />



Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="776" height="105" alt="Screenshot 2025-10-28 203742" src="https://github.com/user-attachments/assets/2c5c7270-9f77-4214-a3e4-25b22c98f56b" />


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:

<img width="1255" height="520" alt="Screenshot 2025-10-28 203825" src="https://github.com/user-attachments/assets/3ce73861-d54e-41b5-9e0c-326c0ac00242" />



set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:


<img width="1137" height="244" alt="Screenshot 2025-10-28 203842" src="https://github.com/user-attachments/assets/acc74473-7696-4053-9f1e-02acdbed65b6" />




## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
