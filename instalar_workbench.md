# Guía de Instalación de MySQL Workbench en Ubuntu 22.04 LTS

## Objetivo

Instalar **MySQL Workbench** (interfaz gráfica oficial de MySQL) en Ubuntu 22.04 LTS y resolver correctamente las dependencias necesarias.

> **Importante:** Esta guía asume que **MySQL Server ya está instalado**.

Descargar el paquete correspondiente a tu versión de Ubuntu desde:

https://dev.mysql.com/downloads/workbench/

---

# 1. Verificar la versión de Ubuntu

Antes de descargar el instalador, verifica la versión de Ubuntu.

```bash
lsb_release -a
```

Debe mostrar algo similar a:

```text
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.5 LTS
Release:        22.04
Codename:       jammy
```

> **Importante**
>
> Descarga el paquete correspondiente exactamente a tu versión de Ubuntu.
>
> - Ubuntu 22.04 → `mysql-workbench-community_8.0.47-1ubuntu22.04_amd64.deb`
> - Ubuntu 24.04 → `mysql-workbench-community_8.0.47-1ubuntu24.04_amd64.deb`

Instalar un paquete para una versión diferente puede ocasionar errores por dependencias incompatibles.

---

# 2. Descargar MySQL Workbench

Descarga el paquete oficial desde la página de MySQL.

Archivo para Ubuntu 22.04:

```text
mysql-workbench-community_8.0.47-1ubuntu22.04_amd64.deb
```

Se recomienda guardarlo en la carpeta:

```text
~/Descargas
```

---

# 3. Abrir la terminal

Ir a la carpeta donde se descargó el archivo.

```bash
cd ~/Descargas
```

Comprobar que el archivo existe.

```bash
ls | grep mysql-workbench
```

Salida esperada:

```text
mysql-workbench-community_8.0.47-1ubuntu22.04_amd64.deb
```

---

# 4. Instalar el paquete

Ejecutar:

```bash
sudo dpkg -i mysql-workbench-community_8.0.47-1ubuntu22.04_amd64.deb
```

---

# 5. ¿Qué puede ocurrir durante la instalación?

## Caso 1: Instalación exitosa

La instalación termina sin errores y regresa el prompt de la terminal.

En este caso continuar con el paso 7.

---

## Caso 2: Error por dependencias

Es completamente normal que aparezca un mensaje como:

```text
dpkg: dependency problems prevent configuration of mysql-workbench-community
```

o

```text
mysql-workbench-community depends on...
```

Esto ocurre porque `dpkg` instala el paquete, pero **no descarga automáticamente las dependencias**.

---

# 6. Corregir dependencias

Ejecutar:

```bash
sudo apt --fix-broken install
```

Durante la instalación aparecerá:

```text
¿Desea continuar? [S/n]
```

Seleccionar:

```text
S
```

y presionar **Enter**.

Ubuntu descargará automáticamente todas las bibliotecas necesarias, por ejemplo:

- libmysqlclient21
- libodbc2
- libproj22
- libzip4
- proj-data

Al finalizar deberá aparecer un mensaje similar a:

```text
Configurando mysql-workbench-community (8.0.47-1ubuntu22.04)
```

Finalmente ejecutar nuevamente:

```bash
sudo apt --fix-broken install
```

La salida esperada es:

```text
0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
```

Esto confirma que todas las dependencias fueron instaladas correctamente.

---

# 7. Abrir MySQL Workbench

Desde la terminal:

```bash
mysql-workbench
```

O desde el menú de aplicaciones buscar:

```text
MySQL Workbench
```

Si la instalación fue correcta, se abrirá la interfaz gráfica del programa.

---

# 8. Crear una conexión al servidor MySQL

En la ventana principal seleccionar el símbolo **"+"** junto a **MySQL Connections**.

Completar los siguientes campos:

| Campo | Valor |
|--------|-------|
| Connection Name | Local MySQL |
| Connection Method | Standard (TCP/IP) |
| Hostname | localhost |
| Port | 3306 |
| Username | root |

Luego seleccionar:

```text
Store in Vault...
```

Ingresar la contraseña del usuario root.

Ejemplo:

```text
root
```

Finalmente pulsar:

```text
Test Connection
```

---

# 9. Resultado esperado

Si la conexión es correcta aparecerá el mensaje:

```text
Successfully made the MySQL connection.
```

Seleccionar:

```text
OK
```

Luego nuevamente:

```text
OK
```

La conexión quedará guardada y lista para utilizarse.

---

# Problemas comunes

## Error

```text
error while loading shared libraries: libzip.so.4
```

### Causa

Se instaló un paquete correspondiente a otra versión de Ubuntu o quedaron dependencias sin instalar.

### Solución

Ejecutar:

```bash
sudo apt --fix-broken install
```

---

## Error

```text
Workbench can't find libproj.so
```

### Causa

Falta instalar la biblioteca `libproj22`.

### Solución

Ejecutar:

```bash
sudo apt --fix-broken install
```

---

## Error

```text
dependency problems prevent configuration
```

### Causa

La instalación se realizó mediante `dpkg`, el cual no instala dependencias automáticamente.

### Solución

Ejecutar:

```bash
sudo apt --fix-broken install
```

---

# Verificación final

Comprobar que Workbench inicia correctamente:

```bash
mysql-workbench
```

Si el programa abre su interfaz gráfica sin mostrar errores, la instalación ha finalizado correctamente.



