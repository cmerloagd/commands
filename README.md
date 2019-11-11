## Ubuntu Command Listt

##### Gestionar archivos y directorios

```sh
cd /home : # Ir al directorio /home.
cd .. : # Ir al directorio anterior.
pwd : # Mostrar ruta.

document.designMode = "on"

sudo su : # Acceder como root.
su : # Acceder como root.
su nombre_usuario : # Cambiar de usuario.

ssh direccion_ip : # Acceder por ssh.
ssh direccion_ip -l usuario : # Acceder por ssh con usuario.
ssh usuario@direccion_ip : # Acceder por ssh con usuario.

ls : # Listar contenido.
ls -lh : # Listar contenido + permisos (h tamaño del archivo).
ls -al : # Listar contenido + permisos + ocultos.
ls -tl : #
ls *.json : #

mkdir dir1 : # Crear directorio.
mkdir -p /var/www/html/nombredirectorio.com : # Crear directorio (-p: crea los directorios padres en caso necesario).

rm file : # Eliminar archivo.
rm -f file : # Eliminar archivo forzado.
rm -rf directorio : # Eliminar directorio recursivo y forzado.

cp file1 destino/ : # Copiar archivo.
cp -ra /origen_directorio/files /destino_directorio/files : # Copiar directorio completo (Recursivo y con los permiso).

scp -r /home/mario/carpeta /home/usr : # Copiar directorio completo.
scp archivo.txt /home/usr : # Copiar archivo a directorio.

mv file1 /destino : # Mover archivo.
mv directorio directorio_renombrado : # Renombrar directorio.


ctrl + c  : # Frenar ejecución.
clear : # Limpiar pantalla.
history : # Historial de comandos ejecutados.

sudo vi index.html : # Crear/Ver Archivo. [insert, esc, :q (Salir si no hubo cambios), :q! (Salir sin guardar cambios), :w (guardar), :wq (guarda y sale de vi)].

touch /home/index.html : # Crear archivo.
echo "<?php phpinfo();?>" > /home/index.php : # Crear archivo con contenido.
```

##### Encontrar archivos:

```sh
find /home/nombre_usuario/Escritorio -name “*.jpg” : # Busca todos los archivos del Escritorio con extensión .jpg.  
find . -name “*hola*” : # Busca todos los archivos que contienen la palabra “hola” en el nombre.  
find . ! -name “*hola*” : # Busca todos los archivos que NO contienen la palabra “hola” en el nombre.  
find . -name “*hola*” -a “*caracola*” : # Busca todos los archivos que contienen la palabra “hola” y “caracola” en el nombre.  
find . -name “*hola*” -o “*caracola*” : # Busca todos los archivos que contienen la palabra “hola” o “caracola” en el nombre.  
find . -iname “*hola*” : # Busca todos los archivos que contienen la palabra “hola” en el nombre tanto en mayúsculas como en minúsculas.   
find . -user nombre_usuario : # Busca todos los archivos de un usuario determinado (nombre_usuario).  
find . -size +1000k : # Busca todos los archivos de tamaño mayor a 1000 kb.  
find . -amin -30 : # Busca todos los archivos a los que se accedió en los últimos 30 minutos.  
find . -atime 365 : # Busca todos los archivos a los que se accedió hace un año exactamente.  
find . -name “*.jpg” -exec rm {} \; : # Busca todos los archivos con extensión .jpg y los borra.  
find nombre_directorio -name nombre_archivo > /home/nombre_usuario/Escritorio/Lista.txt : # Para guardar el resultado de la búsqueda en un archivo de texto.

find / -type f -mtime -3 : # Ver últimos archivos modificados desde hace 3 días.
find / -type f -mmin -30 : # Ver últimos archivos modificados desde hace 30 minutos.
find / -type f -mtime -5 ! -mtime -3 : # Ver últimos archivos hace mas de 5 días pero no menos de 3 días.
find / -type f -newermt "2017-12-27" : # Ver últimos archivos modificados a partir de cierta fecha.
find / -type f -mmin -120 -ls : # Ver últimos archivos modificados hace dos horas mostrando permisos.

find /root/ -type f -printf "%T@ %p\n" | sort -nr | head -15 : # Buscar los 15 archivos modificados.

grep -lir "linux" "/media/cosas" : # Buscar archivos que contengan la frase “linux” dentro la carpeta /media/cosas. El parámetro -l le indica que imprima los nombres de archivos en los que se encuentre el texto solicitado. El parámetro -i, que ignore las mayúsculas y minúsculas. El parámetro -r, que busque en forma recursiva dentro de la ruta indicada.
grep linux /cosas/*.pdf : # Buscar en un determinado archivo la frase linux.
grep Aug /var/log/messages : # Buscar palabras “Aug” en el fichero /var/log/messages.
grep Aug *. * : # Busar palabras "Aug" en todos los ficheros.

grep danger ejemplo.txt> salida.txt : # Redirigir la salida a un archivo.
```

