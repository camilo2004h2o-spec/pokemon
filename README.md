# 🧩 PokeDex App - Despliegue en la Nube

## 📌 Descripción del Proyecto

PokeDex es una aplicación web estática que permite explorar diferentes especies de Pokémon, mostrando información detallada sobre sus características, tipos y habilidades.

El objetivo de este proyecto es desplegar la aplicación en la nube aplicando buenas prácticas de **DevOps** y **seguridad web**, garantizando disponibilidad, rendimiento y protección ante vulnerabilidades comunes.

---

## 🌐 Tecnologías Utilizadas

* **Frontend:** Angular
* **Control de versiones:** Git + GitHub
* **Plataforma de despliegue:** Microsoft Azure (Static Web Apps)
* **Análisis de seguridad:** securityheaders.com

---

## 🚀 Despliegue de la Aplicación

### 1. Clonar el repositorio

```bash
git clone https://github.com/camilo2004h2o-spec/pokemon.git
cd pokedex-angular
```

---

### 2. Instalación de dependencias

```bash
npm install
```

---

### 3. Construcción del proyecto

```bash
npm run build
```

Esto genera la carpeta:

```text
dist/pokedex-angular
```

---

### 4. Configuración de Azure Static Web Apps

Se creó un recurso en **Microsoft Azure** con los siguientes parámetros:

* **App location:** `/pokedex-angular`
* **Output location:** `dist/pokedex-angular`
* **Branch:** `main`

Se configuró integración con GitHub para despliegue automático mediante CI/CD.

---

### 5. Despliegue automático

Cada vez que se realiza un `git push`, Azure:

* Compila la aplicación
* Genera los archivos estáticos
* Publica automáticamente la app

---

## 🔒 Seguridad de la Aplicación

Se implementaron encabezados HTTP de seguridad mediante el archivo:

```text
staticwebapp.config.json
```

### 🔐 Headers configurados

* **Content-Security-Policy:** Previene ataques XSS
* **Strict-Transport-Security:** Obliga uso de HTTPS
* **X-Content-Type-Options:** Evita MIME sniffing
* **X-Frame-Options:** Previene clickjacking
* **Referrer-Policy:** Protege la información del usuario
* **Permissions-Policy:** Restringe acceso a hardware del navegador

---

### 🧪 Validación de seguridad

Se realizó un análisis en:

👉 https://securityheaders.com/

📊 Resultado obtenido:

* Calificación: **A / A+**
* Nivel de seguridad: Alto

---

## 🌍 URL Pública

La aplicación se encuentra disponible en:

```text
* https://white-sand-0e6e6d40f.1.azurestaticapps.net/
```

---

## 🧠 Reflexión Técnica

La implementación de encabezados de seguridad permitió mitigar vulnerabilidades comunes como XSS, clickjacking y filtración de información. Además, se evidenció la importancia de integrar prácticas de seguridad desde la fase de despliegue y no como un proceso posterior.

El uso de **Microsoft Azure** facilitó la automatización del despliegue, demostrando cómo las herramientas modernas de DevOps permiten integrar desarrollo, despliegue y seguridad en un solo flujo de trabajo.

---

## ✅ Conclusión

Se logró desplegar exitosamente una aplicación web en la nube, aplicando buenas prácticas de seguridad y automatización. Este proceso permitió fortalecer habilidades en despliegue, configuración de entornos y protección de aplicaciones web en escenarios reales.

---
