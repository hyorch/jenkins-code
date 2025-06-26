VERSION=0.0.1

build:
	docker build -t jenkins-agent-docker:${VERSION} .

# login en dockerhub
login:
	docker login -u hyorch

#subir el contenedor a docherhub
push:
	docker tag jenkins-agent-docker:${VERSION} hyorch/jenkins-agent-docker:${VERSION}
	docker push hyorch/jenkins-agent-docker:${VERSION}

