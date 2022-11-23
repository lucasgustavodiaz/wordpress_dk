# Instrucciones adicionales

Bajar la ultima version de wordpress y descomprimirla en la carpeta wordpress en la raiz

Para inicializar utilizar el comando:

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

En la carpeta nginx dentro de cert ejecutar

```
mkcert wordpress.test
```

## Plugins

Permite instalar y actualizar plugin sin FTP. agregar a wp-config.php

```php
define('FS_METHOD', 'direct');
```
