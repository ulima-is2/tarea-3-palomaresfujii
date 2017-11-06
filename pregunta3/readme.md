## Nodos - FrontEnd
- Clientes
<p> Visitantes de la página web que utilizan un browser</p>

- Application server FrontEnd#
<p>Los servidores que contienen la plataforma web. 
Dado que, se ejecuta código asíncrono es necesario Javacript + Ajax. 
Por otra parte, es necesario HTML5 + CSS para hacerlo responsive para pantallas de móviles. <p/>

## Nodos - BackEnd
La tecnología a utilizar es la arquitectura de referencia de Netflix. 
Dado que, es Open Source y facilita la escalabilidad es ideal para una startup como CineManzana.

- API Gateway Proxy & Router
<p>Es la puerta de entrada a las API proporcionando un punto de entrada a cada microservicio. 
Recibie un token del cliente OAuth y se comunica con el OAuth server. 
Por tanto, no permite que ninguna petición externa no autorizada pase a través de ella. 
También, utiliza puertos dinámicamente distribuidos para así evitar conflictos y minimizar la administración.
La tecnología a usar es Netflix Zuul que proporciona filtros para realizar funciones de monitoreo de peticiones,
enrutado dinámico, pruebas de estrés, manejo de respuestas estáticas, enrutado a través de regiones (AWS Regions).
Zuul se apoya en Netflix Ribbon para balancear la carga de peticiones entre los servicios disponibles.<p/>

- OAuth Authorization Server
<p>Se sigue el estándar OAuth 2.0 para la autorización de usuarios al sistema de servicios</p>

- Configuration Server
<p>Gestiona las configuraciones de los microservicios desde los entornos de desarrollo, test hasta producción 
de modo que tengan todo lo necesario para la migración.
Netflix Achaius permite transmitir "en caliente" los cambios que se generen en la configuración.</p>

- Discovery Service
<p>Permite a los microservicios registrarse a sí mismos en el momento en que inician su ejecución.
La tecnología a usar en Netflix Eureka. 
Esta se integra fácilmente con Netflix Ribbon, proporcionándole un cliente para el balanceo de carga por round-robin.</p>

- Monitoring Service
<p>Permite monitorear los microservicios.
Las tecnologías a usar son Netflix Hystrix Dashboard y Netflix Turbine. 
Hystrix Dashboard ofrece una vista de los circuit breakers y 
se complementa con Turbine para ofrecer una información completa de los servicios reconocidos por Eureka.</p>

- Centralized Log Analysis
<p>Permite registrar y analizar los eventos de los microservicios como logs.
Se utiliza uno de los stacks más populares, ELK (Elasticsearch, Logstash, Kibana)</p>
<p>Logstash: 
Es un agente que se encuentra en cada uno de nuestros componentes y 
que se dedica a realizar la trazabilidad de cada uno de ellos. Su trabajo es leer trazas, normalizarlas, 
estructurarlas y enviarlas al cluster de elasticsearch.</p>
<p>
Elasticsearch: 
Es un almacén distribuido de datos indexados que normalmente corre 
como un simple cluster. Su función es suministrar de datos a las consultas de Kibana.
</p>
<p>
Kibana: 
Es un servidor web que proporciona una interfaz gráfica de los logs. 
Se encarga de construir gráficos de las trazas obtenidas de las consultas de Elasticsearch. 
Se pueden hacer agregaciones complejas de datos con rangos de tiempo, etc.
</p>


