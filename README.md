# Introducción a Docker

Docker es una plataforma de contenedorización que permite empaquetar aplicaciones y sus dependencias en unidades portátiles y aisladas llamadas *contenedores*. Esto facilita la creación, distribución y ejecución de aplicaciones en entornos diversos, asegurando consistencia y reproducibilidad.

## ¿Por qué usar Docker?

* **Portabilidad:** Un contenedor Docker puede ejecutarse en cualquier sistema que tenga Docker instalado, sin importar la infraestructura subyacente.
* **Aislamiento:** Cada contenedor se ejecuta de manera independiente, evitando conflictos entre dependencias.
* **Eficiencia:** Docker comparte el kernel del sistema operativo anfitrión, lo que permite un uso más ligero de recursos comparado con las máquinas virtuales.
* **Escalabilidad:** Facilita la orquestación y el despliegue de múltiples contenedores en clústeres.

---

## Requisitos previos

* Sistema operativo compatible: Linux, Windows o macOS.
* Permisos de administrador o sudo.
* Conexión a Internet para descargar imágenes.

---

## Instalación de Docker

1. **Linux (Ubuntu):**

   ```bash
   sudo apt update
   sudo apt install docker.io
   sudo systemctl enable --now docker
   ```
2. **macOS y Windows:**

   * Descargar Docker Desktop desde [https://www.docker.com/get-started](https://www.docker.com/get-started)
   * Ejecutar el instalador y seguir las instrucciones.

Verifica la instalación con:

```bash
docker --version
```

---

## Conceptos básicos

* **Imagen:** Plantilla inmutable que contiene el sistema de archivos y configuración necesarios para crear contenedores.
* **Contenedor:** Instancia en ejecución de una imagen.
* **Dockerfile:** Archivo de texto con instrucciones para construir una imagen.
* **Registro (Registry):** Servicio para almacenar y distribuir imágenes (por ejemplo, Docker Hub).

---

## Comandos esenciales

| Comando                    | Descripción                            |
| -------------------------- | -------------------------------------- |
| `docker pull <imagen>`     | Descargar una imagen desde un registro |
| `docker images`            | Listar imágenes locales                |
| `docker run <imagen>`      | Ejecutar un contenedor                 |
| `docker ps`                | Listar contenedores en ejecución       |
| `docker ps -a`             | Listar todos los contenedores          |
| `docker stop <contenedor>` | Detener un contenedor                  |
| `docker rm <contenedor>`   | Eliminar un contenedor                 |
| `docker rmi <imagen>`      | Eliminar una imagen                    |

---

## Crear tu primera imagen

1. Crea un archivo `Dockerfile` en tu proyecto:

   ```Dockerfile
   FROM python:3.10-slim
   WORKDIR /app
   COPY . /app
   RUN pip install -r requirements.txt
   CMD ["python", "app.py"]
   ```
2. Construye la imagen:

   ```bash
   docker build -t mi-app:1.0 .
   ```
3. Ejecuta el contenedor:

   ```bash
   docker run --name contenedor-app -d mi-app:1.0
   ```

---

## Buenas prácticas

* Definir versiones explícitas en las imágenes base.
* Usar `.dockerignore` para excluir archivos innecesarios.
* Etiquetar imágenes (`tags`) de forma clara.
* Mantener capas ligeras y ordenadas en el Dockerfile.

---
