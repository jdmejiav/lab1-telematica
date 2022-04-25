# lab1-telematica


Para el despligue del sitio web con certificado SSL y docker, lo que hice fue desplegar el sitio web con docker en el puerto 8080 e instalar y configurar nginx en local para que redirigiera todo el tráfico http y https a ese puerto, para hacer esto:


## Pasos

### 1.
Necesité adquirir un dominio en Freenom, el cuál fue: <a href="jdmejiav.tk">jdmejiav.tk</a> 

### 2.
Para activar el certificado.

      sudo certbot --nginx -d jdmejiav.tk
      
### 3.
crear un archivo para la configuración del sitio con el nombre del dominio

      touch /etc/nginx/sites-available/jdmejiav.tk
      
### 4.
Pegar el contenido que está en el archivo <a href="https://github.com/jdmejiav/lab1-telematica/blob/master/jdmejiav.tk">jdmejiav.tk</a> que contiene la configuración del sitio, en el archivo se especifica la dirección del certificado SSL, se redirecciona al puerto 8080 y se establecen los headers del proxy

### 5.
Hay que establecer un link simbólico entre los archivos en la carpeta /etc/nginx/sited-available y los que estan en la carpeta /etc/nginx/sited-enabled

      sudo ln -s /etc/nginx/sited-available/jdmejiav.tk /etc/nginx/sited-enabled/jdmejiav.tk
      
### 6.
Reiniciar el servicio de nginx para actualizar los cambios en la configuración.

      sudo systemctl restart nginx

## Ver resultado
Para visital la página desplegada, la URL es <a href="jdmejiav.tk">jdmejiav.tk</a>.
