# Docker para pruebas de desarrollo de modo local

Este proyecto permite ejecutar uns instancia de docker donde la base de dato y wordpress son persistentes en la computadora local.

## Instrucciones adicionales

Bajar la ultima version de wordpress y descomprimirla en la carpeta wordpress en la raiz.

Para inicializar la instancia de docker es necesario docker desktop 

Utilizar el comando:

```
docker-compose up -d --build
```

Levantar servicios:

```
docker-compose up
```

Parar los servicios

```
docker-compose down
```

## Certificados

Primero instalar mkcert en tu computadora

```
scoop bucket add extras
scoop install mkcert
```

mkcert es una herramienta sencilla para crear certificados de desarrollo de confianza local. No requiere configuración

```
mkcert -install
```
Created a new local CA 💥
The local CA is now installed in the system trust store! ⚡️
The local CA is now installed in the Firefox trust store (requires browser restart)! 🦊

En la carpeta nginx dentro de cert ejecutar es importante general el alis del localhost a wordpress.test en el archivo HOST de windows ubicado en la carpeta C:\Windows\System32\drivers\etc
Ejemplo: 127.0.0.1       wordpress.test

```
mkcert wordpress.test
```

Ejemplos de como usar mkcert

$ mkcert example.com "*.example.com" example.test localhost 127.0.0.1 ::1

Created a new certificate valid for the following names 📜
 - "example.com"
 - "*.example.com"
 - "example.test"
 - "localhost"
 - "127.0.0.1"
 - "::1"

The certificate is at "./example.com+5.pem" and the key at "./example.com+5-key.pem" ✅

## Configuración de wordpress

Una vez ingresado a localhost

```php
/** The name of the database for WordPress */
define( 'DB_NAME', 'wp' );

/** Database username */
define( 'DB_USER', 'wp' );

/** Database password */
define( 'DB_PASSWORD', 'secret' );

/** Database hostname */
define( 'DB_HOST', 'mysql' );
```

## Plugins

Permite instalar y actualizar plugin sin FTP. agregar a wp-config.php

```php
define('FS_METHOD', 'direct');
```
