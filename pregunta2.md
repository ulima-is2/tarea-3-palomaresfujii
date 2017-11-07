# What I Wish I Had Known Before Scaling Uber to 1000 Services

La charla en cuestión trata acerca de recomendaciones que “le hubiera gustado recibir” antes y 
durante el proceso del increíble “scaling” que tuvo Uber.

Se comenta como aplican como por la naturaleza de su crecimiento, necesitan crear y 
dejar un buen número de servicios, para lo cual usan microservices que evitan tener “monolitos” en el sistema. 
Sin embargo, comenta algunas eventualidades resultado del uso y el incremento de los micro servicios, 
reconoce sus ventajas como agilidad e independencia de cada uno de los servicios, 
los códigos escritos por ti son tuyos, y los corres y pruebas tú mismo, o el “usar la mejor herramienta para el trabajo”.

Sin embargo, esto causa una serie de costos, sin necesidad de ser intencional, 
incurres en estos como “construir alrededor de los problemas”, problemas al hacer 
troubleshoot cuando hay problemas, y conservas Bias acerca de métodos y herramientas 
de trabajo, a detrimento del equipo en general. Hay muchos más problemas específicos, como:

- **Lenguaje**:
<p>Al ser todos estos microservicios de diferentes lenguajes, el compartir código, 
y cierta inflexibilidad entre equipos, aún más importante, se fractura la cultura 
pues los trabajas tienden a agruparse alrededor de los lenguajes  que emplean, separándose del resto.</p>

- **RPC**:
<p>“Todo se convierte en RPC”, en otras palabras, las comunicaciones en el equipo se limitan al empleo de RPC, 
lo que causa que el HTTP/REST se vuelva complicado, tienes problemas de interpretación, 
lo cual también afecta a los JSON usados, muestra que el “browser programing” 
cambia estas funcionalidades tan interesantes por problemas mayores a la larga 
“servers no son browsers”, es mejor tratar las comunicaciones como “function calls” y no como una especie de “request”.<p>

- **Repos**:
<p>También está el asunto de la cantidad de Repositorios a usar, ¿múltiples?, 
¿o un gran repo único?, ambas tienen beneficios, por ejemplo, tener múltiples 
ayuda a manejar módulos más pequeños, sin embargo, los repos únicos te permiten 
hacer cambios grandes a través de todo el programa, por ejemplo, haciendo cambios 
a través de 2 módulos al mismo tiempo. Sin embargo, crear un “Súper Repo”, causa 
que este sea tan grande que es casi imposible de revisar correctamente.Uber, 
por ejemplo, tiene alrededor de 8000 repositorios.</p>

- **Operacional**:
<p>En el deployment de los microservers, queda el problema de que, 
al cada uno de los equipos tener su propio ritmo, algunos pueden 
retener a otros equipos porque necesitan que el primer equipo 
despliegue su parte, lo que actúa en contraparte de la versatilidad de 
tener muchos equipos, hay que tener coordinación entre todos, recordar 
que todos son un gran equipo único, al final, todos trabajan en un solo proyecto que debe correr.</p>

- **Performance**: 
<p>Dada la cantidad de herramientas e idiomas, para entender que tal es el desempeño de 
cada uno de los microservicios, se necesitan diferentes formatos de perfilamiento, 
lo que no ayuda a uniformizar gráficos y representaciones entre los diferentes, 
lo que hace muy difícil el entender el real performance de cada servicio. 
Ha esto se incluyen los dashboards, que tienden a ser hechos con diferentes variables y 
métricas por equipo, por lo que es necesario crear un dashbord standard, y hecho automáticamente, 
lo que libera al equipo de tener que hacerlo y permite mejor entendimiento a la hora de revisar.</p>

<p>“El performance no es importante, hasta que lo es”, si no se tiene en cuenta el desempeño, 
eventualmente llegaran problemas, y si no se tuvieron medidas es muy probable que el problema se agrave, 
por lo que es recomendable tener al menos un standard vago con el cual poder tener al menos 
una net de seguridad con respecto al performance, no tiene que ser “bueno”, solo tienes que “saber”.</p>

