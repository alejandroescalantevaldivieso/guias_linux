# Instalación de Composer en Ubuntu

Esta guía explica cómo instalar **Composer** de forma global en Ubuntu utilizando el instalador oficial.

> **Fuente oficial:** 
>
>https://getcomposer.org/download/

La documentación oficial incluye siempre la versión más reciente de Composer, el instalador actualizado y las instrucciones recomendadas por el proyecto. Se recomienda consultar esta página antes de realizar la instalación, ya que el hash de verificación y la versión disponible pueden cambiar con el tiempo. :contentReference[oaicite:1]{index=1}

## Requisitos

Antes de comenzar, verifica que PHP esté instalado.

```bash
php -v
```

Ejemplo de salida:

```text
PHP 8.3.32 (cli)
```

---

# Paso 1. Descargar el instalador de Composer

Ejecuta:

```bash
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
```

Este comando descarga el instalador oficial (`composer-setup.php`) en el directorio actual.

---

# Paso 2. Verificar la integridad del instalador

Ejecuta:

```bash
php -r "if (hash_file('sha384', 'composer-setup.php') === 'c8b085408188070d5f52bcfe4ecfbee5f727afa458b2573b8eaaf77b3419b0bf2768dc67c86944da1544f06fa544fd47') { echo 'Installer verified'.PHP_EOL; } else { echo 'Installer corrupt'.PHP_EOL; unlink('composer-setup.php'); exit(1); }"
```

Si todo está correcto, obtendrás:

```text
Installer verified
```

Si aparece:

```text
Installer corrupt
```

No continúes con la instalación. Descarga nuevamente el instalador desde el sitio oficial.

---

# Paso 3. Instalar Composer

Ejecuta:

```bash
php composer-setup.php
```

Al finalizar, verás un mensaje similar a:

```text
All settings correct for using Composer
Downloading...

Composer (version 2.x.x) successfully installed to: composer.phar
Use it: php composer.phar
```

En este punto, Composer aún no está instalado de forma global.

---

# Paso 4. Instalar Composer globalmente

Mueve el archivo generado a un directorio incluido en el PATH:

```bash
sudo mv composer.phar /usr/local/bin/composer
```

De esta manera podrás ejecutar el comando `composer` desde cualquier ubicación del sistema.

---

# Paso 5. Eliminar el instalador

Ejecuta:

```bash
php -r "unlink('composer-setup.php');"
```

Este paso elimina el archivo utilizado durante la instalación.

---

# Paso 6. Verificar la instalación

Comprueba que Composer quedó instalado correctamente:

```bash
composer --version
```

Salida esperada:

```text
Composer version 2.10.2
PHP version 8.3.x
```

También puedes verificar la ruta del ejecutable:

```bash
which composer
```

Salida esperada:

```text
/usr/local/bin/composer
```

---

# Actualizar Composer

Para actualizar Composer a la última versión estable:

```bash
composer self-update
```

Verifica nuevamente la versión:

```bash
composer --version
```

---

# Desinstalar Composer

Si deseas eliminar Composer del sistema:

```bash
sudo rm /usr/local/bin/composer
```

---

# Comandos útiles

Ver la versión:

```bash
composer --version
```

Ver información de diagnóstico:

```bash
composer diagnose
```

Ver ayuda:

```bash
composer --help
```

Actualizar Composer:

```bash
composer self-update
```

---

# Verificación final

Confirma que PHP y Composer funcionan correctamente:

```bash
php -v
composer --version
```

Si ambos comandos muestran su versión sin errores, Composer quedó instalado correctamente y el entorno está listo para trabajar con proyectos Laravel.