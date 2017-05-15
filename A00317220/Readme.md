
### Parcial 3 sistemas operativos

### Estudiantes: 
**Jorge Hernandez - A00317220**

**URL de github: //github.com/GeorgeArturo/so-exam3**

### Procedimiento

* Instrucciones para la configuración del cliente

lo primero que se hizo para la instalación del cliente fue:

``` python
echo '[sensu]
name=sensu
baseurl=https://sensu.global.ssl.fastly.net/yum/$releasever/$basearch/
gpgcheck=0
enabled=1' | sudo tee /etc/yum.repos.d/sensu.repo

```

* Instrucciones para la configuración del servidor
