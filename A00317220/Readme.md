
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

* Para la parte de la configuración de rabbitmq se hizo lo siguiente 

```
cd /etc/sensu/conf.d
```
Una vez aqui se creo un archivo tipo json (client.json) con la siguiente información

```
{
  "client": {
    "name": "A00317220",
    "address": "192.168.57.4",
    "subscriptions": ["webservers"]
  }
}

```

Luego se creo otro archivo tipo json (rabbitmq.json) con la siguiente información:

```
{
  "rabbitmq": {
    "host": "192.168.57.3",
    "port": 5672,
    "vhost": "/sensu",
    "user": "sensu",
    "password": "password",
    "heartbeat": 10,
    "prefetch": 50
  }
}

```

Finalmente se instalaron algunos plugins para el correcto funcionamiento, para esto lo que se hizo fue:

```
cd /etc/sensu/plugins
```

una vez en esta direccion se creo un archivo ruby (check-apache.rb) con la siguiente información

```
#!/usr/bin/env ruby

procs = `ps aux`
running = false
procs.each_line do |proc|
  running = true if proc.include?('httpd')
end
if running
  puts 'OK - Apache daemon is running'
  exit 0
else
  puts 'WARNING - Apache daemon is NOT running'
  exit 1
end

```

* Instrucciones para la configuración del servidor
