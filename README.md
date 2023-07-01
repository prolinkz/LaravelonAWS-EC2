# LaravelonAWS-EC2
Deploy Laravel application on EC2 Ubuntu Server with Apache, MySQL, PHP, PHPMyAdmin, and zip/unzip

<p align="center">
  [GitHUB Text Formatting](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

## How To Run Laravel application on AWS - Ubuntu Server

Deploy Laravel application on EC2 Ubuntu Server with Apache, MySQL, PHP, PHPMyAdmin, and zip/unzip


### How to Run the composer Command Code

- Ope AWS page, and navigate to >> Select services >> EC2 >> select Running Instances
-  Clic on <code>Launch New Instance</code>
-   Step 1: Amazon Machine : select Ubuntu of your range
-   Step 2: Instane Type: Select
-   Step 3: Add Storage of your range from
-   Step 4:
-   Step 5:
-   Step 6:
-   Step 7: Key Pair: Create New piar for each Instance and download it in .ppk file extionsion. If you downloaded in .pem file format, it will be then convert into .ppk extension using "PUTTY gen" application.
-   Final Step: Select "Launch Instance". 
- [Enter project directory] <code> cd project-folder </code>
-  <code> cp .env.example </code> &nbsp; <code> .env </code>
- open: .env and update DB_DATABASE
- run: <code> composer install </code>
- run: <code> php artisan key:generate </code>
- run: <code> php artisan migrate:fresh --seed </code>  <a href="https://laravel.com/docs/10.x/migrations" alt="migration commands">migration commands </a>
- run: <code> php artisan serve </code>
