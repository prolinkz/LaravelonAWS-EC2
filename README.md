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
<p> When you run this, command, it will show some of the packages need to be installed and configured. Enter 'Y' for Yes, to continoue.</p>

<p> Once SQL Server is installed, we have set the Root Password, for which we use the below command;</p>
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



### 5. Install the PHP Server
<p> PHP is Sript processing language. Its a component that process the code to display the dynamic content. It can Run scripts, content to the MySQL database to get information</p>

<p> For PHP installation, enter the below command , it will install all the PHP modules</p>
```
sudo apt install php libapache2-mod-php php-mbstring php-xmlrpc php-soap php-gd php-xml php-cli
```




-  <code> cp .env.example </code> &nbsp; <code> .env </code>
- open: .env and update DB_DATABASE
- run: <code> composer install </code>
- run: <code> php artisan key:generate </code>
- run: <code> php artisan migrate:fresh --seed </code>  <a href="https://laravel.com/docs/10.x/migrations" alt="migration commands">migration commands </a>
- run: <code> php artisan serve </code>
