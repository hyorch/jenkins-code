# Jenkins Configuration

- Install suggested plugins
- Install plugins:  Docker plugin(duda), BlueOcean, Pipeline Stage View, Docker pipeline(si docker local)
- SSH Keys. Administrar Jenkins -> Credentials -> Global -> SSH Username with private key

# Cloud
Crear cloud, tipo Docker, conectar a - /var/run/docker.sock:/var/run/docker.sock    
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

## Template

- image: hyorch/jenkins-agent-docker:0.0.1

- Run container privileged


- Mounts: type=bind,src=/var/run/docker.sock,dst=/var/run/docker.sock



## Permanent Agent
Ejecutar con docker-compose añadiendo las variables de URL, NAME y SECRET en el entorno para que conecte el agente al arrancar.



https://volito.digital/how-to-add-a-jenkins-agent-using-docker-compose/
# docs

Crear imagen agente dind usando Cloud:
https://medium.com/@haroldfinch01/docker-in-docker-jenkins-agent-46014bfd3a03





https://medium.com/@lilnya79/integrating-docker-with-jenkins-20690bb7a146

sudo chmod 666 /var/run/docker.sock


Con docker instalado en Jenkins: https://www.jenkins.io/doc/book/pipeline/docker/
