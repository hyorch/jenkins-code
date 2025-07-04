# Jenkins Configuration

- Install suggested plugins
- Install plugins:  Docker plugin(duda), BlueOcean, Pipeline Stage View, Docker pipeline(si docker local)
- SSH Keys. Administrar Jenkins -> Credentials -> Global -> SSH Username with private key

## Construir agente Jenkins con Docker

Generar agente Jenkins con capacidad para construir contenedores.

```Dockerfile
FROM jenkins/inbound-agent:latest

# Install Docker
USER root
RUN apt-get update && \
    apt-get install -y apt-transport-https ca-certificates curl gnupg2 software-properties-common lsb-release

RUN curl -fsSLo /usr/share/keyrings/docker-archive-keyring.asc \
  https://download.docker.com/linux/debian/gpg

RUN echo "deb [arch=$(dpkg --print-architecture) \
  signed-by=/usr/share/keyrings/docker-archive-keyring.asc] \
  https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list

RUN apt-get update && apt-get install -y docker-ce-cli docker-ce

# Configure Docker to run as non-root user
# Set the group ID for the docker group to match the host's docker group
RUN groupmod -g 1001 docker
RUN usermod -aG docker jenkins

# Install Docker Compose
RUN curl -L "https://github.com/docker/compose/releases/download/2.37.3/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && \
    chmod +x /usr/local/bin/docker-compose

# Enable DinD
RUN mkdir -p /var/lib/docker
VOLUME /var/lib/docker

USER jenkins
```
## Permisos /var/run/docker.sock
El usuario que ejecuta el agent de jenkins, ha de pertenecer al ID del grupo Docker del host que ejecuta Docker.


## Docker Permanent Agent
Ejecutar con docker-compose añadiendo las variables de URL, NAME y SECRET en el entorno para que conecte el agente al arrancar.



https://volito.digital/how-to-add-a-jenkins-agent-using-docker-compose/


## Docker Cloud
Crear cloud, tipo Docker, conectar a - /var/run/docker.sock:/var/run/docker.sock    

Si no está bien conectado el usuario jenkins del contendor con el grupo docker
```bash
sudo chmod 666 /var/run/docker.sock
```

- Error permisos socket
https://medium.com/igorgsousa-tech/docker-in-docker-with-jenkins-permission-problem-637f45549947


Añadir templates teniendo la imagen el agente de jenkins jenkins/inbound-agent:latest y una etiqueta para filtrar la imagen
```groovy
 agent {
        label 'docker-basic-agent' 
      
    }
```

### Template

- image: hyorch/jenkins-agent-docker:0.0.1

- Run container privileged


- Mounts: type=bind,src=/var/run/docker.sock,dst=/var/run/docker.sock







## +info

Crear imagen agente dind usando Cloud:
https://medium.com/@haroldfinch01/docker-in-docker-jenkins-agent-46014bfd3a03





https://medium.com/@lilnya79/integrating-docker-with-jenkins-20690bb7a146

sudo chmod 666 /var/run/docker.sock


Con docker instalado en Jenkins: https://www.jenkins.io/doc/book/pipeline/docker/