- **Fanout**:
<p>El problema de latencia, hace que todo el proceso tenga que esperar hasta por el más lento 
de las partes del “call chain”, se trata de mantener cierto porcentaje de latencia, 
con el objetivo de reducir la cantidad de veces en las que se demora más de lo usual, 
para verificar problemas de demora, se usa tracing.</p>

- **Tracing**:
<p>Vitales, pues con ellos puedes seguir el camino de un request a través de la arquitectura, 
identificar la parte del proceso, o el proceso en específico que arrastra al resto de la operación 
y lo vuelve lento, sin embargo, también sirve para identificar problemas menos evidentes, 
como cuando aparentemente todos los servicios se están demorando más de lo usual, lo cual 
termina en un ”fanout  no-intencional”, solo encontrado por tracing.En otro ejemplo se ve 
como si bien los request fueron rápidos, se habían generado miles de request de base de 
datos de manera no intencional, obviamente teniendo impactos negativos sobre la velocidad. 
Como recomendación, se trata de hacer un tracing muy específico, solo un porcentaje estadístico, 
pues el tracear todo sería increíblemente laborioso y poco ventajoso, al mismo tiempo, 
es recomendable darle cierto contexto en las request, para poder entender mejor el tracing.</p>

- **Logging**:
<p>Otra vez, dado el problema de los diferentes lenguajes, añadiendo la rotación de personal, 
se necesita emplear el logging estructurado, no solo para mejorar el entendimiento, 
“logear demasiado” es un problema en sí, hay que tener alguna manera de contabilizar 
estos logs, pues algunas personas logean demasiada data, y el indexarlo se vuelve un problema mayor.</p>

- **Load Testing**:
<p>Para poder usar el “load testing”, caes en el problema de salirte de todas las métricas existentes, 
si quieres hacer “load testing” de producción, debes poder marcar que el trafico incrementado 
es una prueba, para que no se contabilice como algo real. Es increíblemente importante poder diseñar 
tus sistemas para que pueda manejar el tráfico de prueba.</p>

- **Failure testing**:
<p>El personal tiende a oponerse al “failure testing”, pues se sienten mal al ver su 
trabajo atacado con el objetivo de ver los fallos que tiene. Esto se tiene que enforzar, 
de todas maneras, así que se tiene que acostumbrar al personal a que suceda.</p>

- **Migraciones**:
<p>Hay que tener mucho cuidado con las cosas “legacy”, el migrar tecnologías es algo 
increíblemente importante y común, pues casi todo el mundo está en una constante actualización. 
Los “mandatos” a migración son malos, hacer cambios solo porque se necesita cambiar, y no por 
la utilidad empírica de una nueva tecnología es negativo, si no es por seguridad o compliance, 
no es bueno forzar el cambio.</p>

- **Open Source**:
<p>Cuando trabajas en plataforma y tiene que competir contra plataformas superiores compradas 
a exteriores al contrario de los productos hechos de manera privada, siempre habrá desmoralización 
y empleados que se sientan mal cuando vean que su esfuerzo y trabajo fue inútil al llegar los productos externos.</p>

- **Políticas**:
<p>Lo que nos lleva a las políticas, cuando usas microservicios, invitas a juego de política, 
cuando se toman decisiones que violan la propiedad de otros, cuando se pone al individuo sobre el equipo. 
A veces es difícil sobreponer el bien de la compañía sobre el unitario.</p>

Como regla ultima, se puede establecer que al final casi todo es un intercambio, 
tienes que sacrificar algunas cosas por otras, lo ideal es planificar y realizar es estos intercambios 
y sacrificios de manera intencional y planeada, jamás porque “no queda de otra”. 
La mejor manera de trabajar con los microservicios y sus falencias, es optimizar la 
manera en que miras estos “tradeoffs”, tratando de perder lo que te puedes dar el lujo 
de perder a cambio de funcionalidades con valor.