##### Ver el contenido de un fichero:

```sh
cat /etc/crontab : # Ver crontab.
sudo vi /etc/crontab : # Editar crontab.
 
tailf /var/log/apache2/access.log : # Ver cambios tiempo real.
tailf /var/log/apache2/error.log : # Ver cambios tiempo real.

tail error.log : # Por defecto ver las ultimas 10 lineas. 
tail -n 100 error.log : # Ver las ultimas 100 lineas.
tail -f myfile.txt : # Ver las ultimas 10 lineas y monitorea los cambios.

tail -f error.log | grep error : # filtrar resultados con palabra error.
```

##### Comprimir / Descomprimir:

```sh
sudo unzip archivo.zip /carpeta_destino/ : # descomprimir archivos en formato .zip
sudo unrar -x archivo.rar /carpeta_destino/ : # descomprimir archivos en formato .rar
sudo tar -zxvf archivo.tar.gz /carpeta_destino/ : # descomprimir archivos en formato .tar
sudo gzip -d archivo.zip /carpeta_destino/ : # descomprimir archivos en formato .gzip

sudo zip -r directorio-comprimido.zip /home/usuario : # comprimir un directorio completo incluyendo subdirectorios en formato .zip
sudo rar -a archivo.rar ficheros : # comprimir archivos en formato .rar

sudo tar -czvf empaquetado.tar.gz /carpeta/a/empaquetar/ : # comprimir en formato .tar
sudo tar -czvf empaquetado.tar.gz * : # comprimir en formato .tar todos los archivos dentro de directorio actual incluidos subdirectorios.
```

##### Command MySQL:

```sh
mysql -u name_user -p; : # Abrir MySQL.
mysql -u name_user -p name_bd; : # Abrir MySQL.
mysql -u name_user -p password name_bd -h host -P port : # Abrir MySQL.

use nombre_bd;  : # Abrir bd.
describe nombre_tabla; : # Estructura tabla.
create database nombre_bd; : # Crear bd.
show databases; : # Ver bd.
select database(); : # Ver bd en uso.
show full tables from mi_base_de_datos; : # Ver tablas.
show tables; : # Ver tablas.
show grants; : # Ver Permisos Usuario.
select .. \G; : # Consulta SQL, consulta mas visible.
drop database nombre_bd; : # Eliminar BD.
show procedure status \G; : # Ver procedimientos almacenados(por descripcion).
show create procedure nombre_procedimiento; : # Ver procedimientos almacenados (por codigo).
show create view view_name; : # Ver vista.

ALTER TABLE table_name ADD INDEX index_name (column_name); : # Crear Indices.

show indexes from table_name; : # Ver Indices.
show indexes from table_name in database_name; : # Ver Indices.

sudo tar -zcvf /destino/nombre_archivo.tar.gz /origen_directorio/ : # Comprimir.
mysqldump -u db_username -h db_host -p db_name table_name > /home/name/db_nanme.sql : # Backup.
scp usuario@ip:/carpeta_origen/db_name.sql /carpeta_destino/db_name.sql : # Secure Copy.
sudo tar -xzvf /carpeta_origen/name.tar.gz /carpeta_destino/name/ : # Descomprimir.
mysql -u db_username -p db_name < /home/name/db_name.sql : # Restaurar.
mysql -u db_username -p db_name < /home/name/script.sql : # Ejecutar archivo sql.

mysqldump -u root -p bd_name | gzip -c > /name/bd_name.sql.gz : # Backup y comprime.

gunzip -c /name/bd_name.sql.gz | mysql -u root -p bd_name : # Descomprimir y restaurar. 

gunzip /name/bd_name.sql.gz : # Descomprimir sql.gz.

LOAD DATA INFILE '/tmp/name_file' INTO TABLE name_table FIELDS TERMINATED BY ';' ENCLOSED BY '"' LINES TERMINATED BY '\r\n'; : # Importar archivo a BD.
```

##### Usuarios y privilegios en bases de datos MySQL:

