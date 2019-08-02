# Meu readme

## Como rodar
### Container MySql
1. Cria imagem MySql
`docker build -t mysql-demo-image -f api/db/Dockerfile .`

2. Cria container
`docker run -d --rm --name mysql-container mysql-demo-image`
--com volume (para não perder os dados), e com porta (para expor na minha máquina)
`docker run -d -v //c/projetos/docker-introducao/api/db/data://var/lib/mysql -p 3306:3306 --rm --name mysql-demo-container mysql-demo-image`

3. Verifica container
`docker ps`

4. Entra no MySql
`docker exec -it mysql-demo-container /bin/bash`
`mysql -uroot -pprogramadorabordo`

5. Cria BD
```
CREATE DATABASE IF NOT EXISTS programadorabordo;
USE programadorabordo;

CREATE TABLE IF NOT EXISTS products (
  id INT(11) AUTO_INCREMENT,
  name VARCHAR(255),
  price DECIMAL(10, 2),
  PRIMARY KEY (id)
);

INSERT INTO products VALUE(0, 'Curso Front-end especialista', 2500);
INSERT INTO products VALUE(0, 'Curso JS Fullstack', 900);

SELECT * from products;
```
6. Se quiser fazer pelo phpMyAdmin
`docker run --name phpmyadmin-container -d --link mysql-container:db -p 8080:80 phpmyadmin/phpmyadmin`