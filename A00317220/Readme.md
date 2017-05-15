
### Parcial 3 sistemas operativos

### Estudiantes: 
**Jorge Hernandez - A00317220**

**URL de github: //github.com/GeorgeArturo/so-exam3**

### Procedimiento

* Instrucciones para la configuración del cliente

Lo primero que se hizo para la instalación del cliente fue:

``` 
echo '[sensu]
name=sensu
baseurl=https://sensu.global.ssl.fastly.net/yum/$releasever/$basearch/
gpgcheck=0
enabled=1' | sudo tee /etc/yum.repos.d/sensu.repo

```

Luego se instalo sensu mediante los siguientes comandos:

```
yum install sensu -y
sensu-install -p sensu-plugin
```

El servicio del cliente se inicia mediante el siguiente comando:

```
service sensu-client start
```
El servicio de httpd se instalo mediante el siguiente comando

```
yum install httpd -y
```




* Instrucciones para la configuración del servidor
