#  Despliegue de la Aplicación PokeDex

##  Descripción

En este documento se describe el proceso completo de despliegue de la aplicación PokeDex en la nube utilizando **Microsoft Azure**, mediante el servicio de Static Web Apps. Se incluyen los pasos realizados, configuración del entorno, automatización del despliegue y resolución de problemas.

---

##  Arquitectura del Despliegue

* **Repositorio:** GitHub
* **Framework:** Angular
* **Plataforma Cloud:** Microsoft Azure
* **Servicio:** Static Web Apps
* **CI/CD:** GitHub Actions

---

##  Proceso de Despliegue

### 1. Preparación del proyecto

Se verificó que la aplicación compilara correctamente ejecutando:

```bash id="n7y6u2"
npm install
npm run build
```

Esto generó la carpeta de salida:

```text id="2x0b8n"
dist/pokedex-angular
```

---

### 2. Subida del proyecto a GitHub

Se inicializó el repositorio y se subió el código:

```bash id="3k5g0x"
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/camilo2004h2o-spec/pokemon.git
git push -u origin main
```

---

### 3. Creación del recurso en Azure

En el portal de **Microsoft Azure**:

1. Se seleccionó **Crear recurso**
2. Se eligió **Static Web Apps**
3. Se configuraron los siguientes parámetros:

* **Nombre:** pokemon
* **Región:** East US 2
* **Repositorio:** GitHub
* **Branch:** main

---

### 4. Configuración del pipeline (CI/CD)

Azure generó automáticamente el archivo:

```text id="0v4i5h"
.github/workflows/azure-static-web-apps.yml
```

Se ajustaron los parámetros clave:

```yaml id="2f5xqb"
app_location: "/pokedex-angular"
output_location: "dist/pokedex-angular"
```

Esto permitió que Azure identificara correctamente la ubicación del código fuente y la carpeta de compilación.

---

### 5. Despliegue automático

Cada vez que se realiza un cambio en la rama `main`:

* Se ejecuta el pipeline
* Se construye la aplicación
* Se publica automáticamente en la nube

---

##  Configuración de Seguridad

Se creó el archivo:

```text id="c0qf4o"
staticwebapp.config.json
```

Incluyendo encabezados de seguridad como:

* Content-Security-Policy
* Strict-Transport-Security
* X-Frame-Options
* X-Content-Type-Options
* Referrer-Policy
* Permissions-Policy

Esto permitió mejorar significativamente la seguridad de la aplicación, alcanzando una calificación **A / A+** en herramientas de análisis.

---

##  Dominio Personalizado

Se configuró un dominio utilizando DuckDNS:

```text id="r8k2gj"
midominio.duckdns.org
```

### Pasos realizados:

1. Creación del subdominio en DuckDNS
2. Asociación del dominio en Azure (Custom Domains)
3. Validación mediante registro TXT
4. Activación automática de HTTPS

---

# Validación

Se verificó el despliegue mediante:

* Acceso a la URL pública
* Pruebas de navegación
* Evaluación de seguridad con securityheaders.com

---

##  Problemas Encontrados y Soluciones

## Error 403 en GitHub (Permission denied)

**Problema:**
El repositorio estaba vinculado a otra cuenta.

**Solución:**
Se corrigieron las credenciales y el repositorio remoto.

---

### 🔴 Error: repositorio dentro de otro repositorio

**Problema:**

```text id="n4o1qv"
hint: You've added another git repository inside your current repository.
```

Esto ocurrió porque la carpeta `pokedex-angular` contenía un repositorio Git interno.

**Solución:**

```bash id="g2k8vb"
git rm --cached pokedex-angular
```

Se eliminó el repositorio interno y se volvió a agregar correctamente el proyecto.

---

### 🔴 Error de Azure: appArtifactLocation inválido

**Problema:**
Configuración incorrecta en el pipeline.

**Solución:**
Se corrigió el `output_location` en el workflow.

---

### 🔴 Error de Oryx: lenguaje no detectado

**Problema:**
Azure no detectaba la aplicación Angular.

**Solución:**

```yaml id="7tq2df"
app_location: "/pokedex-angular"
```

---

### 🔴 Error: archivo index.html no encontrado

**Problema:**
Azure no encontraba el archivo principal.

**Solución:**
Se verificó la correcta generación de la carpeta `dist`.

---

##  Lecciones Aprendidas

* La correcta configuración del pipeline es fundamental
* Los errores de rutas son comunes en Angular
* Git puede generar conflictos con repositorios anidados
* La seguridad debe implementarse desde el inicio
* Azure facilita la automatización, pero requiere configuración precisa

---

##  Conclusión

El despliegue de la aplicación PokeDex se realizó exitosamente utilizando **Microsoft Azure**, logrando integrar desarrollo, despliegue automático y seguridad en un mismo flujo.

Este proceso permitió aplicar conceptos reales de DevOps, fortaleciendo habilidades en integración continua, manejo de errores y configuración de entornos en la nube.

---
