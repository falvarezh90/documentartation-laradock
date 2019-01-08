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

### 4 .- If you have errors with installations for Port errors of tools containers, you need edit ```docker-compose.yml``` file. For example, if you hace problems with PostgresQL and Apache2

Postgres:

- Change ```"${POSTGRES_PORT}:5432"``` to ```"${POSTGRES_PORT}:5433"```

Apache2:

- Change ```"${APACHE_HOST_HTTP_PORT}:80"``` to ```"${POSTGRES_PORT}:5433"```
- Change ```"${APACHE_HOST_HTTPS_PORT}:443"``` to ```"${APACHE_HOST_HTTPS_PORT}:444"```



