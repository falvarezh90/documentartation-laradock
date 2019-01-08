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

- service httpd stop (*service restarted with: ```$ service httpd start```*)
- service postgresql-11 stop (*service restarted with: ```$ service postgresql-11 start```*)

Run for second time ```docker-compose up```

```docker-compose up -d postgres pgadmin redis apache2 php-worker selenium jenkins laravel-echo-server elasticsearch workspace```

### 5 .- Enter to bash of Workspace

```docker-compose exec workspace bash```

### 6 .- Create a Laravel Project in ```/var/www``` (example with clone laravel project)  

```git clone https://gitlab.com/agroplastic/backend_agroplastic.git```

### 6 .- Config laravel project

- ```cd my_project/```
- ```composer install```
- ```cp .env_example .env```
- ```php artisan key:generate``` 
- Add this line to ```.env``` file: ```APP_CODE_PATH_HOST=../my_project```

Run other time ```docker-compose up``` (becouse edited ```.env```)

```docker-compose up -d postgres pgadmin redis apache2 php-worker selenium jenkins laravel-echo-server elasticsearch workspace```

### 7.- Enter to PGAdmin (Web Client)

- Enter in browser to ```http://localhost:5050```
- Login Credentials 
    - ```Username:  pgadmin4@pgadmin.org```
    - ```Password:  admin```
- In PGAdmin
    - Create server
        - ```name: postgres_docker```
        - ```host name/address: 172.17.0.1``` (you IP fro docker container)
        - ```user: default```
        - ```password: secret```

#### 7.1 Get IP for docker

Run this command in your machine CLI

```ipconfig```

And search docker network

![docker network](laradock-documentation/blob/master/README.md "Docker IP Network")

In this case, the IP of docker is ```172.17.0.1```


[Laradock Documentation](https://laradock.io/)