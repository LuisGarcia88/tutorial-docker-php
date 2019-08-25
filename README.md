# Tutorial: Como generar una imagen Docker
## Descripción
Docker es una forma de distribuir aplicaciones, donde todas las dependencias, 
librerías y código están contenidas en una imagen Docker que puede ser ejecutada
en cualquier servidor que tenga el servicio de **Docker Engine**.

El servicio usado para almacenar las imágenes Docker es llamado **Docker Registry**.
[Docker Hub (docker.io)](https://hub.docker.com/) es un servicio gratuito para almacenar imágenes publicas. 

## Crear el Dockerfile
Para generar una imagen Docker, lo primero es crear el archivo Dockerfile, El cual
lleva la todas las instrucciones necesarias para generar la imagen Docker.

Puedes consultar el archivo Dockerfile [aquí](./Dockerfile). 

## Generar imagen - docker build
El comando **docker build** genera la imagen Docker:
```bash
docker build -t ${IMAGE_NAME}:${TAG} .

# Ejemplo, el comando genera una imagen de nombre 'tutorial-docker-php' y tag 'v1.0':
docker build -t tutorial-docker-php:v1.0 .
```

## Listar imágenes - docker images
El comando **docker images** muestra las imágenes existentes.
Puede usarse para confirmar el nombre de una imagen:
```bash
docker images
```

## Generar tag - docker tag
El comando **docker tag** permite especificar la ruta y nombre de una imagen Docker:
```bash
docker tag ${IMAGE_NAME}:${TAG} ${DOCKER_REGISTRY}/${REPOSITORY}:${TAG}

# Ejemplo
docker tag tutorial-docker-php:v1.0 docker.io/inetshelldocs/tutorial-docker-php:v1.0

# Si se utiliza Docker Hub, se puede omitir la dirección 'docker.io'
docker tag tutorial-docker-php:v1.0 inetshelldocs/tutorial-docker-php:v1.0
``` 

## Iniciar sesión en Docker Registry - docker login
El comando **docker login** inicia sesion al Docker Registry:
```bash
docker login ${DOCKER_REGISTRY} --username=${USER}

# Ejemplo
docker login docker.io --username=inetshell
```

## Subir imagen - docker push
El comando **docker push** sube la imagen al Docker Registry:
```bash
docker push ${DOCKER_REGISTRY} --username=${USER}

# Ejemplo
docker login docker.io --username=inetshell
```
## Descargar imagen - docker pull
## Referencias
1. [Dockerfile](https://docs.docker.com/engine/reference/builder/)
2. [docker build](https://docs.docker.com/engine/reference/commandline/build/)
3. [docker tag](https://docs.docker.com/engine/reference/commandline/tag/)