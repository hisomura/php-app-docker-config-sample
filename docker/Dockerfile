version: "3.4"
services:

  db:
    container_name: db
    image: mysql:5.6
    entrypoint: docker-entrypoint.sh --character-set-server=utf8mb4 --collation-server=utf8mb4_general_ci
    environment:
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: sample
      MYSQL_USER: sample
      MYSQL_PASSWORD: sample
    ports:
      - "3306:3306"
    volumes:
      - './data/db:/var/lib/mysql'

  web:
    build: ./configs/web
    container_name: web
    ports:
      - "80:80"
    volumes:
      - './test:/var/www/html'
