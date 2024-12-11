<h1>Introduction to Django</h1>
<h3>219-day-streak</h3>

<br>

![image](https://github.com/user-attachments/assets/a90b2a0d-c263-4d87-bfee-42a8d476cff8)


<br>

![image](https://github.com/user-attachments/assets/92f03208-68bb-4466-891b-c0f5d02cc0b6)

<br>

<h2>Task 1. Unit 1: Introduction</h2>

<br>

![image](https://github.com/user-attachments/assets/250c629a-c5d8-42c4-b093-01a93e3b4f7a)

<br>

<p>Learning Python can be extremely useful for penetration testers, and a simple understanding of its frameworks can be a key to success. In this lesson, we are going to learn about one of the best ones ever made: Django. <br>

Django is a high-level Python web framework that enables rapid development of secure and maintainable websites. It allows you to develop websites and web applications in a matter of hours.<br>

Django can automatically compile HTML code, therefore making it possible for anyone without any advanced knowledge in markup languages to develop a website. Additionally, Django is arguably one of the most secure developing frameworks, which in the right configuration, can strongly resist against SQL injections and XSS.<br>

All in all, if you are familiar with Python and considering creating a website, Django can be a really good choice. As for penetration tester, it is important to understand the basic structure of Django-powered websites in order to be able to identify possible weaknesses and mistakes a developer can make.</p>


<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

<br>

> 1.1. <em>Read the above.</em><br><a id='1.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>


<h2>Task 2. Unit 2: Getting Started</h2>

<p>Attention! If you have absolutely no experience in python, I recommend doing this room on python basics: "Intro To Python"<br>

For this room, we are going to use Python 3. (Any 3.x.x works here) with Django 2.2<br>

Install Django by running this command:<br>

<code>pip3 install Django==2.2.12</code><br><br>

Now we are ready to create and properly configure our first website.<br>

Make a directory for your project files and navigate there with the command prompt.<br>

run django-admin startproject {project_name} in order to start your project. (Replace {project_name} with your prefered name).<br>

Run python3 manage.py migrateto automatically configure new files.<br>

After creating the project you can see that Django creates a file manage.py and a file directory named after your project.<br>

manage.py is a command-line utility that lets you interact with your Django project in various ways. It is especially handy in creating web-apps, managing databases, and most importantly running the server.<br>

Basic syntax for using this utility is <code>python3 manage.py {command}</code></p>

> runserver

<p>Runserver is the most important command used with manage.py; It allows you to deploy your website on the server. Django has a wonderful feature that allows you to instantly see changes made on the website without restarting it. (It is only necessary to restart runserver command when adding a new app).<br>

Run this command and navigate to your website with IP given in the outline. You should see a page like this:</p>

<br>

![image](https://github.com/user-attachments/assets/d8f385a5-a166-42e8-9b1f-5bc8e91bef73)

<br>

<p>Note: If you are willing to run the server to your local network, just add 0.0.0.0:8000 after runserver command. (In case if you get an error afterward, just go to settings.py located your websites folder and add this address to ALLOWED_HOSTS)</p>

![image](https://github.com/user-attachments/assets/958d12fa-c9f6-48bf-ab62-cc8417b77769)

<br>

> createsuperuser
>
> <br>

<p>This command allows you to create an admin account for your Django web admin panel.<br>

Run this command and access the panel at IP:8000/admin</p>

<br>

![image](https://github.com/user-attachments/assets/3a7ec91b-55f5-4753-883c-d590f00bb6a6)

<br>


> startapp


<br>

<p>Startapp allows you to initialize an app for your project. Django projects can have infinite number of apps. Basic syntax:<br>

python3 manage.py startapp {app_name}</p>

<br>


<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

<br>

> 2.1. <em>How would we create an app called Forms? </em><br><a id='2.1'></a>
>> <code><strong>python3 manage.py startapp Forms</strong></code>

<br>

> 2.2. <em>How would we run our project to a local network?</em><br><a id='2.2'></a>
>> <code><strong>python3 manage.py runserver 0.0.0.0:8000</strong></code>

<br>


<h2>Task 3. Unit 3: Creating a website</h2>

<p>......</p>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

<br>

> 3.1. <em>Read the above.</em><br><a id='3.1'></a>
>> <code><strong>No answer needed</strong></code>

<br>


<h2>Task 4. Unit 4: Concluding</h2>

<p>.....</p>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

<br>

> 4.1. <em>Flag from GitHub page</em><br><a id='4.1'></a>
>> <code><strong>THM{g1t_djang0_hUb}</strong></code>

<br>

![image](https://github.com/user-attachments/assets/ae1d4903-98cd-4806-be23-47f01e57091c)

<br>




<h2>Task 5. Unit 5: CTF</h2>

<br>

<h3 align="left"> $$\textcolor{#f00c17}{\textnormal{Answer the question below}}$$ </h3>

<br>

> 5.1. <em>Flag from GitHub page</em><br><a id='5.1'></a>
>> <code><strong>THM{g1t_djang0_hUb}</strong></code>

<br>

> 5.2. <em>User flag?</em><br><a id='5.2'></a>
>> <code><strong>THM{SSH_gUy_101}</strong></code>

<br>

> 5.3. <em>Hidden flag?</em><br><a id='5.3'></a>
>> <code><strong></strTHM{django_w1zzard}ong></code>

<br>


<br>

![image](https://github.com/user-attachments/assets/d0231776-85ca-4bfc-84ee-c5ddd14b737d)

<br>

![image](https://github.com/user-attachments/assets/c6f6a011-8f82-418d-ab67-23b6add054fa)

<br>


![image](https://github.com/user-attachments/assets/83f63ead-7456-410c-972d-a72f228ff2d1)

<br>

![image](https://github.com/user-attachments/assets/ae1a5a8c-e478-4db8-a63f-654126aa834b)

<br>

![image](https://github.com/user-attachments/assets/2020a809-7973-4ee1-a73f-f18549b87cac)

<br>

![image](https://github.com/user-attachments/assets/08175b51-687a-4479-8bd8-ba7a7975ab4a)

<br>


![image](https://github.com/user-attachments/assets/f8dfe079-3304-477b-9b84-90444dc8664c)

<br>

![image](https://github.com/user-attachments/assets/40e0a445-d6c5-4a95-abe3-7eb135d51f79)

<br>



![image](https://github.com/user-attachments/assets/7626c97a-eff2-418a-9b62-8c1ae6516668)


<br>

![image](https://github.com/user-attachments/assets/81bd26e2-5d26-4c51-a792-e22a188dbb3e)









