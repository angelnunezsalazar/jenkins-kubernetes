## Descripción de las imágenes

### Jenkins-Master
TBD

### Jenkins-Slave

- El master utiliza SSH para conectarse a este slave.
- Necesita una llave pública para iniciar (esta llave está en el 'docker-compose.yml')
- Tiene Docker client y accede al daemon del propio host:
  Ventajas:
  - Permite reutilizar las imágenes del host entre ejecuciones.
  - No se tiene que instalar todo el daemon en el esclavo.
  Desventajas:
  - Es complejo configurarlo.
- Tiene K8S Client

## Tareas Pendientes

- Probar que en K8S el contenedor esté accediendo al docker Daemon
- Autenticarnos con K8S utilizando las propias credenciales que ya están en los nodos.

## Referencias
- Cómo acceder al dar grant a jenkins para el docker daemon
https://github.com/jenkinsci/docker/issues/196
https://github.com/SvenDowideit/docs-automation/blob/master/jenkins/setup-docker-and-start-jenkins.sh
- Cómo montar el socker de docker al iniciar el contenedor
https://github.com/jenkinsci/docker-workflow-plugin/tree/master/demo