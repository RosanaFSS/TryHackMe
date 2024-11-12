<p align="center">November 12, 2024</p>
<p align="center">Hey there, fellow lifelong learner! I´m <a href="https://www.linkedin.com/in/rosanafssantos/">Rosana</a>, and I’m genuinely excited to join you on this adventure.<br>
It´s part of my $$\textcolor{#FF69B4}{\textbf{190}}$$-day-streak in  <a href="https://tryhackme.com/r/hacktivities">TryHackMe</a>.</p>

<h1 align="center"> $$\textcolor{#3bd62d}{\textnormal{ Expediting Registry Analysis }}$$ </h1>
<p align="center">This room explores different tools used to expedite analysis of registry data during investigation.</p>
<p align="center">Access this 🆓 TryHackMe CTF Room clicking <a href="https://tryhackme.com/r/room/expregistryforensics">Expediting Registry Analysis</a>.</p>
<p align="center">
  <img height="150px" hspace="20" src="https://github.com/user-attachments/assets/0a679284-0798-4f74-9098-92a98c6336e0"><br>
  <img width="800px" src="https://github.com/user-attachments/assets/54e2868b-89d6-4eeb-9689-c1579cddcf74">
</p>

<p align="center">Summary</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [1. Introduction](#1) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [2. Background Information](#2) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [3. Time to Analyze the Vulnerable Code!](#3) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [4. Exploitation](#4) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [5. Try It Yourself!](#5) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [6. Conclusion](#6) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [7. Room Complete](#7) &nbsp;&nbsp;&nbsp;&nbsp;▪️&nbsp;&nbsp;&nbsp;&nbsp; [8. My Journey](#8)

<br>
<br>
<br>
<h2 align="center">Task 1. Introduction<a id='1'></a></h2>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

> 1.1. <em>I have completed the prerequisites for the room.</em><br><a id='1.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

<h2 align="center">Task 2. Data Acquisition Considerations and the FTK Imager<a id='2'></a></h2>
<p>To start the investigation, Anna needs to acquire registry data. There are several ways to acquire registry data from a system. We will discuss the most common ones in this room. But before that, let's understand the difference between live and cold collections.</p>

<h3>Live Acquisition</h3>
<p>ive acquisition is done on a running system. In a live acquisition, the Windows OS is already loaded into the memory, and the configurations are all in the memory. In a live system, the registry hives files are locked and cannot be copied without special tools. However, in a live system, since the configuration is already loaded, we don't have to analyse the registry to identify the active configuration of the system (e.g., the CurrentControlSet key is already loaded, and we know which configuration is in use). However, the problem with acquiring registry data from a live system is that whatever tool we use will leave a trace and might overwrite some critical data points. For example, if we use FTK Imager to collect live data, we will have to execute FTK imager, adding an entry to all the registry keys that keep track of program execution. The most common reason a live acquisition is done is to save time. Taking a full disk image and then extracting data from that takes a lot of time and can be impractical when dealing with an outbreak or when quick results are required. It is often better to take a live collection when time is of the essence.</p>
<br>
<h3>Cold Acquisition</h3>
<p>A cold data acquisition is done when the system is not running. In such an acquisition, a full disk image is first taken of the system by putting the system's hard disk drive in a write blocker. The system is shut down at this point. This disk image is then hashed and copied, and all the analysis is done on a copy of the original disk image. This is done to maintain the integrity of the original evidence so that, if need be, it can be proven that the evidence was not tampered with and the results are reproducible. We first mount the disk image using image mounting software to analyse the registry from a cold acquisition and extract the data from the mounted image. Some tools like FTK Imager and Autopsy can perform both steps simultaneously, and we don't need a separate image mounting software to view the data. Though a cold acquisition takes a lot of time, as we can guess from the number of steps involved in this process, it is to be noted that a cold acquisition makes the most negligible impact on the system under analysis, as it can be done from a write-blocked disk image instead of an actual running system. A cold acquisition is more suitable if we have to ensure the integrity of the data for purposes such as going to court. </p>
<br>
<h3>Data Acquisition Using FTK Imager</h3>
<p>FTK Imager is a tool primarily used to take disk and memory images of a live system. However, it can also be used to read acquired disk images. Acquiring a full disk or memory image is out of the scope of this room. However, we will learn to acquire registry data using FTK Imager in this room.<br>

First, we must load the disk image from which we want to extract the data. In the attached VM, we can see the shortcut file for FTK Imager on the Desktop. After starting, we can <code>Add Evidence Item</code> by going to <code>File > Add Evidence Item</code>.</p>

<p>...............</p>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question2 below}}$$ </h3>

> 2.1. <em>I have collected registry data from the attached VM, as shown in this task.</em><br><a id='2.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>

> 2.2. <em>When we take a forensic data collection from the disk image of a system, what type of acquisition is it called?</em><br><a id='2.2'></a>
>> <code><strong>___________________</strong></code>

<br>

> 2.3. <em>Is speed one of the advantages of collecting registry data from FTK Imager? Y or N?</em><br><a id='2.2'></a>
>> <code><strong>___________________</strong></code>

<br>


![image](https://github.com/user-attachments/assets/5493cc7a-b7cd-4c11-9a46-4f037173ddb4)