```sh
select * from mysql.user; : # Listado de usuarios con sus persmisos.
show grants for nombre_usuario; : # Listar privilegios de usuario a las base de datos que tiene acceso.
SHOW GRANTS; : # Listar privilegios para el usuario conectado.
SHOW GRANTS FOR CURRENT_USER; # Listar privilegios para el usuario conectado.
select user,host,select_priv from mysql.db where db='nombre_basedatos'; : # Listado de usuarios que tienen acceso a una determinada base de datos de modo solo conuslta. (Y => yes, N => no)
select user,host,insert_priv,update_priv,delete_priv from mysql.db where db='nombre_basedatos'; : # Listado de usuarios que tienen acceso a una determinada base de datos de modo edición (insertar, modificar y eliminar filas). (Y => yes, N => no)

create user 'user'@'localhost' identified by 'password'; : # Crear nuevo usuario.
drop user 'user'@'localhost'; : # Eliminar usuario.

# Se ejecuta a nivel de base de datos.
GRANT ALL PRIVILEGES on base1.* to 'pepe'@'%' identified by 'pepe1234'; : # Permitir el acceso al usuario "pepe" a la base de datos "base1" desde el host remoto "192.168.1.101" utilizando la contraseña "pepe1234"

GRANT ALL PRIVILEGES ON mydb.* TO 'user'@'%' WITH GRANT OPTION;
GRANT ALL PRIVILEGES ON mydb.* TO 'user'@'localhost';

FLUSH PRIVILEGES; : # Refrescar todos los privilegios.
```

##### Espacio en disco:

```sh
df -h : # Muestra el uso de espacio de discos duros o particiones.
df -Th / : # mismo de arriba.
du -h --max-depth=1 -x : # Muestra el uso de espacio de archivos y directorios.
du -csh / : # mismo de arriba.
du -d1 -h /home | sort -h : # mismo de arriba.

du -hs * | sort -nr | head -5
du -h | sort -hr | head
```

##### Permisos en ficheros:

```sh
sudo chown usuario.www-data -R /directorio/ : # Cambiar propietario al directorio.
sudo chmod -R 755 /directorio : # Cambiar permisos al directorio.
```

##### Información del Servidor:

```sh
top : # Procesos de la CPU en tiempo real.
top -u jrivera : # Mostrar unicamente de un usuario.
ps : # Procesos activo.
ps -u nombre_usuario : # Procesos activos del usuario.
ps aux : # muestra todos los procesos del sistema.
ps aux | grep bash : # filtrar resultados de procesos bash.

kill id_proceso : # Termina procesos.

w : # Usuarios conectados.
who : # Usuarios conectados.
users : # Usuarios conectados.
last : # Ultimos usuarios conectados.
lastlog : # Listados de todos los usuarios con la fecha de ultimo ingreso.

whoami : # Muestra el usuario actual.

lsb_release -a : # Version del Servidor.

netstat -lntu : # Puertos Ubuntu.
-l : # Permite ver exclusivamente los puertos de escucha.
-p : # Muestra las conexiones para el protocolo especificado que puede ser TCP o UDP.
-u : # Lista todos los puertos UDP.
-t : # Lista todos los puertos TCP.
-o : # Muestra los timers.
-n : # Muestra el numero de puerto.
-a : # Visualiza todas las conexiones activas del sistema.

curl -I https://www.agd.com.ar : # Info header.

dig google.com : # Consultas DNS
dig @8.8.8.8 google.com : # Consultas DNS

wget  url_descargar : # Descargar archivo de internet

ifconfig : # Muestra/Configura las interfaces de red del sistema

resolveip : # Resuelve la ip del dominio o host que se indique.

ping 172.30.0.131

hostnamectl : # Informacion del Hostname
hostname -I : # Muestra todas las direcciones de red del host
host www.agd.com.ar : # Buscar el nombre del host 
nslookup www.agd.com.ar : # Buscar el nombre del host

telnet 172.30.0.131 3306 : # Telnet

iptables -L -n : # Listar iptables
vi /etc/sysconfig/iptables : # Modificar iptables

```

##### Ubuntu Server

```sh
sudo service apache2 restart : # Restart Apache 2.
sudo service apache2 stop : # Stop Apache 2.
sudo service apache2 start : # Start Apache 2.

sudo service mysql restart : # Restart Mysql.
sudo service mysql stop : # Stop Mysql.
sudo service mysql start : # Start Mysql.
```

