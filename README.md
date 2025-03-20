This repository provides a guide on configuring Docker to run Laravel with Vue.js and PostgreSQL. It also includes a setup for a PgAdmin4 container to manage the PostgreSQL database.

# CONFIGURE PROJECT
-Step 1: Create Laravel Project
$ composer create-project --prefer-dist laravel/laravel docker-vue-laravel-postgres

-Step 2: Move into the project folder
$ cd docker-vue-laravel-postgres

-Step 3: Install Laravel Breeze (modern Vue setup)
$ composer require laravel/breeze --dev
$ php artisan breeze:install vue

-Step 4: Install JavaScript dependencies
$ npm install

-Step 5: Start the development server
$ npm run dev



# Modify the following files to configure Docker and networking:
$ docker-compose.yml
$ Dockerfile
$ docker/nginx/site.conf

# Vite Configuration:
$ vite.config.js


# Database Configuration:
$ .env  (file)



# Running the Docker Environment
Step 1: Stop Any Existing PostgreSQL Service
If you have PostgreSQL running locally, stop it to avoid conflicts:
$ systemctl stop postgresql.service

Step 2: Build and Start Docker Containers
$ docker-compose up --build -d

Step 3: Check Running Containers
$ docker ps
Laravel_nginx
Laravel_postgres
Laravel_postgres
Laravel_php
Laravel_vite


Step 4: Access the PHP Container
To install dependencies inside the container:
$ docker exec -it Laravel_php /bin/sh
       -> $ composer install
Step 5: Run Migrations
Inside the container, run:

$ php artisan migrate


# Access the Application
Open your browser and visit:
http://localhost:8001/



# Starting and Stopping Docker Containers

$  sudo docker-compose start
$  sudo docker-compose stop


# Troubleshooting
Restart the containers if necessary:

$ docker-compose down
$ docker-compose up --build -d
