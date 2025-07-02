# Creación de un Entorno Multi-Contenedor

- Docker build

![alt text](<images/docker build1.png>)

- Listado de contenedores

![alt text](<images/docker ps.png>)

- Conewxion con Postgress

![alt text](<images/docker postgress.png>)

- Docker desktop

![alt text](<images/docker postgress.png>)

- App corriendo desde docker

![alt text](<images/app corriendo.png>)

### ¿Cuál es la diferencia entre una imagen y un contenedor? 
Una imagen es una plantilla que incluye el sistema operativo, las dependencias, configuraciones y todo lo necesario para crear un entorno específico.

Por otro lado, un contenedor es una instancia en ejecución de esa imagen, un entorno aislado y temporal donde se ejecuta la aplicación.
 
### ¿Qué beneficios aporta Docker Compose frente a ejecutar contenedores por separado? 
Es posible automatizar y organizar el funcionamiento de múltiples contenedores a la vez e incluso configurarlos para trabajar en conjunto.

### ¿Qué mecanismos de seguridad podrías aplicar en esta arquitectura? 
Utilizar variables de entorno secretas para la configuración de base de datos.
Evitar exponer la base de datos integrando una configuración más segura.
Comprobar siempre que las dependencias utilizadas no tengan vulnerabilidades.

### ¿Cómo podrías extender este entorno para simular una app completa?

Separando las funcionalidades en distintos contenedores, se agrega uno para la API que actúa como backend y se conecta a la base de datos existente. El contenedor de PostgreSQL se mantiene para la persistencia de datos, y Nginx continúa sirviendo el frontend estático. Además, se puede incluir un contenedor que consuma la API desde el frontend, y otro opcional para integrar APIs externas si es necesario. Esta estructura mejora la organización, facilita el mantenimiento y permite escalar cada componente por separado.

### Una breve explicación de cómo se comunican los servicios entre sí.

En el código inicial, los servicios definidos en el archivo docker-compose.yml se comunican entre sí mediante una red creada por Docker Compose. Al estar dentro de la misma red, los contenedores pueden resolverse por el nombre del servicio especificado en el archivo, lo que permite que el contenedor nginx acceda al servicio PostgreSQL sin configuración adicional de red ni exposición de puertos entre ellos.
