# Instalación de PHP 8.3 en Ubuntu

Esta guía explica cómo instalar **PHP 8.3** en Ubuntu utilizando el repositorio oficial recomendado para distribuciones Ubuntu.

> **Página oficial de PHP:**
>
> https://www.php.net/downloads.php?os=linux&osvariant=linux-ubuntu&version=8.3

## 1. Actualizar los paquetes del sistema

Antes de comenzar, actualiza la lista de paquetes disponibles:

```bash
sudo apt update
```

---

## 2. Instalar la herramienta para agregar repositorios

Instala el paquete necesario para agregar repositorios externos:

```bash
sudo apt install -y software-properties-common
```

---

## 3. Agregar el repositorio de PHP

Agrega el repositorio que proporciona las versiones más recientes de PHP para Ubuntu:

```bash
sudo LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php -y
```

---

## 4. Actualizar nuevamente los paquetes

Después de agregar el repositorio, actualiza la información de los paquetes:

```bash
sudo apt update
```

---

## 5. Instalar PHP 8.3

Instala PHP junto con las extensiones más utilizadas por Laravel.

```bash
sudo apt install -y \
php8.3 \
php8.3-cli \
php8.3-common \
php8.3-fpm \
php8.3-mysql \
php8.3-pgsql \
php8.3-sqlite3 \
php8.3-mbstring \
php8.3-xml \
php8.3-curl \
php8.3-zip \
php8.3-bcmath \
php8.3-intl \
php8.3-gd \
php8.3-soap \
php8.3-readline
```

### Extensiones instaladas

| Extensión | Descripción |
|-----------|-------------|
| php8.3-cli | Permite ejecutar PHP desde la terminal. |
| php8.3-common | Archivos comunes de PHP. |
| php8.3-fpm | FastCGI Process Manager para servidores web. |
| php8.3-mysql | Soporte para MySQL y MariaDB. |
| php8.3-mbstring | Manejo de cadenas multibyte. |
| php8.3-xml | Procesamiento de XML. |
| php8.3-curl | Realizar solicitudes HTTP. |
| php8.3-zip | Compresión y descompresión de archivos ZIP. |
| php8.3-bcmath | Operaciones matemáticas de alta precisión. |
| php8.3-intl | Internacionalización y soporte para diferentes idiomas. |
| php8.3-sqlite3 | Soporte para bases de datos SQLite. |

---

## 6. Verificar la instalación

Comprueba que PHP se haya instalado correctamente:

```bash
php -v
```

Salida esperada:

```text
PHP 8.3.x (cli)
Built: ...
Copyright (c) The PHP Group
Zend Engine v4.3.x
```

---

## Verificar los módulos instalados

Puedes listar todos los módulos de PHP instalados con:

```bash
php -m
```

---

## Verificar la ubicación del ejecutable

```bash
which php
```

Ejemplo de salida:

```text
/usr/bin/php
```

---

## Comprobar la versión instalada

```bash
php --version
```

o

```bash
php -v
```

---

## Instalación completada

Si todos los comandos anteriores se ejecutaron correctamente, PHP 8.3 estará listo para utilizarse en tu sistema Ubuntu.

El siguiente paso para trabajar con Laravel es instalar **Composer**.