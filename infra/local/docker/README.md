# Instalación de Infraestructura

## Docker

Copiar `dist.env` a `.env` y modificar los valores necesarios.
```
cp dist.env .env
```

Hacer build de los contenedores
```
docker-compose build --pull
```

Levantar los contenedores
```
docker-compose up -d
```

Agregar entrada al /etc/hosts
```
127.0.0.1 blog.loc
```


Configurar base de datos
```
docker exec -it blog-db mysql -e "CREATE DATABASE blog"
docker exec -it blog-db mysql -e "GRANT ALL ON blog.* TO 'blog'@'%' IDENTIFIED BY 'blog'"
```

Instalar vendor y configuración
```
docker exec -it blog-php bash
cd /home/app
composer install
```

Probar: http://blog.loc
