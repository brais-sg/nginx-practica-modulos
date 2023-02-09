# nginx-practica-modulos
Módulos adicionales para Nginx sobre Amazon EC2

# Bloqueo de direcciones IP
Para bloquear direcciones IP en Nginx debemos realizar lo siguiente:

1 - Nos dirigimos al archivo de configuración

![Archivo de configuración](/img/configuracion.png)

2 - En nuestro campo server, añadiremos un include hacia un fichero que será nuestra blacklist
```include /etc/nginx/blacklist.conf;```

3 - Ahora, debemos crear y modificar dicho fichero, para esto, usaremos el editor nano
```sudo nano /etc/nginx/blacklist.conf```

En este fichero, configuremos las reglas de acceso, por ejemplo
```conf
deny 192.168.1.0/24;
allow all;
```

Tras editar estas reglas, ahora debemos darle acceso al fichero al usurio desde el que se ejecuta el servidor
```sudo chown ec2-user /etc/nginx/blacklist.conf ```

Tras esto, reiniciamos el servicio de nginx y tendremos el bloqueo por IPs activo




