# Instalación de Node.js y npm en Ubuntu usando NVM

Esta guía explica cómo instalar **Node.js** y **npm** en Ubuntu utilizando **NVM (Node Version Manager)**, el método recomendado para entornos de desarrollo.

> **Fuente oficial:** https://nodejs.org/es/download

La documentación oficial siempre muestra la versión LTS más reciente de Node.js y las instrucciones de instalación recomendadas. Se recomienda consultar esta página antes de instalar, ya que las versiones pueden cambiar con el tiempo.

---

# ¿Qué es NVM?

**NVM (Node Version Manager)** es una herramienta que permite instalar y administrar múltiples versiones de Node.js en un mismo equipo.

Entre sus ventajas se encuentran:

- Instalar diferentes versiones de Node.js.
- Cambiar fácilmente entre versiones.
- Actualizar Node.js sin afectar otros proyectos.
- No requiere permisos de administrador para instalar nuevas versiones.
- Es el método recomendado para desarrollo.

---

# Requisitos

Antes de comenzar, verifica que tengas instalado `curl`:

```bash
curl --version
```

Si no está instalado:

```bash
sudo apt update
sudo apt install curl
```

---

# Paso 1. Instalar NVM

Descarga e instala la versión más reciente de NVM:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
```

Este comando descarga y ejecuta el script oficial de instalación.

Al finalizar, aparecerá un mensaje indicando que NVM fue instalado correctamente.

---

# Paso 2. Cargar NVM en la terminal actual

Sin cerrar la terminal, ejecuta:

```bash
\. "$HOME/.nvm/nvm.sh"
```

Este comando carga NVM en la sesión actual para poder utilizarlo inmediatamente.

Si cierras y vuelves a abrir la terminal, este paso ya no será necesario.

---

# Paso 3. Verificar que NVM fue instalado

Ejecuta:

```bash
nvm --version
```

Ejemplo de salida:

```text
0.40.3
```

Si obtienes un número de versión, NVM quedó instalado correctamente.

---

# Paso 4. Instalar Node.js (versión LTS)

Instala la versión LTS más reciente:

```bash
nvm install 24
```

Durante la instalación se descargarán automáticamente:

- Node.js
- npm

Al finalizar, NVM configurará esta versión como la predeterminada.

---

# Paso 5. Verificar Node.js

Comprueba la instalación:

```bash
node -v
```

Salida esperada (puede variar según la versión disponible):

```text
v24.18.0
```

---

# Paso 6. Verificar npm

Comprueba la instalación de npm:

```bash
npm -v
```

Salida esperada (puede variar):

```text
11.16.0
```

---

# Paso 7. Verificar la ubicación de Node.js

Puedes comprobar qué ejecutable está utilizando el sistema:

```bash
which node
```

Ejemplo:

```text
/home/usuario/.nvm/versions/node/v24.18.0/bin/node
```

También puedes verificar npm:

```bash
which npm
```

Ejemplo:

```text
/home/usuario/.nvm/versions/node/v24.18.0/bin/npm
```

---

# Comandos útiles de NVM

## Mostrar la versión actual

```bash
node -v
```

## Mostrar la versión de npm

```bash
npm -v
```

## Ver la versión de NVM

```bash
nvm --version
```

## Listar versiones instaladas

```bash
nvm ls
```

## Mostrar versiones disponibles

```bash
nvm ls-remote
```

## Instalar otra versión de Node.js

Ejemplo:

```bash
nvm install 22
```

---

## Cambiar de versión

```bash
nvm use 22
```

---

## Establecer una versión como predeterminada

```bash
nvm alias default 24
```

---

## Desinstalar una versión

```bash
nvm uninstall 22
```

---

# Actualizar Node.js

Para instalar una nueva versión LTS cuando esté disponible:

```bash
nvm install --lts
```

O instalar una versión específica:

```bash
nvm install 26
```

---

# Verificación final

Comprueba que todo quedó instalado correctamente:

```bash
nvm --version
node -v
npm -v
```

Si los tres comandos muestran una versión sin errores, la instalación fue exitosa y el entorno está listo para trabajar con proyectos que utilicen Node.js, como Laravel con Vite.