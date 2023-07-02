# LaravelonAWS-EC2
Deploy Laravel application on EC2 Ubuntu Server with Apache, MySQL, PHP, PHPMyAdmin, and zip/unzip

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

  - [GitHUB Text Formatting](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

## How To Run Laravel application on AWS - Ubuntu Server

Deploy Laravel application on EC2 Ubuntu Server with Apache, MySQL, PHP, PHPMyAdmin, and zip/unzip


### How to Run the AWS EC2 Instance

Open AWS page, and navigate to >> Select services >> EC2 >> select Running Instances
1. Click on <code>Launch New Instance</code>
  - Step 1: Amazon Machine : select Ubuntu of your range
  - Step 2: Instane Type: Select
  - Step 3: Add Storage of your range from
  - Step 4:
  - Step 5:
  - Step 6:
  - Step 7: Key Pair: Create New piar for each Instance and download it in .ppk file extionsion. If you downloaded in .pem file format, 
      it will be then convert into .ppk extension using "PUTTY gen" application.
  - Final Step: Select **Launch Instance**.
<br />
<p>Once done, check the Instance Status, if it work fine, you will find the __Public IP__, __Privete IP__, __Public DNS__, and the __Key Pair file__   </p>

![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/ecec9541-1e17-440f-b1d4-d0ac2d42209b)

<br />

2. Connect Ubuntu Linux Server with SSH Terminal **PUTTY**
  - Start Putty application, and write the ```User_Name @ Public DNS address or IP```.
  
  - The default user-name for Ubuntu server is *Ubuntu*. The full syntax would be as <code>ubuntu@DNS</code>
    ![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/5cf99bc3-89dc-44a9-b1e8-7027011ae29c)
  
  - Atttach the .ppk file, under Configuration > Connection > SSH > Auth > Upload the **Private Key file** for Authentication.
    ![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/2a343714-c8c5-4b04-98d8-55535d952a75)

  - Click OK to connect, if you get the console screen like, below with your serverDNS address, its means it's Working Fine.
  ![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/6152bc94-3ad5-4adc-87ce-678d7515dfef)

### Installation of Apatche Server on Ubuntu Server
<p> Apatche web server is amoung most popular web servers in the World, due its well-documented and has been in wide use much of the history of Web which makes it great choice for Server based web application.
</p>
<p>First,, we need to Update and Upgrade all the modules. For this, we have coomands for both</p>

- To Update the Modules
```
sudo apt-get update
```

- To Upgrade the Modules
```
sudo apt-get upgrade
```

- To Install the zip/Unzip 
```
sudo apt install zip unzip
```

- To Install the Apache Server 
```
sudo apt install apache2
```

- To Restart the Apache Server 
```
sudo service apache2 restart
```
<p> To check whether the Apchae server is sussccfully installed or not. Copy the Public IP or ServerDNS address , and paste it into the brower to browe the server page. 

  ![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/ba625c14-42d8-4498-b168-1e0db206b7f2)
</p>

  ![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/ba625c14-42d8-4498-b168-1e0db206b7f2)

<p>if it shows the page like below, its means the Apache server is Installed and running successfully!

  ![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/e82752b8-1f5b-43e5-9104-20163a459d5a)

</p>


### 3. Install the MySQL Server 
<p> MySQL is the database management service which is used where we store and access the information</p>
- To Install the MySQL Server 

```
sudo apt install mysql-server
```

<p> When you run this, command, it will show some of the packages need to be installed and configured. Enter <code> Y </code> for Yes, to continue.</p>
#### Running mysql_secure_installation

<p>Before <b> July, 2022 </b> we directly use <code> mysql_secure_installation </code> for creating Password of MySQL Server, but <b> later on July, 2022 version </b> we will got error while creating password for a user 'root'@'localhost', as shown below ;

  ![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/2c83fe1c-f8b2-43dc-9528-e0c77a819604)


we need to make run configuration command  before running the mysql_secure_installtion, for that we first need to; </p>
- Enter to mysql directory, using

```
sudo mysql
```
once you enter to mysql> , then run the coomand for root@localhost
```
alter user root@localhost identified with mysql_native_password by 'Your-Password';
```
<p>You will find it works, now flush the privileges using command</p>

```
flush privileges;
```
<p> When privileges flushed, now exit from <code> mysql> </code>code> directory using exit command </p>

```
exit;
```
The path will be directed to the Ubuntu server, now it time to run <code> my_secure_installation </code> command for setting the Root password.

<p> Once SQL Server is installed, we have set the MySQL swerver Root Password, for which we use the below command;</p>

- To set the MySQL Server Root Password 
```
sudo mysql_secure_installation
```

- Enter <code> Y </code> for Yes
- Password Strength: Enter <code>0 for Low</code>, <code>1 for Medium level</code>, or <code>2 for High secure</code> password.
- New Password: Now 'Enter & Re-enter' your New password for the Root User.
- If the password strength is OK, to Continue : <code> press 'Y' </code>
- Remove anonymous User? : <code> press 'Y' </code>
- Disallow Root Login remotely? : <code> press 'N' </code>
- Remove test database? : <code> press 'N' </code>
- Reload Privilege tables now? : <code> press 'Y' </code>

Once we get the message 'All Done!', it means the MySQL server has beeen installed successfully, like shown below;
![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/7ea8baf2-0759-4de1-bb9f-caa2cd73c159)


### 4. Install the PhpMyAdmin

```
sudo apt install phpmyadmin
```
- Press <code> Y </code>
- select <code> apache </code> and press Enter
 ![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/d2932a7b-6332-4766-8d1b-5097485eecfc)
- Press <code> Y </code> for Configuring PHPmyAdmin
 ![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/bc36ab3c-f404-49de-b94d-22b5df1f85c0)
- Enter Password for PhpMyAdmin, and Confirm it
 ![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/e6cfc7ed-0ce8-4108-8fb3-fbd74be9a6c9)

<P> When it done. check to browse the /phpmyadmin dashboard</P>


```
http://server-IP/phpmyadmin
```
<p>if the URL request gave an *** Not Found *** message, then run the below command, to change the configuration;</p>

```
sudo nano /etc/apache2/apache2.conf
```
<p>We will get the page like below;</p>

![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/31458f0f-4e95-482c-9baf-4945b006c5a9)

<p> come to the bottom of the console page, and write the below configuration path to include </p>

```
include /etc/phpmyadmin/apache.conf
```

<p> To Save the above configuration file, 
  - Press <code> Ctrl + X </code> to save
  - Press <code> Y </code> for Yes - update it, and 
  - Press <code> Enter </code> to save.

<p> Now the phpmyAdmin configuration has been changed, Try to run the modules Update and Upgrade commands.

  ```
sudo apt update
sudo apt-get upgrade
```
We also restart the Apache server using 
  
```
sudo service apache2 restart
```

we can have other options for apache2 services, like to <code> Start </code>, <code> Stop </code>, <code> Restart </code>, <code> Reload </code>

once restart, try to browse the [/phpmyAdmin](ec2-18-191--us-east-2-compute-amazonaws.com/phpmyadmin/)

![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/ed285edc-c1c6-47ef-8ab4-39532d0bb392)

if you forget the user-name or password, use the command to check ;
```
sudo nano /etc/phpmyadmin/config-db.php
```
press Enter, and you will find all the information.

![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/ce4726fe-c90c-458f-ae13-580532e96524)

Now try to login into /phpmyadmin
![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/6aa47b14-3e04-4058-84cb-e1e192ce0ea3)

Now create a database, to check whether its working or having issue with the <code> Privileges </code>, like below 
![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/a9736eaf-85a4-4538-9a65-045f9639a748)

if the Privileges error coming, the goto the Terminal, and write the command <code> sudo mysql </code> press <b> Enter </b>. The path will selected of mysql directory.
Now run the privileges permission grant to the user, using below command

```
mysql> grant all on *.* to phpmyadmin@localhost; 
```
Now flush/restart the privileges; 
```
mysql> flush privileges;
```

then use the <code> exit; </code> command to return to the Ubuntu server main directory

![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/592f267d-af92-4ed8-ba19-6c4a969306de)

Now Logout and logIn again to the phpmyadmin dashboard, and you will find the Privileges would assigned, and the database will be able to create, like below;

![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/6e96e27d-b868-4adf-a434-19a09725af10)



</p>

  
### 5. Install the PHP Server
<p> PHP is Sript processing language. Its a component that process the code to display the dynamic content. It can Run scripts, content to the MySQL database to get information</p>

<p> For PHP installation, enter the below command , it will install all the PHP modules</p>

```
sudo apt install php libapache2-mod-php php-mbstring php-xmlrpc php-soap php-gd php-xml php-cli php-zip php-bcmath php-tokenizer php-json php-pear php-mysql php-gettext php-crul php-memcached php-xdebug php-intl php-fpm php-pgsql php imap 
```
- Press <code> Y </code> to install all the PHP modules.

Once the PHP installed, check it version using 
```
php -v
```

<p> Now the PHP is installed on the AWS server, let's Upload the LAravel Project, before uploading <b> Update </b> all the modules using <code> sudo apt-get update </code> and <b> restart </b> the Apache Server using <code> sudo service apache2 restart </code>

</p>

### 6. Deploy Laravel Project on Server
<p> We can upload the Laravel application to the aws server, using Two approaches; </p>
- Using GitHUB
- through Filezilla 

<p> We will use FileZilla ftp protocol approach.</p>
open the FileZilla applicaion.
- Under the File menu, select 'Site Manager'
- create new site and Enter the credientials
 - Protocol: SFTP - SSH File Transfer Protocol
 - Host: Ubuntu Public DNS address
 - Port: 22
 - Logon type: Key file
 - User: Ubuntu
 - Key file: Upload the Key file of Instance
 - Click 'Connect'
  
![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/5ae671dd-def3-4192-903b-c4755c1cb773)

<p> Once FTP server connected, Navigate to the web directory, have path root of <code> /Var/www/html </code>

  ![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/edff9638-d5d1-4267-b7f0-984de5f78d4e)

<p> The root file already the default index.html page, we need to delete this page. If you got the Error of <b>Permission denied</b> message, uon file deletion ,this occcurs because of Root Owner user will be Root, but our user-name is Ubuntu. 
  
![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/432341a0-2c2a-4a23-bd74-233ff14a41a1)

So we need to change the Owner name from 'root' to 'ubuntu'. The command to change the HTML directory ownership is as under; 
```
sudo chown -R ubuntu /var/www/html
```
-Pess Enter
- Refresh the FileZilla application, and the HTML directory Ownership will be changed, like as under;
  ![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/4904f99b-613d-4394-9e4a-0de4a35620d4)


Now try again to Delete the 'index.html' file from the HTML direcotry, and it will removed.
![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/d1afae01-2123-4d96-8970-5d88e24a741f)

It's time to uploade the LAravel project Zip file to the server using FileZilla. Drap the project zip file and drop under Filezilla, and it will uploaded;
![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/2b21e82f-2558-488c-9072-47a7d86f5bce)

We now need to Unzip the project folder, Goto the terminal and navigate to the HTML directory,;
- Navigate to main directory: <code> cd / </code>
- Enter to VAr directory: <code> cd var </code>
- Enter to www directory: <code> cd www </code>
- Enter to HTML directory: <code> cd html </code>
- Now Unzip the Project file, using command
  ```
  unzip projectfile.zip
  ```
![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/8b1e207b-e5f8-4894-9f7f-65553368177c)

Once Done, let browse the project using /public directory with url, like http://awsserverDNS/public

if it gave an Error of Storage permission, then navigatge to the Storage directory under the projet directory in FileZilla, right-click on Storage folder and Select the Permission to Addd the Write Permission for the Storage directory.
![image](https://github.com/prolinkz/LaravelonAWS-EC2/assets/45316278/9ea4c4b5-212c-45ee-addd-16578d996754)

Now goto Terminal , and run the command to change the 777 permission 
```
sudo chmod -R 777 storage
```

Again Refresh the Proect file in FileZilla, and browse the project page [serverDNS](/public)

</p>



</p>

