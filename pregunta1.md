# Microservices: Theory and application

## Teoría
### Introducción a la arquitectura

Los patrones de diseño se basa en la comunicación. Para aplicar un patrón de diseño es necesario comunicar y decidir en conjunto con el equipo de desarrollo qué patrón utilizar. Esto también es parte de una comunicación a alto nivel dentro del equipo para acordar qué hacer y qué diseño hacer para cumplir con los objetivos del proyecto. Al estar todos informados, la tasa de éxito se incrementa. Asimismo, se puede detectar errores de forma más ágil.

#### Sistemas monolíticos

Sistemas o aplicaciones grandes que realizan muchas funciones y es difícil su mantenimiento. Con el transcurrir del tiempo, el costo de mantener un sistema monolítico excede sus beneficios.

#### Microservicios

Separa las funciones de negocio en contextos delimitados, un contexto delimitado por servicio. 
Tiene las siguientes características:

- Es amigable para migraciones graduales. 
Sin embargo, la migración de sistemas monolíticos a microservicios toma tiempo.

- Agnóstico a la tecnología. 
Elimina la restricción de exclusividad de un lenguaje presente en un sistema monolítoco. Pues te permite agregar funcionalidades     desarrolladas en lenguajes diferentes según los objetivos del negocio.

- Es lo que debería tener una arquictectura de servicios.

##### Principios

Los principios más importantes son los primeros cuatro:

- Encapsulamiento
Es necesario aislar los servicios en contextos delimitados.

- Dominio céntrico. 
El encapsulamiento de cada servicio tiene que estar enfocado en un problema específico a solucionar, es decir, en un requerimiento.

- Independiente

- A prueba de fallos

Los últimos tres son más importantes para devOps:

- Automatización

- Descentralizado

- Observable

El principal impulso de los microservicios es ofrecer escalabilidad. Se puede ilutrar como un cubo de 3 ejes. El eje x implica la descomposición funcional del sistema o aplicación. Por otra parte, el eje y consiste en la redundancia de servidores, clusters, etc. Finalmente, el eje z muestra la fragmentacion de los datos en varios en nodos.

Los principios de desarrollo SOLID y DRY se alinean con las bases para microservicios. Principalmente, SOLID; en cambio, DRY no se cumple al 100% porque algunas partes tienen duplicidad en microservicios.

En un ambiente empresarial, más importante que la optimización del código, es la mantenbilidad.

Caracteristicas
Una arquictectura de microservicios incluye un API Gateway que distribuye las peticiones según sus necesidades a un conjunto de microservicios con más de 1 nivel de profundidad. Es decir, los servicios pueden estar compuestos por otros servicios.

### Acercamiento al éxito

Asimismo, las definiciones de éxito de un sistema son las siguientes:
- El software hace lo que debería hacer
- Se cumplen las necesidad de los usuarios
- Es seguro 
- Escalable. Puede soportar gran cantidad de usuarios
- Es tolerante a fallos
- Fácil de gestionar y lanzar
- Directo para realizar cambios
- Dentro del presupuesto
- A tiempo

Tener éxito implica conocer el negocio, tener una estructura organizativa dentro del equipo, definir el tamaño del código, del equipo, etc. Definir la tecnología, si esta se ajusta a los objetivos.

- Conocer el negocio consiste en dividir los problemas en partes más fáciles de gestionar. Se aplica el ciclo de vida software con la ayuda de diferentes metodologías ágiles.
Se evalúa el sistema de acuerdo a usabilidad e interacción por parte del usuario.
- Tener un estructura organizativa implica que los servicios pertenecen a un equipo y no por varios equipos. La simplicidad es la clave para tener éxito, por consiguiente, los patrones ayudan a lograr éxito

### Beneficios / retos
Rendimiento. Reducción del time to market

Satisfacer las expectativas más altas de los usuarios a través de la arquitectura como la escalabilidad, robustez, etc.

Más rápido de desplegar
Más fácil de probar
Más barato de escalar
Mejoramiento del aislamiento de fallos

Retos
Mayor complejidad en sistemas distribuidos
Sistema de pruebas por la interdependencia los servicios.
Transacciones distribuidas
Gestión del sistema
Se requiere mayor memoria
Organización y cultura
Madurez general

## Aplicación
### Tecnologías

CQRS(Command Query Responsability Segregation) El sistema se subdivide en 2 subsistemas: el de command, operaciones de escritura; y el de query, consultas.
Domain driven design Diseño guiado por el dominio. Se delimita el contexto del microservicio a su dominio.
Aprovisionamiento de eventos. Se almacena las acciones realizadas sobre el sistema de forma que garantice la trazabilidad y la contabilidad. Además, volver a recuperar un estado del sistema anterior
### Seguridad

