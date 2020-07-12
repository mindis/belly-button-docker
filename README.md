# Belly Button Homework "Dockerized"

Docker is very important in the current job market.  This brief introduction is meant as a "bootcamp" (i.e. not "gentle") introduction to what Docker brings to the table.  The main focus is on Windows as Docker on Mac / Linux is much more straight forward.

## Lots Exciting Changes in the Windows Ecosystem!

### WSL2 - True Linux Kernel Running in Windows:

For the first time ever, a true Linux kernel can run on a Windows machine.  This kernal can access your Windows file system without issue. It is a true Linux kernal and not a mock version (like git bash).

[WSL 2 and Docker](https://www.youtube.com/watch?v=5RQbdMn04Oc)

[Install WSL2 on Windows](https://docs.microsoft.com/en-us/windows/wsl/install-win10)'

Docker is really meant to work with Windows 10 Professional and NOT Windows 10 Home.  If your are going to do a lot of Windows work, I would consider spending the $100 to upgrade to Windows Pro.

The following "trick" may or may not work but could save you $100 if you don't have Windows Professional.

Do the following:
- Start Windows Powershell as Admininstrator
- cd into c:\windows\system32
- create a vir.bat file with the following code and then run it:
```
pushd "%~dp0"
dir /b %SystemRoot%\servicing\Packages\*Hyper-V*.mum >hyper-v.txt
for /f %%i in ('findstr /i . hyper-v.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"
del hyper-v.txt
Dism /online /enable-feature /featurename:Microsoft-Hyper-V -All /LimitAccess /ALL
pause
```
- reboot
- confirm / enable required features by:
-- "Turn Windows Features On Off" and make sure the following are on:
<br><br><img src="images\Windows_On_Off.PNG"
     alt="Windows on off ( make sure wsl and virtual machine platform are on )"
     style="float: center; margin-left: 10px;" />
- reboot again

### Windows Terminal

Windows terminal is an awesome new product that makes all your possible windows scripting environments available from one program.  It's really amazing! DOS, PowerShell, Ubunto, Debian, Azure cloud and many more available from one tool!  

[Intro Video](https://www.youtube.com/watch?v=9jQthJ2uvLI)

[Install](https://www.microsoft.com/en-us/p/windows-terminal)

<br><br><img src="images\Terminal.PNG"
     alt="Windows Terminal is Awesome"
     style="float: center; margin-left: 10px;" />


## Install Docker and Docker-Machine

Docker will come with docker and docker-compose

[Install Docker Desktop on Windows](https://docs.docker.com/docker-for-windows/install/)<br>
[Install Docker Desktop on Mac](https://docs.docker.com/docker-for-mac/install/)

You need to install docker-machine by itself.  This is a very cool tool that makes deploying to the cloud super easy!
<br>[Install Docker-Machine](https://github.com/docker/machine/releases)

[Great WSL2 & Docker Article](https://www.hanselman.com/blog/HowToSetUpDockerWithinWindowsSystemForLinuxWSL2OnWindows10.aspx)

## Docker and Belly Button Homework Walkthrough

A lot of the structure from this demo is built upon the EXCELLENT course <b>Test-Driven Development with Python, Flask, and Docker</b>

[Course Link](https://testdriven.io/courses/tdd-flask/)

### AWS Setup ( Configuration ) for CLI:

[AWS Signup](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/get-set-up-for-amazon-ec2.html)<br>
[AWS IAM](https://aws.amazon.com/iam/)<br>

[Docker AWS Example](https://docs.docker.com/machine/examples/aws/)<br>

### Crucial Commands Demonstrated

- Create AWS Machine ```docker-machine create --driver amazonec2 <ec2_name>```<br>
- Get AWS IP: ```docker-macine ip <ec2_name>```<br>



