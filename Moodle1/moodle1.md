# Guia d'instalació Moodle

## Abans de començar:
Abans de començar amb l'instal·lació del Moodle, hem d'instal·lar unes eines.
Necesitarem:
- Ubuntu server amb ssh
- apache2
- unzip
- MariaDB

### Ubuntu server amb ssh
A l'instal·lació del Ubuntu server, haurem d'instal·lar el servei "ssh"

![](Fotos/instalacio_ssh.png)

### Instalació unzip
Descarregarem l'eina "unzip" per descomprimir un arxiu que veurem més endavant.
```sh
sudo apt install unzip
```
![](Fotos/install_unzip.png)

### Instalació apache2
Un cop tenim la màquina virtual creada, ens descarregarem el
"apache2"
```sh
sudo apt install apache2
```
![](Fotos/install_apache2.png)

### Instalació MariaDB
Ara descarregarem la base de dades "MariaDB" amb la següent comanda:
```sh
sudo apt-get install mariadb-server
```
![](Fotos/install_mariadb.png)

Seguidament, executarem la seguretat del servidor MariaDB i la configurarem.
```sh
sudo apt-get install mariadb-server
```
![](Fotos/mysql_secure.png)

![](Fotos/mysql_secure_2.png)

### Instalació PHP
I per últim descarregarem el PHP, el meu cas he descarregat la versió 7.3, ja que és la compatible amb la versió de Moodle que jo tinc.
```sh
sudo apt-get install php7.3 -y
```
```sh
sudo apt install libapache2-mod-php7.3
```
Un cop el tenim instal·lat reiniciarem el servei "apache2" perquè es desin tots els canvis.
```sh
sudo service apache2 restart
```
Ara comprovarem si el servei "apache2" funciona correctament amb la seguent comanda:
```sh
sudo service apache2 status
```
![](Fotos/apache2_status.png)

### Instalació Moodle
Un cop ja tenim totes aquestes eines, ens dirigirem a moodle.org, a l'apartat de "Downloads"

![](Fotos/pagina_moodle.png)

Ens descargarem la ultima versio disponible, la 4.0.5.

![](Fotos/moodle_1.png)

Se'ns baixara un document automàticament, però només ens interessa l'enllaç de la baixada. Ens sortirà un missatge on ens indica que si no s'ens ha baixat res fes clic a aquest enllaç i torneu a provar, però nosaltres farem clic dret a sobre d'aquest enllaç i el copiarem.

![](Fotos/moodle_2.png)

Un cop hem obtingut l'enllaç de la descarrega, obrirem la màquina virtual i executarem la seguent comanda amb el link:
 ```sh
wget https://download.moodle.org/download.php/stable400/moodle-latest-400.zip
```

Descomprimirem l'arxiu zip i el rediccionarem al directori /var/www/html/
 ```sh
sudo unzip moodle-latest-400.zip -d /var/www/html/
```
![](Fotos/unzip_moodle.png)

Cambiarem el propietari del directori.
 ```sh
sudo chown www-data:www-data /var/www/html/moodle
```
![](Fotos/sudo_chown.png)

Un cop hem fet aixo tornarem a reiniciar el servei "apache2" i provarem d'accedir al Moodle pel nostre navegador.
```sh
sudo service apache2 restart
```
![](Fotos/acces_moodle.png)

Seleccionarem l'idioma de la instalació del moodle, en el meu cas he seleccionat el catala.

![](Fotos/idioma_moodle.png)

Ara ens indicara que falten dos moduls de PHP: curl i zip.

![](Fotos/error_moodle.png)

Per solucionar aquest problema executarem les seguents comandes:
```sh
sudo apt install php7.3-curl
```
![](Fotos/php_curl.png)

```sh
sudo apt install php7.3-zip
```
![](Fotos/php_zip.png)

Despres d'executar aquestes comandes reiniciarem el servei apache.
```sh
sudo service apache2 restart
```

Li donarem a F5 i refrescarem la pagina, i podrem veure que ja podrem seguir.
![](Fotos/moodle_3.png)

Canviarem el direcori de dades per un directori que previament haviem creat "/home/moodledata"
![](Fotos/moodle_4.png)

Quan li donarem a seguent, ens demanara quin controlador de base de dades usarem, en el nostre cas hem instalat MariaDB.
![](Fotos/moodle_5.png)

A la pàgina següent preguntaran l'adreça de la base de dades: "localhost", el nom de la base de dades: "moodle", l'usuari: "moodlemanager" i la contrasenya: "managermoodle", la resta de camps els podem deixar tal com estan.
![](Fotos/moodle_6.png)

Pero ens donara un error ja faltes unes eines que hem d'instalar.

![](Fotos/moodle_7.png)

Archiu XML
```sh
sudo apt install php7.3-xml
```
![](Fotos/terminal_1.png)

Archiu MBSTRING
```sh
sudo apt install php7.3-mbstring
```
![](Fotos/terminal_2.png)

Archiu GD
```sh
sudo apt install php7.3-GD
```
![](Fotos/terminal_3.png)

Archiu INTL
```sh
sudo apt install php7.3-intl
```
![](Fotos/terminal_4.png)

Archiu XMLRPC
```sh
sudo apt install php7.3-xmlrpc
```
![](Fotos/terminal_5.png)

Archiu SOAP
```sh
sudo apt install php7.3-soap
```
![](Fotos/terminal_6.png)

Un cop hem instalat tots aquests archius, reiniciarem el servei apache.
```sh
sudo service apache2 restart
```

Recargarem la pagina i ens sortiran les condicions de moodle, les aceptarem.

![](Fotos/moodle_8.png)

Seguidament ens mostrara les comprovacions del servidor, li donarem a continuar.

![](Fotos/moodle_9.png)

Ara ens sortiran els logs que tenim al servidor.

![](Fotos/moodle_10.png)

Seguidament actualitzarem el nostre perfil.

![](Fotos/moodle_11.1.png)

![](Fotos/moodle_11.2.png)

També hem de configurar els paràmetres de la pàgina de Moodle amb algunes descripcions:

![](Fotos/moodle_12.png)

I ja tindriem acces al nostre curs de moodle

![](Fotos/acces_moodle_complet.png)




