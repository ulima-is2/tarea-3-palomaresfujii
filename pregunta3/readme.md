## Nodos - FrontEnd
- **Clientes**
<p> Visitantes de la página web que utilizan un browser</p>

- **Balanceador de carga**
<p>Para garantizar la disponibilidad de la página web se utiliza balanceadores de carga utilizando round robin.
La tecnología a usar es Netflix Ribbon que proporciona una librería IPC (Inter process calls). Esta proporciona
el balanceo en el cliente, la tolerancia a fallos, soporte a múltiples protocolos (HTTP, TCP, UDP) 
en modelo asíncrono y reactivo, y caching.</p>

- **Application server FrontEnd#**
<p>Los servidores que contienen la plataforma web. 
Dado que, se ejecuta código asíncrono es necesario Javacript + Ajax. 
Por otra parte, es necesario HTML5 + CSS para hacerlo responsive para pantallas de móviles. <p/>

## Nodos - BackEnd
La tecnología a utilizar es la arquitectura de referencia de Netflix. 
Dado que, es Open Source y facilita la escalabilidad es ideal para una startup como CineManzana.

- **API Gateway Proxy & Router**
<p>Es la puerta de entrada a las API proporcionando un punto de entrada a cada microservicio. 
Recibie un token del cliente OAuth y se comunica con el OAuth server. 
Por tanto, no permite que ninguna petición externa no autorizada pase a través de ella. 
También, utiliza puertos dinámicamente distribuidos para así evitar conflictos y minimizar la administración.
La tecnología a usar es Netflix Zuul que proporciona filtros para realizar funciones de monitoreo de peticiones,
enrutado dinámico, pruebas de estrés, manejo de respuestas estáticas, enrutado a través de regiones (AWS Regions).
Zuul se apoya en Netflix Ribbon para balancear la carga de peticiones entre los servicios disponibles.<p/>

- **OAuth Authorization Server**
<p>Se sigue el estándar OAuth 2.0 para la autorización de usuarios al sistema de servicios</p>

- **Configuration Server**
<p>Gestiona las configuraciones de los microservicios desde los entornos de desarrollo, test hasta producción 
de modo que tengan todo lo necesario para la migración.
Netflix Achaius permite transmitir "en caliente" los cambios que se generen en la configuración.</p>

- **Discovery Service**
<p>Permite a los microservicios registrarse a sí mismos en el momento en que inician su ejecución.
La tecnología a usar en Netflix Eureka. 
Esta se integra fácilmente con Netflix Ribbon, proporcionándole un cliente para el balanceo de carga por round-robin.</p>

- **Monitoring Service**
<p>Permite monitorear los microservicios.
Las tecnologías a usar son Netflix Hystrix Dashboard y Netflix Turbine. 
Hystrix Dashboard ofrece una vista de los circuit breakers y 
se complementa con Turbine para ofrecer una información completa de los servicios reconocidos por Eureka.</p>

- **Centralized Log Analysis**
<p>Permite registrar y analizar los eventos de los microservicios como logs.
Se utiliza uno de los stacks más populares, ELK (Elasticsearch, Logstash, Kibana)</p>
<p><b>Logstash</b>: 
Es un agente que se encuentra en cada uno de nuestros componentes y 
que se dedica a realizar la trazabilidad de cada uno de ellos. Su trabajo es leer trazas, normalizarlas, 
estructurarlas y enviarlas al cluster de elasticsearch.</p>
<p>
  <b>Elasticsearch</b>: 
Es un almacén distribuido de datos indexados que normalmente corre 
como un simple cluster. Su función es suministrar de datos a las consultas de Kibana.
</p>
<p>
<b>Kibana</b>: 
Es un servidor web que proporciona una interfaz gráfica de los logs. 
Se encarga de construir gráficos de las trazas obtenidas de las consultas de Elasticsearch. 
Se pueden hacer agregaciones complejas de datos con rangos de tiempo, etc.
</p>

- API **User** Command
<p>Es el microservicio que permite realizar operaciones de escritura para el recurso <b>usuario</b>
Se utiliza tecnología Django-Rest-Framework, Django en Python porque es lo único que el dev team conoce</p>

- API **User** Query
<p>Es el microservicio que permite realizar consultas para el recurso <b>usuario</b>
Se utiliza tecnología Django-Rest-Framework, Django en Python porque es lo único que el dev team conoce</p>

