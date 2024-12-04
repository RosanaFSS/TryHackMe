<h1>Hacking with PowerShell</h1>
<p>October 19, 2024<br><br>
Learn the basics of Powershell and Powershell Scripting
<br>

![image](https://github.com/user-attachments/assets/06f2d3fc-73ad-4821-bd01-3606a87ae1f2)
<br>
Type: Easy<br>
Link: https://tryhackme.com/r/room/powershell</p><br>

<p><h2>Task 1 - Objectives</h2>
Before completing this room, you should be aware of some fundamentals. For example, the differences between CMD, PS and some syntax. This room will cover the following:

<ul>
  <li> What is Powershell</li>
  <li> Basic Powershell commands</li>
  <li> Windows enumeration skills</li>
  <li> Powershell scripting </li>
</ul> 

You can control the machine in your browser or <code>RDP</code> into the instance with the following credentials. 
<br>

![image](https://github.com/user-attachments/assets/53cb4ffc-37fd-44e9-8455-6bfb5f316412)


<p>1.1 - <em>Read the above and deploy the machine!</em><br>
  
>  No answer needed  </p>


<p><h2>Task 2 - What is Powershell?</h2>
Powershell is the Windows Scripting Language and shell environment built using the .NET framework. <br><br>
This also allows Powershell to execute .NET functions directly from its shell. Most Powershell commands, called cmdlets, are written in .NET. Unlike other scripting languages and shell environments, the output of these cmdlets are objects - making Powershell somewhat object-oriented.<br><br>
This also means that running cmdlets allows you to perform actions on the output object (which makes it convenient to pass output from one <em>cmdlet</em> to another). The normal format of a <em>cmdlet</em> is represented using <strong>Verb-Noun</strong>; for example, the <em>cmdlet</em> to list commands is called <code>Get-Command</code>. <br><br>
Common verbs to use include: 
<ul>
  <li> Get </li>
  <li> Start </li>
  <li> Stop </li>
  <li> Read </li>
  <li> Write </li>
  <li> New </li>
  <li> Out </li>
</ul> 
<p>To get the complete list of approved verbs, visit the following link.

[Approved Verbs for PowersShell Commands](https://learn.microsoft.com/en-us/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands?view=powershell-7.4&viewFallbackFrom=powershell-7)
</p>
<p> 2.1 - <em>What is the command to <strong>get</strong> a <strong>new</strong> object?</em><br>
  
> <code>Get-New</code></p>
<br>
<p><h2>Task 3 - Basic Powershell Commands</h2>
Now that we've understood how cmdlets work - let's explore how to use them! The main thing to remember here is that <code>Get-Command</code> and <code>Get-Help</code> are your best friends!<br>
<h3>Using Get-Help</h3>
<code>Get-Help</code> displays information about a cmdlet. To get help with a particular command, run the following: <br><br>
<code>Get-Help Command-Name</code> <br><br>
You can also understand how exactly to use the command by passing in the <code>-examples</code> flag. This would return output like the following:</p><br>
<p><strong>Running the Get-Help cmdlet to explain a command</strong><br>
<code>Get-Help Get-Command -Examples</code></p>

![image](https://github.com/user-attachments/assets/92a200ce-764a-4036-819b-82aea7a29f01)</p>

<h3>Using Get-Command</h3>
<p><code>Get-Command</code>code> gets all the cmdlets installed on the current Computer. The great thing about this cmdlet is that it allows for pattern matching like the following<br>

<code>Get-Command Verb-*</code> or <code>Get-Command *-Noun</code>

Running <code>Get-Command New-*</code> to view all the <em>cmdlets</em> for the verb new displays the following: <br>
<p><strong>Using the Get-Command to list all <em>cmdlets</em> installed</strong>
<br>

<code>Get-Command New-*</code></p>

![image](https://github.com/user-attachments/assets/fe5cd701-c90f-477f-bdf8-4ea1cc5da6fd)
<br><br>

<h3>Object Manipulation</h3>
<p>In the previous task, we saw how the output of every <em>cmdlet</em> is an object. If we want to manipulate the output, we need to figure out a few things: <br>
<ul>
  <li> passing the output to other <em>cmdlets</em></li>
  <li> using specific object cmdlets to extract information</li>
</ul> 
<br>
The Pipeline(<code>|</code>) is used to pass output from one <em>cmdlet</em> to another. A major difference compared to other shells is that Powershell passes an object to the next cmdlet instead of passing text or string to the command after the pipe. Like every object in object-oriented frameworks, an object will contain methods and properties.<br><br>
You can think of methods as functions that can be applied to output from the cmdlet, and you can think of properties as variables in the output from a cmdlet. To view these details, pass the output of a cmdlet to the <code>Get-Member</code> <em>cmdlet</em>:
<br>
<code>Verb-Noun | Get-Member</code>
<br>
An example of running this to view the members for <code>Get-Command</code> is: <br>
<br>
<p><strong>Using pipe (<code>|</code>) to pass output from one cmdlet to another</strong><br>
<code>Get-Command | Get-Member -MemberType Method</code></p>

![image](https://github.com/user-attachments/assets/f5bf744c-0eb6-4393-936c-1c70e2581757)
<br>
<h3>Creating Objects from Previous <em>cmdlets</em></h3>
<p>One way of manipulating objects is pulling out the properties from the output of a <em>cmdlet</em> and creating a new object. This is done using the <code>Select-Object</code <em>cmdlet</em></code>. <br><br> 
Here's an example of listing the directories and just selecting the mode and the name:
<br></p>

<p><strong>Listing the directories and filtering via mode and name</strong><br>
<code></code>Get-ChildItem | Select-Object -Property Mode, Name</code></p>

![image](https://github.com/user-attachments/assets/48c8ce83-c156-4bf2-b378-7b20425a2b9a)
<p>You can also use the following flags to select particular information:
<br>
<ul>
  <li> first - gets the first x object</li>
  <li> last - gets the last x object</li>
  <li> unique - shows the unique objects</li>
  <li> skip - skips x objects</li>
</ul> 
</p><br><br>

<h3>Filtering Objects</h3>
<p>When retrieving output objects, you may want to select objects that match a very specific value. You can do this using the <code>Where-Object</code> to filter based on the value of properties.<br><br> 
The general format for using this <em>cmdlet</em> is <br>
<code>Verb-Noun | Where-Object -Property PropertyName -operator Value</code><br>
<code>Verb-Noun | Where-Object {$_.PropertyName -operator Value}</code><br><br>
The second version uses the <code>$_</code> operator to iterate through every object passed to the <code>Where-Object</code> <em>cmdlet</em>.<br>
<strong>Powershell is quite sensitive, so don't put quotes around the command!</strong><br>
Where <code>-operator</code> is a list of the following operators:
<br>
<ul>
  <li> <code>-Contains</code>: if any item in the property value is an exact match for the specified value</li>
  <li> <code>-EQ</code>: if the property value is the same as the specified value</li>
  <li> <code>-GT</code>: if the property value is greater than the specified value</li>
</ul> 
</p>
<br>
<p>For a full list of operators, access the following link.<br>
  
[Where-Object](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/where-object?view=powershell-7.4&viewFallbackFrom=powershell-6)

Here's an example of checking the stopped processes:</p>
<p><strong>Demonstrating the use of operators only to show stopped services</strong><br>
<code>Get-Service | Where-Object -Property Status -eq Stopped</code></p>

![image](https://github.com/user-attachments/assets/616b6384-4a7c-42b4-ab00-65e06f0b6149)
<br><br>

<h3>Sort-Object</h3>
<p>When a cmdlet outputs a lot of information, you may need to sort it to extract the information more efficiently. You do this by pipe-lining the output of a cmdlet to the <code>Sort-Object</code> <em>cmdlet</em>.<br>
The format of the command would be:<p>
<code>Verb-Noun | Get-Member</code>
<br>
<p><strong>Using the <code>Sort-Object</code> cmdlet to sort piped information</strong><br>
<code>Get-ChildItem | Sort-Object</code>

![image](https://github.com/user-attachments/assets/dbd6bd81-8ce0-4b36-941e-92adb251303b)</p>

<p>Now that you've understood how Powershell works let's try some commands to apply this knowledge!</p>


3.1 - <em>What is the location of the file "interesting-file.txt".</em><br>
> <code>C:\Program Files</code><br><br>
![image](https://github.com/user-attachments/assets/9af38fc6-2b25-4473-9ab5-bcd944d4df35)


3.2 - <em>Specify the contents of this file.</em>e <br>
> notsointerestingcontent<br><br>
![image](https://github.com/user-attachments/assets/05d00dc7-bfb1-4edb-b74a-8701b7740eff)

<strong>3.3 - How many cmdlets are installed on the system(only cmdlets, not functions and aliases)?<strong> <br>
> 6638  <br><br>
![image](https://github.com/user-attachments/assets/a87402ea-a849-44bb-a983-09d22b1857a3)

<strong>3.4 - Get the MD5 hash of interesting-file.txt.<strong> <br>
>  49A586A2A9456226F8A1B4CEC6FAB329  <br><br>
![image](https://github.com/user-attachments/assets/82ba3651-d912-454f-885d-54c090e40436)

<strong>3.5 - What is the command to get the current working directory?<strong> <br>
>  <code>Get-Location</code><br><br>
![image](https://github.com/user-attachments/assets/e30e479f-e2ff-4c8f-a0cf-bb839e06c769)

<strong>3.6 - Does the path "C:\Users\Administrator\Documents\Passwords" Exist (Y/N)?<strong> <br>
>  N <br>
>>  <code>if(Set-Location C:\Users\Administrator\Documents\Passwords) {Write-Host "Path exists!"} Else{Write-Host "Path do NOT exist!!!"}</code> <br><br>
![image](https://github.com/user-attachments/assets/8bb69e46-6102-4912-ba3a-7fd1089fcbbb)

<strong>3.7 - What command would you use to make a request to a web server?<strong> <br>
>  <code>Invoke-WebRequest</code><br>
![image](https://github.com/user-attachments/assets/66d5c6ed-23d1-49e2-83b9-656b665c0b59)

> <strong>3.8 - Base64 decode the file b64.txt on Windows.<strong> <br>
>  ihopeyoudidthisonwindows <br>
![image](https://github.com/user-attachments/assets/c82e774e-85c3-4ad2-92e6-7216d931703d)



<h2>Task 4 - Enumeration</h2>
<p>The first step when you have gained initial access to any machine would be to enumerate.<br>
We'll be enumerating the following: users, basic networking information, file permissions, registry permissions, scheduled and running tasks
insecure files. <br>
Your task will be to answer the following questions to enumerate the machine using Powershell commands!</p>

<strong>4.1 - How many users are there on the machine?.<strong> <br>
> 5  <br>
>> <code>Get-LocalUser</code> <br><br>
![image](https://github.com/user-attachments/assets/12e094c8-3b20-4b81-a667-4c074ae8f5fd)

<strong>4.2 - Which local user does this SID(S-1-5-21-1394777289-3961777894-1791813945-501) belong to?<strong> <br>
> Guest  <br>
>> <code>Get-LocalUser -SID "S-1-5-21-1394777289-3961777894-1791813945-501"</code><br><br>
![image](https://github.com/user-attachments/assets/67b91791-64a9-4d4d-b7db-6cb3008e0c50)

<strong>4.3 - How many users have their password required values set to False?<strong> <br>
> 4  <br><br>
![image](https://github.com/user-attachments/assets/4db72e87-8d56-461e-80e9-50f20e30dbf8)

<strong>4.4 - How many local groups exist?<strong> <br>
>  24  <br><br>
![image](https://github.com/user-attachments/assets/44e85fd3-15f3-4d90-b1d1-4a339e453751)

<strong>4.5 - What command did you use to get the IP address info?<strong> <br>
>  <code>Get-NetIPAddress</code><br><br>
![image](https://github.com/user-attachments/assets/16f16150-105d-48ba-9a4d-0460fc1dc1c6)

<strong>4.6 - How many ports are listed as listening?<strong> <br>
>  20 <br>
>>  <code>GEt-NetTCPConnection | Where-Object -Property State -Match Listen | measure</code><br>
![image](https://github.com/user-attachments/assets/b16ecfe0-030d-451c-b9ba-703ef8f3d78b)

<strong>4.7 - What is the remote address of the local port listening on port 445?<strong> <br>
> ::<br>
>> <code>GEt-NetTCPConnection | Where-Object -Property State -Match Listen</code><br>
![image](https://github.com/user-attachments/assets/f60ff60c-1ff8-4c2f-bace-1f046cd89ed3)

<strong>4.8 - How many patches have been applied?<strong> <br>
>  20 <br>
>> <code>Get-Hotfix | measure</code><br>
![image](https://github.com/user-attachments/assets/d414518e-2152-4c8a-9814-fb454d15fd2c)<br>
![image](https://github.com/user-attachments/assets/a6288277-992f-48ac-bbb7-a40ce1019950)

<strong>4.9 - When was the patch with ID KB4023834 installed?<strong> <br>
>  6/15/2017 12:00:00 AM <br>
>> <ccode>Get-Hotfix -Id KB4023834</code><br>
![image](https://github.com/user-attachments/assets/84ff0c14-0901-437d-a0b7-283a1198d2e0)

<strong>4.10 - Find the contents of a backup file.<strong> <br>
>  backpassflag <br>
>> <code>Get-ChildItem -Path C:\ -Include *.bak* -File -Recurse -ErrorAction SilentlyContinue</code><br>
>> <code>Get-Content "C:\Program Files (x86)\Internet Explorer\passwords.bak.txt"</code>
![image](https://github.com/user-attachments/assets/a0657b15-8254-4057-beb7-4fd9d2c7d2c3)

<strong>4.11 - Search for all files containing API_KEY.<strong> <br>
>  fakekey123 <br>
>> <code>Get-ChildItem -Path C:\Users -Recurse -ErrorAction SilentlyContinue | Select-String “API_KEY”</code><br>
![image](https://github.com/user-attachments/assets/d222aa44-3e40-4f56-b707-38961744df56)

<strong>4.12 - What command do you do to list all the running processes?.<strong> <br>
>  <code>Get-Process</code><br>
![image](https://github.com/user-attachments/assets/9028b46d-6ce2-4d97-8c08-2c9e780a3d15)


<strong>4.13 - What is the path of the scheduled task called new-sched-task?.<strong> <br>
> <code>/</code> <br>
>> <code>Get-ScheduleTask -TaskName new-sched-task<br></code>
![image](https://github.com/user-attachments/assets/3f85b2fa-2a7a-422e-a61e-81566fc44341)


<strong>4.14 - Who is the owner of the C:\ ?<strong> <br>
>  NT SERVICE\TrustedInstaller <br>
>> <code>Get-Acl C:/</code><br>
![image](https://github.com/user-attachments/assets/e69f7189-236b-4a97-a477-4ee84759b865)


<h2>Task 5 - Basic Scripting Challenge</h2>

<p>Now that we have run Powershell commands, let's try to write and run a script to do more complex and powerful actions. <br>
For this ask, we'll use Powershell ISE (the Powershell Text Editor). Let's use a particular scenario to show an example of this script. Given a list of port numbers, we want to use this list to see if the local port is listening. Open the listening-ports.ps1 script on the Desktop using Powershell ISE. Powershell scripts usually have the .ps1 file extension.</p>

<p>> $system_ports = Get-NetTCPConnection -State Listen
> $text_port = Get-Content -Path C:\Users\Administrator\Desktop\ports.txt
> foreach($port in $text_port){
>    if($port -in $system_ports.LocalPort){
>        echo $port
>     }
>}</p>
<br>
<p>On the first line, we want to get a list of all the ports on the system that are listening. We do this using the Get-NetTCPConnection cmdlet. We are then saving the output of this cmdlet into a variable. The convention to create variables is used as:</p>
> $variable_name = value
<p>In the following line, we want to read a list of ports from the file. We do this using the Get-Content cmdlet. Again, we store this output in the variables. The simplest next step is to iterate through all the ports in the file to see if the ports are listening. To iterate through the ports in the file, we use the following:</p>
> foreach($new_var in $existing_var){}
<p>This particular code block is used to loop through a set of objects. Once we have each individual port, we want to check if this port occurs in the listening local ports. Instead of doing another for loop, we just use an if statement with the -in operator to check if the port exists in the LocalPort property of any object. A full list of if statement comparison operators can be found here. To run the script, call the script path using Powershell or click the green button on Powershell ISE:</p>



<p>Now that we've seen what a basic script looks like - it's time to write one of your own. The emails folder on the Desktop contains copies of the emails John, Martha, and Mary have been sending to each other(and themselves). Answer the following questions with regard to these emails (try not to open the files and use a script to answer the questions). <br>

Scripting may be a bit difficult, but here is a good resource to use: </p?

<strong>5.1 - What file contains the password?<strong> <br>
> Doc3M<br>
>> Get-ChildItem -Path C:\Users\Administrator\Desktop\emails -Recurse -ErrorAction SilentlyContinue | Select-String “password”<br>
![image](https://github.com/user-attachments/assets/4f257f6e-2742-4c87-8f7b-ea4e7cf71cb6)

<strong>5.2 - What is the password??<strong> <br>
> johnisalegend99
![image](https://github.com/user-attachments/assets/4f257f6e-2742-4c87-8f7b-ea4e7cf71cb6)

<strong>5.3 - What files contains an HTTPS link?<strong> <br>
>Doc2Mary
>> Get-ChildItem -Path C:\Users\Administrator\Desktop\emails -Recurse -ErrorAction SilentlyContinue | Select-String “HTTPS”
![image](https://github.com/user-attachments/assets/ec387707-e7e8-4301-b459-f88d6c230cf1)



<h2>Task 6 - Intermediate Scripting</h2>
<br>
<p>Now that you've learnt a little bit about how scripting works - let's try something a bit more interesting. Sometimes we may not have utilities like Nmap and Python available, and we are forced to write scripts to do very rudimentary tasks. <br>

Why don't you try writing a simple port scanner using Powershell? Here's the general approach to use:<br>

Determine IP ranges to scan(in this case it will be localhost) and you can provide the input in any way you want<br>
Determine the port ranges to scan<br>
Determine the type of scan to run(in this case it will be a simple TCP Connect Scan) </p>

<strong>6.1 - How many open ports did you find between 130 and 140(inclusive of those two)?<strong> <br>
>Doc2Mary


$ErrorActionPreference -eq "SilentlyContinue"
$Target -eq "localhost"
$LowEnd = 130
$HighEnd = 140
$X = 0

Do
{
$CurrentPort = $LowEnd + $X
if((Test-NetConnection -ErrorAction SilentlyContinue $Target -Port $CurrentPort).PingSucceeded -or (Test-NetConnection -ErrorAction SilentlyContinue $Target -Port $CurrentPort).TcpTestSucceeded)
{$CurrentPort | Out-File .\OpenPorts.txt -Append}
$X = $X + 1
}
While($CurrentPort -lt 140)

(Get-Content .\OpenPorts.txt).Count

![image](https://github.com/user-attachments/assets/3123b8a6-1928-4af7-b448-984fcbc7adb2)
![image](https://github.com/user-attachments/assets/e2c14597-5230-45bc-8bf3-bf4f40bc0a07)
![image](https://github.com/user-attachments/assets/c9716682-18d9-4fb9-a907-644392d7d7a8)
![image](https://github.com/user-attachments/assets/13f36841-d236-4c87-8d43-70a1241cd57e)


# ...

![image](https://github.com/user-attachments/assets/419af036-b95b-4fb0-a89f-6071f3f22cb8)

<div style="page-break-after: always!important; height: -10px;"></div>