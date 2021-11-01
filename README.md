<p align="center">
  <a href="https://github.com/othneildrew/Best-README-Template">
    <img width="946" alt="Ciberseguridad" src="https://user-images.githubusercontent.com/46871300/125079966-38ef8380-e092-11eb-9b5e-8bd0314d9274.PNG">
  </a>
 
   <h3 align="center">Implementacion de SOC con herramientas Open Source</h3>

  <p align="center">
    Proporcionamos los primeros pasos a los nuevos equipos de manejo de incidentes.
    <br />
    <a href="https://github.com/othneildrew/Best-README-Template"><strong>Explora la guia »</strong></a>
    <br />
    <br />
  </p>
</p>


----
### WazuhSIEM Overview!

Esta guía de configuración le mostrará cómo configurar su servidor WazuhSIEM, este proceso es simple de completar. En esta configuración usaremos un script para instalar nuestro WazuhSIEM desde cero.

-----------------------
Nota:
- Esta compilación se configuró en un XCP-ng 8.0 y las máquinas virtuales funcionan las 24 horas del día, los 7 días de la semana.
- Ahora, si desea utilizar ese proceso, esta guía de configuración sigue siendo la misma.

-----------------------


Estoy tratando de hacer este proceso simple y directo al grano. Para que pueda seguir y volver a crear la misma configuración que he creado.

## Referencias de recursos:


Que es Wazuh?
> https://documentation.wazuh.com/current/index.html

-----------------------

## Software Requerido

- Software de alojamiento

- Ubuntu Server 20.04 LTS **#Opccion 2:**
> https://ubuntu.com/download/server

- Descarga Directa:

> https://releases.ubuntu.com/20.04.3/ubuntu-20.04.3-live-server-amd64.iso

- El hipervisor que utiliza depende de usted, pero el proceso sigue siendo el mismo.
- Puede utilizar Linux o Windows para la instalación del hipervisor base.

-----------------------
- VirtualBox para instalaciones de Windows o Linux

- Oracle VirtualBox 6.1.16 
> https://www.virtualbox.org/wiki/Downloads

- Oracle VirtualBox Paquete de extensión para invitados
> https://download.virtualbox.org/virtualbox/6.1.16/Oracle_VM_VirtualBox_Extension_Pack-6.1.16.vbox-extpack

-----------------------
- VMware para instalaciones de Windows o Linux

- VMware Workstation 16.1.0 Player Free 
> https://my.vmware.com/en/web/vmware/downloads/details?downloadGroup=PLAYER-1610&productId=1039&rPId=55792

Estos dos son opcionales a continuación.
Necesitará hardware físico para instalar.

- XCP-ng
> https://mirrors.xcp-ng.org/isos/8.2/xcp-ng-8.2.0.iso?https=1


## Módulo de instalación de Wazuh

- Wazuh Overview!

Wazuh proporciona una solución de seguridad capaz de monitorear su infraestructura, detectar amenazas, intentos de intrusión, anomalías del sistema, aplicaciones mal configuradas y acciones de usuarios no autorizados. También proporciona un marco para la respuesta a incidentes y el cumplimiento normativo.

- Fuente:

> https://wazuh.com/product/


## Instalacion de Wazuh Server & Agent!

Esta será una implementación de nodo único de **Wazuh.**

#### All-in-one deployment

> https://documentation.wazuh.com/current/installation-guide/open-distro/all-in-one-deployment/index.html#all-in-one-index


