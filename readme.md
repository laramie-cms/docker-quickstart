# Getting started

If you'd like to test Laramie out and have Docker for Mac or Windows installed, add the following `docker-compose.yml` file to the root of your Laravel / Laramie project and execute `docker-compose up`.

``` yaml
version: '3'
services:
  web:
    image: laramie:php
    command: php -S 0.0.0.0:8765 -t /var/www/web/public
    container_name: laramie
    ports:
      - "8765:8765"
    volumes:
      - ./:/var/www/web
    links:
      - db
  db:
    image: postgres:9.6
    container_name: laramie-postgres
    environment:
      - POSTGRES_USER=dev
      - POSTGRES_PASSWORD=123
    ports:
      - "5432"
```
