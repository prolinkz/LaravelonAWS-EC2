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
Once done, check the Instance Status, if it work fine, you will find the _Public IP_, _Privete IP_, _Public DNS_, and the _Key Pair file_
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

```
- sudo apt-get update
- sudo apt-get upgrade
```

-  <code> cp .env.example </code> &nbsp; <code> .env </code>
- open: .env and update DB_DATABASE
- run: <code> composer install </code>
- run: <code> php artisan key:generate </code>
- run: <code> php artisan migrate:fresh --seed </code>  <a href="https://laravel.com/docs/10.x/migrations" alt="migration commands">migration commands </a>
- run: <code> php artisan serve </code>
