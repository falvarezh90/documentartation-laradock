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