# PokeDex App - Despliegue en la Nube

## Descripción del Proyecto

PokeDex es una aplicación web estática que permite explorar diferentes especies de Pokémon, mostrando información detallada sobre sus características, tipos y habilidades.

El objetivo de este proyecto es desplegar la aplicación en la nube aplicando buenas prácticas de **DevOps** y **seguridad web**, garantizando disponibilidad, rendimiento y protección ante vulnerabilidades comunes.

---

# Tecnologías Utilizadas

* **Frontend:** Angular
* **Control de versiones:** Git + GitHub
* **Plataforma de despliegue:** Microsoft Azure (Static Web Apps)
* **Análisis de seguridad:** securityheaders.com

---

# Despliegue de la Aplicación

## 1. Crear repositorio en git

<img width="921" height="320" alt="image" src="https://github.com/user-attachments/assets/c35bcfd2-834d-4e75-b705-0e57413b2514" />

## 2. Inicamos la inicializacion del repositorio
<img width="905" height="572" alt="image" src="https://github.com/user-attachments/assets/2a315f94-024f-42cd-925c-c2af57a458d4" />
<img width="917" height="569" alt="image" src="https://github.com/user-attachments/assets/1994d9a1-0b3d-4e75-86de-1d81b5f67361" />



## 3. Proyecto creado 
<img width="578" height="366" alt="image" src="https://github.com/user-attachments/assets/0aa05928-94fb-400d-bdf7-59edceabcf36" />


## 4. Creamos la aplicacion web statica en azure
<img width="921" height="444" alt="image" src="https://github.com/user-attachments/assets/a1dbfef8-dae6-4578-9d52-bb77e9210c88" />
<img width="921" height="411" alt="image" src="https://github.com/user-attachments/assets/9dc477b9-e36e-47b7-8cd2-3dd036f47c54" />
<img width="993" height="483" alt="image" src="https://github.com/user-attachments/assets/9ff84d86-9fb4-4fbc-ae2b-56eb6d638768" />


---

## 4. Configuración de Azure Static Web Apps

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

## Seguridad de la Aplicación

Se implementaron encabezados HTTP de seguridad mediante el archivo:

```text
staticwebapp.config.json
```

## Headers configurados

* **Content-Security-Policy:** Previene ataques XSS
* **Strict-Transport-Security:** Obliga uso de HTTPS
* **X-Content-Type-Options:** Evita MIME sniffing
* **X-Frame-Options:** Previene clickjacking
* **Referrer-Policy:** Protege la información del usuario
* **Permissions-Policy:** Restringe acceso a hardware del navegador

---

## Validación de seguridad

Se realizó un análisis en:

👉 https://securityheaders.com/

 Resultado obtenido:

* Calificación: **A / A+**
* Nivel de seguridad: Alto

---

##  URL Pública

La aplicación se encuentra disponible en:

```text
*👉 https://white-sand-0e6e6d40f.1.azurestaticapps.net/
```

---

##  Reflexión Técnica

La implementación de encabezados de seguridad permitió mitigar vulnerabilidades comunes como XSS, clickjacking y filtración de información. Además, se evidenció la importancia de integrar prácticas de seguridad desde la fase de despliegue y no como un proceso posterior.

El uso de **Microsoft Azure** facilitó la automatización del despliegue, demostrando cómo las herramientas modernas de DevOps permiten integrar desarrollo, despliegue y seguridad en un solo flujo de trabajo.

---

##  Conclusión

Se logró desplegar exitosamente una aplicación web en la nube, aplicando buenas prácticas de seguridad y automatización. Este proceso permitió fortalecer habilidades en despliegue, configuración de entornos y protección de aplicaciones web en escenarios reales.

---