![](https://github.com/watsoninfosec/WazuhSIEM/blob/main/Deployment/images/overview.png)


Primero, tomemos el archivo de configuración que necesitaremos Instalar **Wazuh**.

Nota: Se requieren privilegios de usuario root para ejecutar todos los comandos que se describen a continuación. Para descargar el script se utilizará el paquete ** curl **.

- Obtenga acceso root:

~~~
sudo su
~~~

- Instalacion de Wazuh:

~~~
curl -so ~/all-in-one-installation.sh https://raw.githubusercontent.com/wazuh/wazuh-documentation/4.1/resources/elastic-stack/unattended-installation/all-in-one-installation.sh && bash ~/all-in-one-installation.sh
~~~

Ahora bien, este proceso en un **Unattended installation**

- Una vez que ese script se esté ejecutando, debería ver algo como esto:

### Wazuh Server Salida:

~~~
 The password for wazuh is vhDpq7YcwA08BLTmcdeYeJmXPU_VD31f

 The password for admin is uLo9SBKCE80B8OSE8zNbOWlVvHlOjQ00

 The password for kibanaserver is -A452dUzB8gnk3ed7nSuci_kNiSZ0y6z

 The password for kibanaro is yyNBlV28VzJHKnYVPNLgoAEssgics9d4

 The password for logstash is Hm86wUT7paLDPNhtq-I6Q1H8Weh7tX-g

 The password for readall is ZDqyYqvV5moE60k_X5580-4US6CIjBmi

 The password for snapshotrestore is FCHX-YhCV_o6IE8x_AA6lFQsjzlmCVe7

 The password for wazuh_admin is rkDgTQEnyw8Li3hYXfhD9td-voCw1awm

 The password for wazuh_user is _9JE9cY2nMWdR5GRb_Gda8ikrRRvsASH

 Checking the installation...
 Elasticsearch installation succeeded.
 Filebeat installation succeeded.
 Initializing Kibana (this may take a while)
 .
 Installation finished

 You can access the web interface https://<kibana_ip>. The credentials are wazuh:vhDpq7YcwA08BLTmcdeYeJmXPU_VD31f
 ~~~

Ahora copie estas contraseñas de arriba y guárdelas, las necesitará para obtener acceso al panel del servidor.

- Ahora puede acceder a su panel de control desde la dirección IP que creó:

~~~
Puede acceder a la interfaz web https://<kibana_ip>.
~~~

- Ves una advertencia como esta:

![](https://github.com/watsoninfosec/WazuhSIEM/blob/main/Deployment/images/warning.png)

Acepte la advertencia haciendo clic en Avanzado, luego Acepte el Riesgo y continúe a la pantalla de inicio de sesión.

### Pantalla de ingreso al sistema:
![](https://github.com/watsoninfosec/WazuhSIEM/blob/main/Deployment/images/elastic.png)

- Now login in with your **elastic** username and password: **v3gJLYItKkxuYmunES5T**

### Wazuh Dashboard:
![](https://github.com/watsoninfosec/WazuhSIEM/blob/main/Deployment/images/wazuh.png)

### Listo!

Ahora tiene su nuevo **Wazuh Server** configurado y en funcionamiento.
Tómate un tiempo para explorar y echar un vistazo a tu nuevo **WazuhSIEM.**

## MISP Threat Sharing

- MISP Overview!

MISP es una solución de software de código abierto para recopilar, almacenar, distribuir y compartir indicadores de ciberseguridad y amenazas sobre el análisis de incidentes de ciberseguridad y el análisis de malware. MISP está diseñado por y para analistas de incidentes, profesionales de la seguridad y las TIC o reversores de malware para respaldar sus operaciones diarias para compartir información estructurada de manera eficiente.

- Source:

> https://www.circl.lu/services/misp-malware-information-sharing-platform/


## Instalando MISP!

~~~
sudo apt-get update -y && sudo apt-get upgrade -y
sudo apt-get install mysql-client  -y
wget https://raw.githubusercontent.com/MISP/MISP/2.4/INSTALL/INSTALL.sh
chmod +x INSTALL.sh
./INSTALL.sh -A
~~~

~~~
Puede acceder a la interfaz web https://<misp_ip>.
~~~

- Ves una advertencia como esta:

![](https://github.com/watsoninfosec/WazuhSIEM/blob/main/Deployment/images/warning.png)

Acepte la advertencia haciendo clic en Avanzado, luego Acepte el Riesgo y continúe a la pantalla de inicio de sesión.

### Pantalla de ingreso al sistema:
![e83ca3e2-9b9f-4e7e-8266-2f15311fbee6](https://user-images.githubusercontent.com/87453279/133007437-06d62d36-4bad-4982-a9e6-a3d2afca7960.png)

- Now login in with your default credentials **admin@admin.test** username and password: **admin**

### Listo!

Ahora tiene su nuevo **MISP Server** configurado y en funcionamiento.
Tómate un tiempo para explorar y echar un vistazo a tu nuevo **MISP Server.**

## TheHive

- TheHive Overview!

MISP es una solución de software de código abierto para recopilar, almacenar, distribuir y compartir indicadores de ciberseguridad y amenazas sobre el análisis de incidentes de ciberseguridad y el análisis de malware. MISP está diseñado por y para analistas de incidentes, profesionales de la seguridad y las TIC o reversores de malware para respaldar sus operaciones diarias para compartir información estructurada de manera eficiente.

~~~
sudo apt-get install -y openjdk-8-jre-headless
sudo echo JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64" >> /etc/environment
sudo export JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64"
curl -fsSL https://www.apache.org/dist/cassandra/KEYS | sudo apt-key add -
echo "deb http://www.apache.org/dist/cassandra/debian 311x main" | sudo tee -a /etc/apt/sources.list.d/cassandra.sources.list
sudo apt update -y
sudo apt install cassandra -y
~~~

~~~
UPDATE system.local SET cluster_name = 'thp' where key='local';
exit
~~~

~~~
nodetool flush
~~~

~~~
cluster_name: 'thp'
listen_address: 'localhost' # address for nodes
rpc_address: 'localhost' # address for clients
seed_provider:
    - class_name: org.apache.cassandra.locator.SimpleSeedProvider
      parameters:
          - seeds: 'localhost' # self for the first node
data_file_directories:
  - '/var/lib/cassandra/data'
commitlog_directory: '/var/lib/cassandra/commitlog'
saved_caches_directory: '/var/lib/cassandra/saved_caches'
hints_directory: '/var/lib/cassandra/hints'
~~~

~~~
sudo systemctl start cassandra
sudo systemctl enable cassandra
sudo mkdir -p /opt/thp_data/files/thehive
sudo chown -R thehive:thehive /opt/thp_data/files/thehive
~~~

~~~
netstat -an | grep 7000
~~~

~~~
curl https://raw.githubusercontent.com/TheHive-Project/TheHive/master/PGP-PUBLIC-KEY | sudo apt-key add -
echo 'deb https://deb.thehive-project.org beta main' | sudo tee -a /etc/apt/sources.list.d/thehive-project.list
sudo apt-get update
sudo apt-get install thehive4 -y
~~~

~~~
db.janusgraph {
  storage {
    backend: cql
    hostname: ["127.0.0.1"]
    cql {
      cluster-name: thp
      keyspace: thehive
    }
  }
}
~~~

~~~
storage {
  provider: localfs
  localfs.directory: /opt/thp_data/files/thehive
}
~~~

~~~
systemctl start thehive
~~~

~~~
systemctl enable thehive
~~~


![thehive](https://user-images.githubusercontent.com/87453279/133007558-0d962857-5244-494f-a46c-66798ed16a73.png)


## Cortex

- Cortex Overview!

MISP es una solución de software de código abierto para recopilar, almacenar, distribuir y compartir indicadores de ciberseguridad y amenazas sobre el análisis de incidentes de ciberseguridad y el análisis de malware. MISP está diseñado por y para analistas de incidentes, profesionales de la seguridad y las TIC o reversores de malware para respaldar sus operaciones diarias para compartir información estructurada de manera eficiente.

~~~
curl https://raw.githubusercontent.com/TheHive-Project/TheHive/master/PGP-PUBLIC-KEY | sudo apt-key add -
echo 'deb https://deb.thehive-project.org release main' | sudo tee -a /etc/apt/sources.list.d/thehive-project.list
sudo apt-get update
~~~

~~~
apt install cortex
~~~

~~~
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
~~~

~~~
sudo apt install apt-transport-https
~~~

~~~
sudo apt update && sudo apt install elasticsearch
~~~

~~~
sudo add-apt-repository ppa:openjdk-r/ppa
sudo apt-get update
sudo apt-get install openjdk-11-jre-headless
~~~

~~~
sudo addgroup cortex
sudo adduser --system cortex
sudo cp /opt/cortex/package/cortex.service /usr/lib/systemd/system
sudo chown -R cortex:cortex /opt/cortex
sudo chgrp cortex /etc/cortex/application.conf
sudo chmod 640 /etc/cortex/application.conf
sudo systemctl enable cortex
sudo service cortex start
~~~

~~~
sudo mkdir /etc/cortex
(cat << _EOF_
# Secret key
# ~~~~~
# The secret key is used to secure cryptographics functions.
# If you deploy your application to several instances be sure to use the same key!
play.http.secret.key="$(cat /dev/urandom | tr -dc 'a-zA-Z0-9' | fold -w 64 | head -n 1)"
_EOF_
) | sudo tee -a /etc/cortex/application.conf
~~~

~~~
bin/cortex -Dconfig.file=/etc/cortex/application.conf
~~~

~~~
sudo apt-get install -y --no-install-recommends python-pip python2.7-dev python3-pip python3-dev ssdeep libfuzzy-dev libfuzzy2 libimage-exiftool-perl libmagic1 build-essential git libssl-dev
~~~

~~~
sudo pip install -U pip setuptools && sudo pip3 install -U pip setuptools
~~~

~~~
git clone https://github.com/TheHive-Project/Cortex-Analyzers
~~~

~~~
for I in $(find Cortex-Analyzers -name 'requirements.txt'); do sudo -H pip2 install -r $I; done && \
for I in $(find Cortex-Analyzers -name 'requirements.txt'); do sudo -H pip3 install -r $I || true; done
~~~

~~~
analyzer {
  # Directory that holds analyzers
  path = [
    "/path/to/default/analyzers",
    "/path/to/my/own/analyzers"
  ]

  fork-join-executor {
    # Min number of threads available for analyze
    parallelism-min = 2
    # Parallelism (threads) ... ceil(available processors * factor)
    parallelism-factor = 2.0
    # Max number of threads available for analyze
    parallelism-max = 4
  }
}

responder {
  # Directory that holds responders
  path = [
    "/path/to/default/responder",
    "/path/to/my/own/responder"
  ]

  fork-join-executor {
    # Min number of threads available for analyze
    parallelism-min = 2
    # Parallelism (threads) ... ceil(available processors * factor)
    parallelism-factor = 2.0
    # Max number of threads available for analyze
    parallelism-max = 4
  }
}
~~~

![cortex](https://user-images.githubusercontent.com/87453279/133007557-ccc79e8e-653a-4016-81a9-4d94c3709f57.png)

![analizer](https://user-images.githubusercontent.com/87453279/133007556-4c6ae266-75f2-44b7-bd82-39e5e1188446.png)



## Patrowl

- Patrowl Overview!

----

PatrOwl es una solución escalable, gratuita y de código abierto para orquestar operaciones de seguridad.

**PatrowlManager** es la aplicación Front-end para administrar los activos, revisar los riesgos en tiempo real, orquestar las operaciones (escaneos, búsquedas, llamadas a API, ...), agregar los resultados, transmitir alertas a terceros (p. Ej., Plataforma de respuesta a incidentes). como TheHive, SIEM, ...) y proporcionando los informes y cuadros de mando.
**PatrowlEngines** es el marco del motor y la lista admitida de motores que realizan las operaciones (escaneos, búsquedas, llamadas a API, ...) a su debido tiempo.

----

## Hardware Pre-requisitos
Patrowl Manager usa PostgreSQL para almacenar datos. Recomendamos utilizar una máquina virtual con al menos 4 vCPU, 8 GB de RAM y 60 GB de disco. También puede utilizar una máquina física con especificaciones similares.

### Instalar e implementar Backend desde Docker
#### 1. Instalar los requisitos previos del sistema
Instalacion de Docker:
+ [Docker and Docker-Compose](https://docs.docker.com/install/)

#### 2. Descarga PatrowlManager de GitHub
```
git clone https://github.com/Patrowl/PatrowlManager.git
```
#### 3. Implemente el backend usando docker-compose
```
cd PatrowlManager
docker-compose build --force-rm
docker-compose up
```
> Nota 1: El volumen persistente no está establecido en la configuración de base de datos predeterminada. Actívelo si es necesario (¡debería serlo!). Ajústelo en el archivo `docker-compose.yml`

> Nota 2: ¿Quieres motores preconfigurados? Ejecute `docker-compose -f docker-compose.with-engines.yml up` en su lugar   

#### 4. Use esto:

> Ir a http://ip_patrowl:8083/ e iniciar sesión con las credenciales de administrador predeterminadas: **admin/Bonjour1!**


![patrowl](https://user-images.githubusercontent.com/87453279/133007771-932a9d19-c45a-4ce5-89ad-65aaa2502946.png)


### 5. Desplegar algunos de los engines

```
docker run -d -p 5005:5005 --name="arachni-docker-001" patrowl-arachni
```
```
docker run -d -p 5009:5009 --name="cortex-docker-002" patrowl-cortex
```
```
docker run -d -p 5021:5021 --name="droopescan-docker-003" patrowl-droopescan
```
```
docker run -d -p 5018:5018 --name="eyewitness-docker-004" patrowl-eyewitness
```
```
docker run -d -p 5001:5001 --name="nmap-docker-005" patrowl-nmap
```
```
docker run -d -p 5004:5004 --name="ssllabs-docker-006" patrowl-ssllabs
```
```
docker run -d -p 5014:5014 --name="sslscan-docker-007" patrowl-sslscan
```
```
docker run -d -p 5008:5008 --name="urlvoid-docker-008" patrowl-urlvoid
```
```
docker run -d -p 5022:5022 --name="apivoid-docker-009" patrowl-apivoid
```
```
docker run -d -p 5017:5017 --name="certstream-docker-010" patrowl-certstream
```

![engines](https://user-images.githubusercontent.com/87453279/133007778-98dd7ceb-82c2-47bd-b008-1135f0bb9cd6.png)

---

### Orquestacion!

Esta guía de configuración le mostrará cómo configurar su servidor WazuhSIEM, este proceso es simple de completar. En esta configuración usaremos un script para instalar nuestro WazuhSIEM desde cero.

-----------------------

## integracion de Wazuh & TheHive 
This project integrates SIEM Wazuh and TheHive. Use the following instructions to configure:
 
```sh
cd /opt/
git clone https://github.com/crow1011/wazuh2thehive.git
/var/ossec/framework/python/bin/pip3 install -r /opt/wazuh2thehive/requirements.txt
cp /opt/wazuh2thehive/custom-w2thive.py /var/ossec/integrations/custom-w2thive.py
/opt/wazuh2thehive/custom-w2thive /var/ossec/integrations/custom-w2thive
chmod 755 /var/ossec/integrations/custom-w2thive.py
chmod 755 /var/ossec/integrations/custom-w2thive
chown root:ossec /var/ossec/integrations/custom-w2thive.py
chown root:ossec /var/ossec/integrations/custom-w2thive
nano /var/ossec/etc/ossec.conf


```
inserte el siguiente fragmento en el bloque ossec_config:
```xml
<integration>
    <name>custom-w2thive</name>
    <hook_url>http://localhost:9000</hook_url>
    <api_key>123456790</api_key>
    <alert_format>json</alert_format>
</integration>
```
Descripción de líneas:

**name** - integration name(no need to change)

**hook_url** - TheHive host

**api\_key** - TheHive user's API key. You can generate the key on the user management page by logging in as administrator. For security, allow the api-user to create only an alert.

**alert\_format** - format that wazuh sends alert to the integrator(no need to change)

after configuration, apply the changes with this command:
```sh
/var/ossec/bin/ossec-control restart
```
Finally, check the /var/ossec/log/integrations.log file for errors. If there is not enough information from the errors, you can enable debug_mode by changing the line in the file custom-w2thive.py 
```python
debug_enabled = False
```
to 
```python
debug_enabled = True
```
If you receive too many events, you can set a severity threshold for events that will be send to TheHive. Set the value of the lvl_threshold variable in the file /var/ossec/integrations/custom-w2thive.py
```python
lvl_threshold = 0
```
Events with a severity level equal to or greater will be sent to TheHive. You can read more about event classification in Wazuh here: [wazuh-rules-classification](https://documentation.wazuh.com/current/user-manual/ruleset/rules-classification.html)
