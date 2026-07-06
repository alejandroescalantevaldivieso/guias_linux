
# Guía de instalación de MySQL Server y MySQL Workbench en Ubuntu

## Objetivo

Al finalizar esta guía tendrás:

- MySQL Server instalado.
- Servicio MySQL funcionando automáticamente.
- Usuario `root`.
- Contraseña del usuario `root`: `root`.
- Método de autenticación compatible con MySQL Workbench (`mysql_native_password`).
- MySQL Workbench instalado y conectado al servidor.

---

# 1. Actualizar el sistema

```bash
sudo apt update
sudo apt upgrade -y
```

---

# 2. Instalar MySQL Server

```bash
sudo apt install mysql-server -y
```

### ¿Aparecerán preguntas?

Normalmente **NO**.

La instalación termina automáticamente.

---

# 3. Verificar que el servicio esté funcionando

```bash
sudo systemctl status mysql
```

Debe aparecer algo similar a:

```
Active: active (running)
```

Si no está iniciado:

```bash
sudo systemctl start mysql
sudo systemctl enable mysql
```

---

# 4. Entrar al servidor MySQL

En Ubuntu el usuario root utiliza autenticación por socket.

Ingresamos mediante:

```bash
sudo mysql
```

Si todo salió bien aparecerá:

```
mysql>
```

---

# 5. Configurar contraseña para root

Dentro de MySQL ejecutar:

```sql
ALTER USER 'root'@'localhost'
IDENTIFIED WITH mysql_native_password BY 'root';

FLUSH PRIVILEGES;

EXIT;
```

Con esto:

Usuario:

```
root
```

Contraseña:

```
root
```

Método de autenticación:

```
mysql_native_password
```

Este método permite conectarse desde:

- MySQL Workbench
- DBeaver
- Visual Studio Code
- Aplicaciones Java
- Aplicaciones PHP
- Laravel
- Node.js

---

# 6. Probar el acceso

Ya NO se debe ingresar con:

```bash
sudo mysql
```

Ahora utilizar:

```bash
mysql -u root -p
```

El sistema preguntará:

```
Enter password:
```

Escribir:

```
root
```

Si aparece:

```
mysql>
```

Todo está correctamente configurado.

---

# 7. Ejecutar la configuración de seguridad

Ejecutar:

```bash
sudo mysql_secure_installation
```

Durante el proceso aparecerán varias preguntas.

---

## Pregunta 1

```
Would you like to setup VALIDATE PASSWORD component?
```

Responder:

```
N
```

---

## Pregunta 2

```
Change the password for root?
```

Responder:

```
N
```

Ya configuramos la contraseña anteriormente.

---

## Pregunta 3

```
Remove anonymous users?
```

Responder:

```
Y
```

---

## Pregunta 4

```
Disallow root login remotely?
```

Responder:

```
Y
```

---

## Pregunta 5

```
Remove test database and access to it?
```

Responder:

```
Y
```

---

## Pregunta 6

```
Reload privilege tables now?
```

Responder:

```
Y
```

Con esto termina la configuración básica de seguridad.

---

# 8. Verificar la versión instalada

```bash
mysql --version
```

Ejemplo:

```
mysql  Ver 8.0.xx
```

---

# 9. Descargar MySQL Workbench

Descargar el paquete correspondiente a tu versión de Ubuntu desde:

https://dev.mysql.com/downloads/workbench/

Por ejemplo:

Ubuntu 22.04

```
mysql-workbench-community_8.0.xx-1ubuntu22.04_amd64.deb
```

Ubuntu 24.04

```
mysql-workbench-community_8.0.xx-1ubuntu24.04_amd64.deb
```

---

# 10. Instalar MySQL Workbench

Ir a la carpeta donde se descargó el archivo.

Ejemplo:

```bash
cd ~/Descargas
```

Instalar:

```bash
sudo dpkg -i mysql-workbench-community*.deb
```

Si aparecen errores por dependencias:

```bash
sudo apt --fix-broken install
```

Luego ejecutar nuevamente:

```bash
sudo dpkg -i mysql-workbench-community*.deb
```

---

# 11. Abrir MySQL Workbench

Desde la terminal:

```bash
mysql-workbench
```

O buscar:

```
MySQL Workbench
```

en el menú de aplicaciones.

---

# 12. Crear una conexión

Seleccionar:

```
+
```

Nueva conexión.

Completar:

Connection Name

```
Localhost
```

Hostname

```
127.0.0.1
```

Port

```
3306
```

Username

```
root
```

Password

```
Store in Vault...
```

Contraseña:

```
root
```

Guardar.

---

# 13. Probar la conexión

Presionar:

```
Test Connection
```

Debe aparecer:

```
Successfully made the MySQL connection.
```

---

# 14. Verificar desde consola

```bash
mysql -u root -p
```

Contraseña:

```
root
```

Mostrar bases de datos:

```sql
SHOW DATABASES;
```

Salir:

```sql
EXIT;
```

---

# Resultado esperado

✔ MySQL Server instalado.

✔ Servicio iniciado automáticamente.

✔ Usuario:

```
root
```

✔ Contraseña:

```
root
```

✔ MySQL Workbench instalado.

✔ Conexión gráfica funcionando.

✔ Compatible con Laravel, Java, PHP, Node.js y cualquier cliente MySQL.

---

# Comandos útiles

Iniciar MySQL

```bash
sudo systemctl start mysql
```

Detener MySQL

```bash
sudo systemctl stop mysql
```

Reiniciar MySQL

```bash
sudo systemctl restart mysql
```

Ver estado

```bash
sudo systemctl status mysql
```

Entrar al servidor

```bash
mysql -u root -p
```

Ver versión

```bash
mysql --version
```



