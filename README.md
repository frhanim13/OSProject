# OSProject Running Containers for Application Development

Group Name: __Fill your team name__. 

Section: 3

Team Mates:
1. SITI NURFARAHANIM BINTI MOHD ISA (2119316)
2. Aisha Mohammed Alwan Aljuboori (2125992)



***Questions:***

1. What is the link of the fork OSProject in your repository. ***(1 mark)*** https://github.com/frhanim13/OSProject
2. How many files and folders are in this repository. ***(1 mark)*** <br> 1 readme.md file , 1 images folder 
 


***Questions:***

1. What is default OS used to run the virtual environment for codespaces. ***(1 mark)***  Ubuntu linux 
2. What are the two options of ram, disk and vcpu configuration you can have in running codespaces . ***(1 mark)***  <br>  <img width="763" alt="image" src="https://github.com/frhanim13/OSProject/assets/48370531/0b36287a-5e55-47fa-b63a-ebece7a02850">  <br> 
Option 1 :

RAM : 8 GB  <br> 
DISK: 32 GB  <br> 
VCPU 2 CORE  <br> 

OPTION 2: <br> 

RAM:16 GB <br> 
DISK: 32 GB <br> 
VCPU: 4 <br> 
   

3.. Why must we commit and sync our current work on source control? ***(1 mark)***   <br> So we will not lost our works and collaborators also got the latest version of the code. 

## Exploring the Terminal


***Questions:***

Look at the TERMINAL tab. Run the following commands and provide the output here. 

1. Run the command **pwd** . ***(1 mark)*** __ ![Alt text](q1.PNG) __
2. Run the command **cat /etc/passwd** . ***(1 mark)*** __ ![Alt text](q2-1.PNG) __
3. Run the command **df** . ***(1 mark)*** __ ![Alt text](q3.PNG) __
4. Run the command **du** . ***(1 mark)*** __ ![Alt text](q4p1.PNG) / ![Alt text](q4p2.PNG) __
5. Run the command **ls** . ***(1 mark)*** __ ![Alt text](q5.PNG) __
6. Run the command **ls -asl** . ***(1 mark)*** __ ![Alt text](q6.PNG) __
7. Run the command **free -h** . ***(1 mark)*** __ ![Alt text](q7.PNG) __
8. Run the command **cat /proc/cpuinfo** . ***(1 mark)*** __ ![Alt text](q8p1.PNG) / ![Alt text](q8p2.PNG) __
9. Run the command **top** and type **q** to quit. ***(1 mark)*** __ ![Alt text](q9.PNG) __
10. Run the command **uname -a**. ***(1 mark)*** __ ![Alt text](q10.PNG) __
11. What is the available free memory in the system. ***(1 mark)*** __148Mi__.
12. What is the available disk space mounted on /workspace. ***(1 mark)*** __17516344__.
13. Name the version and hardware architecture of the linux Virtual environment. ***(1 mark)*** __Linux codespaces-521c8f 6.2.0-1018-azure #18~22.04.1-Ubuntu SMP Tue Nov 21 19:25:02 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux__.
14. What is the difference between **ls** vs **ls -asl**. ***(1 mark)*** __The ls command is used to list files and directories in Linux. The ls -asl command displays some additional details__.
15. What is the TLB size of the Virtual CPU. ***(1 mark)*** __2560 4K pages__.
16. What is the CPU speed of the Virtual CPU. ***(1 mark)*** __3165.560__.
17. What is the top running process that consumes the most CPU cycles. ***(1 mark)*** __10:44:13 up 38 min, 0 users, load average: 1.05, 0.39, 0.28__.

## Running your own container instance.

<img width="1052" alt="image" src="https://github.com/frhanim13/OSProject/assets/48370531/b4ed1140-c61e-4446-9209-b9ab376483c2">

<img width="1052" alt="image" src="https://github.com/frhanim13/OSProject/assets/48370531/34264cf6-db7e-4de2-9376-6516b2ad4bd2">

<img width="1052" alt="image" src="https://github.com/frhanim13/OSProject/assets/48370531/d0203b5e-91fa-461d-9a03-43483bbc47df">




1. At the terminal, run a linux instance. By typing the following command. 
```
docker pull debian
docker run --detach -it debian
```
2. This will run the debian container. To check if the debian container is running, type
```bash
@joeynor ➜ /workspaces/OSProject (main) $ docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED         STATUS         PORTS     NAMES
f65be1987f84   debian    "bash"    4 minutes ago   Up 4 minutes             romantic_jackson
```

3. Keep note of the name used by your container, this is usually given random names unless you specify your own name. Now run a bash command on the container. Make sure you use the name of your container instead of the one shown here. 
```bash
docker exec -i -t romantic_jackson /bin/bash
```