#### GIT:

##### Getting & Creating Projects

```sh
git init : # Crear un nuevo repositorio.
git clone /path/to/repository : # Crea una copia local del repositorio.
git clone username@host:/path/to/repository : # Si utilizas un servidor remoto.

git remote add origin https://github.com/nombre_repositorio.git : # Conectar tu repositorio local a un repositorio remoto.
```

##### Basic

```sh
git status : # Estado del repositorio.
git add nombre_archivo : # Registrar cambios de un archivo.
git add . : # Agregando todos los cambios de archivos en un directorio.
git add -A : # Registrar cambios de todos los archivos.
git commit -m "Commit message" : # Hace commit.
git rm -r [file-name.txt] : # Eliminar un archivo o directorio.
 ```
 
##### Branching & Merging

```sh
git branch : # Listar branches (local).
git branch -a : # Listar branches (local y remoto).
git branch [branch name] : # Crear un nuevo branch.
git branch -d [branch name] : # Eliminar un branch.
git push origin --delete [branch name] : # Elimina un branch remoto.
git checkout -b [branch name] : # Crea un nuevo branch y me cambio a ella.
git checkout -b [branch name] origin/[branch name] : # Clona un branch remota y me cambia a ella.
git checkout - : # Switch to the branch last checked out.
git checkout -- [file-name.txt] : # Descartar cambios a un archivo.
git stash : # Stash changes in a dirty working directory.
git stash clear : # Remove all stashed entries.

# Para fusionar una rama nuevafuncionalidad dentro de master vamos a situarnos en la rama mater y a mezclar ambas:
git checkout master : # Cambiar a branch master.
git merge nuevafuncionalidad : # Fusionar nuevafuncionalidad a tu rama activa(master).
 ```
 
##### Sharing & Updating Projects

```sh
git push origin <branch> : # Subir (push) la rama a tu repositorio remoto.
git pull : # Actualizar tu repositorio local al commit más nuevo.
git pull origin NombreDeBranch : # Actualiza nuestro branch local, desde un branch remoto que indicamos en el comando.
 ```
 
##### Inspection & Comparison

```sh
git log : # Ver cambios.
git log --summary : # Ver cambios detallados.
git show : # Muestra los cambios realizados en el commit.
git diff [source branch] [target branch] : # Vista previa de cambios antes de fusionar.

git config : # Establecer la configuracion.
git remote -v : # Muestra los repositorios remotos que están configurados actualmente.

git remote set-url origin https://github.com/USERNAME/REPOSITORY.git : # Cambiar la URL del repositorio remoto existente.

git config --get remote.origin.url : # Obtener la url de nuestro repositorio.

git remote show nombre_repositorio : # Ver informacion detallada sobre la configuracion del repositorio.
git remote show origin : # Ver informacion detallada sobre la configuracion del repositorio.
git config --local -l : # Conocer todos los datos de la configuración local de Git en nuestro proyecto.
git config --global -l : # Conocer todos los datos de la configuración global de Git en nuestro proyecto.
git config --global user.name "Sam Smith" : # Configurar name que será identificado al hacer el commits.
git config --global user.email sam@example.com : # Configurar email que será identificado al hacer el commits.
git config --global color.ui true : # Aplicar color al git.
 ```
#### Vaciado de Compras DB Mantenimiento (131) 
```sh
 SET FOREIGN_KEY_CHECKS = 0;truncate attachment_additional_doc; truncate attachment_oqs; truncate attachment_visits; truncate attachments; truncate balance_cancelations; truncate building_visit_dates; truncate building_visit_headers; truncate calendaries; truncate chat_messages; truncate chat_participants; truncate chat_threads; truncate contacts_for_ocs; truncate filings; truncate mail_invitations;truncate metrics;truncate notifications; truncate oq_additional_costs; truncate oq_line_additional_costs; truncate oq_lines; truncate oqs; truncate oqs_added; truncate px_company; truncate px_company_notification; truncate px_company_oq; truncate px_company_oq_lines; truncate px_company_oq_lines_comments; truncate px_company_requote_comments; truncate px_oq; truncate pxs; truncate reject_comment_ocs; truncate statistics_oqs; truncate web_hooks; truncate doc_memory; SET FOREIGN_KEY_CHECKS = 1;
 ```
```sh
#### Comando artisan para transferir respuestas de proveedores de una PX GRANDE (137) 
/var/www/html$ sudo php artisan jde:enviar-respuestas --px PX13459
```
