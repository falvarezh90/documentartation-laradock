# Laradock Documentation

## Installing laradock

### 1.- Clone the project

```git clone https://github.com/Laradock/laradock.git```

### 2.- Enter to laradock folder and rename ```env-example``` to ```.env```

```cp env-example .env ```

### 3.- Run your containers

In this case, we will install the next tools of Laradock:

- postgres
- pgadmin
- redis
- apache2
- php-worket
- selenium
- jenkins
- laravel-echo-server
- elasticsearch
- workspace (different tools for development, for example, ```composer```, ```vim```, ```npm```, etc )

```docker-compose up -d postgres pgadmin redis apache2 php-worker selenium jenkins laravel-echo-server elasticsearch workspace```

### 4 .- Port errors

Close containers

```docker-compose down```

After, you must stop services Apache and PostgreSQL in main machine (example with fedora S.O.)

- ```service httpd stop``` (*service restarted with: ```$ service httpd start```*)
- ```service postgresql-11 stop``` (*service restarted with: ```$ service postgresql-11 start```*)

Run for second time ```docker-compose up```

```docker-compose up -d postgres pgadmin redis apache2 php-worker selenium jenkins laravel-echo-server elasticsearch workspace```

### 5 .- Enter to bash of Workspace

```docker-compose exec workspace bash```

### 6 .- Create a Laravel Project in ```/var/www``` (example with clone laravel project)  

```git clone https://gitlab.com/agroplastic/backend_agroplastic.git```

### 7 .- Config laravel project

- ```cd my_project/```
- ```composer install```
- ```cp .env_example .env```
- ```php artisan key:generate``` 
- Add this line to ```.env``` file: ```APP_CODE_PATH_HOST=../my_project```

Run other time ```docker-compose up``` (because edited ```.env```)

```docker-compose up -d postgres pgadmin redis apache2 php-worker selenium jenkins laravel-echo-server elasticsearch workspace```

### 8.- Enter to PGAdmin (Web Client)

- Enter in browser to ```http://localhost:5050```
- Login Credentials 
    - ```Username:  pgadmin4@pgadmin.org```
    - ```Password:  admin```
- In PGAdmin
    - Create server
        - ```name: postgres_docker```
        - ```host name/address: 172.17.0.1``` (your IP for docker container)
        - ```user: default```
        - ```password: secret```
    - Create DB (in ```postgres_socker``` server)

#### 8.1 Get IP for docker

Run this command in your machine Shell

```ipconfig```

And search docker network

![docker network](https://github.com/falvarezh90/laradock-documentation/blob/master/src/IP-docker.png "Docker IP Network")

In this case, the IP of docker is ```172.17.0.1```

#### 8.2 Config Postgres Binary Path in PGAdmin (optional)

- Enter to ```File > Preferences > Path > Binary paths```
- Added path ```/usr/local/bin/``` in PostgresSQL Binary Path

Now is ready for use Backup of DB 

### 9.- Config Postgres Connection in your```.env``` file of your laravel project 

```
DB_CONNECTION=pgsql
DB_HOST=172.17.0.1
DB_PORT=5432
DB_DATABASE=example
DB_USERNAME=default
DB_PASSWORD=secret
```

### 10.- Re-run ```Apache``` and ```Workspace``` containers


[Laradock Documentation](https://laradock.io/)

```docker-compose up -d postgres pgadmin redis apache2 php-worker selenium jenkins laravel-echo-server elasticsearch workspace```