4. Create a file on the container. First you must make sure you are in the bash command prompt of the container. The container is new, and does not have any software other than the debian OS. To create a new file, you will need an editor installed. In the bash shell of the container, run the package manager apt-get to install nano text editor. 

```bash
root@f65be1987f84:~# apt-get update      

root@f65be1987f84:~# apt-get install nano

root@f65be1987f84:~# cd /root

root@f65be1987f84:~# nano helloworld.txt
```

5. Edit your helloworld.txt, create your messsage and save by typing ctrl-X. Once saved, explore using the container to see where the file is located. Then exit the shell, by typing **exit**.

6. Stop the container and run **docker ps -a**, and restart the container again. Is your file in the container still available?
```bash 
@joeynor ➜ /workspaces/OSProject (main) $ docker stop romantic_jackson

@joeynor ➜ /workspaces/OSProject (main) $ docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED          STATUS                        PORTS     NAMES
f65be1987f84   debian    "bash"    19 minutes ago   Exited (137) 18 seconds ago             romantic_jackson

@joeynor ➜ /workspaces/OSProject (main) $ docker restart romantic_jackson
```

7. Stop the container and delete the container. What happened to your helloworld.txt?

```bash 
@joeynor ➜ /workspaces/OSProject (main) $ docker stop romantic_jackson

@joeynor ➜ /workspaces/OSProject (main) $ docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED          STATUS                        PORTS     NAMES
f65be1987f84   debian    "bash"    19 minutes ago   Exited (137) 18 seconds ago             romantic_jackson

@joeynor ➜ /workspaces/OSProject (main) $ docker rm romantic_jackson
```

***Questions:***

1. Are files in the container persistent. Why not?. ***(1 mark)*** It is not persistent 
3. Can we run two, or three instances of debian linux? . ***(1 mark)*** Yes, either by virtualization or containers

## Running your own container with persistent storage




1. In the previous experiment, you might have notice that containers are not persistent. To make storage persistent, you will need to mount them. 
At the terminal, create a new directory called **myroot**, and run a instance of debian linux and mount myroot to the container. Find out the exact path of my root, and mount it as the root folder in the debian container. 
2. Create a file in /root on the container, the files should also appear in myroot of your host VM.

```bash 
@joeynor ➜ /workspaces/OSProject (main) $ mkdir myroot
@joeynor ➜ /workspaces/OSProject (main) $ cd myroot/
@joeynor ➜ /workspaces/OSProject/myroot (main) $ pwd
/workspaces/OSProject/myroot

@joeynor ➜ /workspaces/OSProject/myroot (main) $ docker run --detach -it -v /workspaces/OSProject/myroot:/root debian
```

***Questions:***

1. Check the permission of the files created in myroot, what user and group is the files created in docker container on the host virtual machine? . ***(2 mark)*** <br> <img width="1052" alt="image" src="https://github.com/frhanim13/OSProject/assets/48370531/143d1c7c-1271-4f72-ae11-ffcb44180f6f"> <br> user : codespace <br>  group : codespace 

2. Can you change the permission of the files to user codespace.  You will need this to be able to commit and get points for this question. ***(2 mark)***
```bash
//use sudo and chown
sudo chown -R codespace:codespace myroot

```
*** __Fill answer here__.***

## You are on your own, create your own static webpage

1. Create a directory called webpage in your host machine
2. Inside the directory, create a page index.html, with any content you would like
3. Then, run the apache webserver and mount the webpage directory to it. Hint:
```bash
## the -p 8080:80 flag points the host port 8080 to the container port 80

docker run --detach -v /workspaces/OSProject/webpage:/usr/local/apache2/htdocs/ -p 8080:80 httpd
```

4. If it works, codespace will trigger a port assignment and provide a URL for you to access your webpage like the one below.

 <img src="./images/websitelink.png" width="70%">


5. You can also see the Port in the **PORTS** tab, next to the terminal tab.

6. You can then access your website by adding an index.html towards the end of your url link, like the one below. 

 <img src="./images/helloworldweb.png" width="70%">

***Questions:***

1. What is the permission of folder /usr/local/apache/htdocs and what user and group owns the folder? . ***(2 mark)*** __Fill answer here__.
2. What port is the apache web server running. ***(1 mark)*** 8080
3. What port is open for http protocol on the host machine? ***(1 mark)*** 80 

## What to submit

1. Make sure to commit all changes on your source control, and make sure your source control is sync to the repository. 
2. Check your repository link, to see if all the files and answers are included in the repository. 
3. Submit through italeem, by providing the link to your repository.
4. Due by ***31 January, 2024***
