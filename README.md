# 🚀 Proyecto n8n Local con Docker y Node.js

Este repositorio contiene la configuración inicial para ejecutar **n8n** de forma local utilizando **Docker** y gestionarlo desde **Visual Studio Code**.  
La finalidad es disponer de un entorno de automatización rápido de levantar, portable y con datos persistentes en carpetas locales.

---

## 📌 Características principales
- Ejecución de **n8n** en contenedor Docker.
- Variables de entorno separadas en archivo `.env`.
- Persistencia de datos y logs en carpetas locales.
- Estructura optimizada para trabajar desde VS Code.
- Preparado para extender con scripts en **Node.js** que interactúen con la API REST de n8n.

---

## 🛠️ Requisitos previos

Antes de comenzar, asegúrate de tener instalado:

- [Docker Desktop](https://www.docker.com/products/docker-desktop)  
- [Git](https://git-scm.com/downloads)  
- [Visual Studio Code](https://code.visualstudio.com/)  
- Extensiones recomendadas en VS Code:
  - **Docker**
  - **Node.js Extension Pack**
- (Opcional) Cuenta en [GitHub](https://github.com/) para versionar el proyecto.

---

## 📂 Estructura de carpetas recomendada en VS Code

n8n-docker-local/
│
├── docker-compose.yml # Configuración del servicio n8n
├── .env # Variables de entorno
├── .gitignore # Archivos/carpetas que no se subirán a GitHub
│
├── data/ # Datos persistentes de n8n (Workflows, BD interna)
│ └── .gitkeep
│
├── logs/ # Logs generados por n8n
│ └── .gitkeep
│
└── node-scripts/ # Scripts Node.js para interactuar con la API de n8n
└── ejemplo.js


## 📷 **Evidencia visual de la estructura en VS Code:**  

<img width="902" height="496" alt="image" src="https://github.com/user-attachments/assets/ee12e078-00e8-4eee-bb7c-7163758c0982" />

---
## 📷 **Evidencia visual de como deberia verse la terminal para saber que Docker esta corriendo perfectamente:** 

<img width="1112" height="475" alt="image" src="https://github.com/user-attachments/assets/faee14dd-f88e-4a02-bfcd-cf040b46200c" />

---
## 🐳 Archivo docker-compose.yml
services:
  n8n:
    image: n8nio/n8n
    container_name: n8n_local
    ports:
      - "${N8N_PORT}:5678"
    environment:
      - N8N_BASIC_AUTH_ACTIVE=${N8N_BASIC_AUTH_ACTIVE}
      - N8N_BASIC_AUTH_USER=${N8N_BASIC_AUTH_USER}
      - N8N_BASIC_AUTH_PASSWORD=${N8N_BASIC_AUTH_PASSWORD}
      - GENERIC_TIMEZONE=${GENERIC_TIMEZONE}
    volumes:
      - ./data:/home/node/.n8n
    restart: unless-stopped
---

##  ▶️ Pasos para ejecutar n8n localmente
   1) Clonar este repositorio
      git clone https://github.com/TU_USUARIO/n8n-docker-local.git
      cd n8n-docker-local
   2) Levantar contenedor en tu terminal CMD: docker-compose up -d
      <img width="353" height="37" alt="image" src="https://github.com/user-attachments/assets/bd030750-4caa-465e-8503-64ba34c78de7" />
   3) Acceder desde el navegador: http://localhost:5678
      📷 Evidencia de n8n funcionando:
      <img width="1354" height="686" alt="image" src="https://github.com/user-attachments/assets/9297037b-2107-49d0-898a-22e4271e777a" />

## 📦 Dependencias utilizadas
  n8nio/n8n → Imagen oficial de n8n en Docker Hub.

  Docker → Para contenerización del servicio.

  Docker Compose → Para orquestar el contenedor.

  Node.js → Solo necesario si deseas añadir scripts que interactúen con la API REST de n8n.

  Git → Para control de versiones.

## 📄 Notas importantes
  La carpeta data/ contiene todos tus workflows y credenciales, no la borres.

  El archivo .env contiene credenciales, no lo subas a GitHub.

  Si el puerto 5678 está ocupado, cámbialo en .env.