- API **Encargado** Command
<p>Es el microservicio que permite realizar operaciones de escritura para el recurso <b>encargado</b>
Se utiliza tecnología Django-Rest-Framework, Django en Python porque es lo único que el dev team conoce</p>

- API **Encargado** Query
<p>Es el microservicio que permite realizar consultas para el recurso <b>encargado</b>
Se utiliza tecnología Django-Rest-Framework, Django en Python porque es lo único que el dev team conoce</p>

- API **Cliente** Command
<p>Es el microservicio que permite realizar operaciones de escritura para el recurso <b>cliente</b>
Se utiliza tecnología Django-Rest-Framework, Django en Python porque es lo único que el dev team conoce</p>

- API **Cliente** Query
<p>Es el microservicio que permite realizar consultas para el recurso <b>cliente</b>
Se utiliza tecnología Django-Rest-Framework, Django en Python porque es lo único que el dev team conoce</p>

- API **Compra** Command
<p>Es el microservicio que permite realizar operaciones de escritura para el recurso <b>compra</b>
Se utiliza tecnología Django-Rest-Framework, Django en Python porque es lo único que el dev team conoce</p>

- API **Compra** Query
<p>Es el microservicio que permite realizar consultas para el recurso <b>compra</b>
Se utiliza tecnología Django-Rest-Framework, Django en Python porque es lo único que el dev team conoce</p>

- API **Funcion** Command
<p>Es el microservicio que permite realizar operaciones de escritura para el recurso <b>funcion</b>
Se utiliza tecnología Django-Rest-Framework, Django en Python porque es lo único que el dev team conoce</p>

- API **Funcion** Query
<p>Es el microservicio que permite realizar consultas para el recurso <b>funcion</b>
Se utiliza tecnología Django-Rest-Framework, Django en Python porque es lo único que el dev team conoce</p>

- API **Pelicula** Command
<p>Es el microservicio que permite realizar operaciones de escritura para el recurso <b>pelicula</b>
Se utiliza tecnología Django-Rest-Framework, Django en Python porque es lo único que el dev team conoce</p>

- API **Pelicula** Query
<p>Es el microservicio que permite realizar consultas para el recurso <b>pelicula</b>
Se utiliza tecnología Django-Rest-Framework, Django en Python porque es lo único que el dev team conoce</p>

- API **Sala** Command
<p>Es el microservicio que permite realizar operaciones de escritura para el recurso <b>sala</b>
Se utiliza tecnología Django-Rest-Framework, Django en Python porque es lo único que el dev team conoce</p>

- API **Sala** Query
<p>Es el microservicio que permite realizar consultas para el recurso <b>sala</b>
Se utiliza tecnología Django-Rest-Framework, Django en Python porque es lo único que el dev team conoce</p>

- API **Cine** Command
<p>Es el microservicio que permite realizar operaciones de escritura para el recurso <b>cine</b>
Se utiliza tecnología Django-Rest-Framework, Django en Python porque es lo único que el dev team conoce</p>

- API **Cine** Query
<p>Es el microservicio que permite realizar consultas para el recurso <b>cine</b>
Se utiliza tecnología Django-Rest-Framework, Django en Python porque es lo único que el dev team conoce</p>

- API **Cadena** Command
<p>Es el microservicio que permite realizar operaciones de escritura para el recurso <b>cadena</b>
Se utiliza tecnología Django-Rest-Framework, Django en Python porque es lo único que el dev team conoce</p>

- API **Cadena** Query
<p>Es el microservicio que permite realizar consultas para el recurso <b>cadena</b>
Se utiliza tecnología Django-Rest-Framework, Django en Python porque es lo único que el dev team conoce</p>

- **API Facebook**
<p>Es el API de Facebook que permite al sistema interactuar con esta red social.</p>

- **API Twitter**
<p>Es el API de Twitter que permite al sistema interactuar con esta red social.</p>

- **DB Server**
<p>Es el servidor de base de datos. 
  Se utiliza MongoDB porque permite data sharding en cluster con un modelo de escalamiento horizontal.
Lo cual facilita la satisfacción del objetivo de CineManzana de ofrecer una alta disponiblidad de sus servicios a sus clientes.</p>

## Componentes - Backend

Se utilizan en más de un nodo.

- **Circuit Breaker**
<p>Se utiliza la librería Netflix Hystrix que se ejecuta embebido dentro del consumidor del servicio. 
Está diseñado para dar control sobre la latencia y fallos 
de las dependecias entre servicios, parar los errores en cascada en el sistema, 
recuperación rápida antes fallos y monitoreo en tiempo real.</p>



