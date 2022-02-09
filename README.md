# -6.5-Curso-de-Bases-de-Datos-en-AWS

_____________________________________________________________________
![](https://static.platzi.com/media/courses/og-aws-database.png)
_____________________________________________________________________
### Introducción al documento
_____________________________________________________________________
El contenido de este documento esta basado en el curso del mismo nombre dictado por Mauro Parra Miranda en Platzi.
  
**Table of Contents**

[TOCM]

[TOC]

# 1. Qué aprenderás sobre bases de datos en AWS

Bienvenido al Curso de Bases de Datos en AWS de Platzi. Vamos a aprender sobre los servicios de bases de datos relacionales en AWS, principalmente el servicio de RDS, y sobre el servicio de bases de datos no relacionales en AWS: DynamoDB.

Esta vez nuestro profesor será Carlos Andrés Zambrano, que tiene más de 4 años de experiencia trabajando con AWS.

# 2. Características de Relational Database Service (RDS)

RDS (Relational Database Service) es un servicio de AWS enfocado a bases de datos relacionales con compatibilidad a 6 motores de bases de datos: Amazon Aurora, MySQL, MariaDB, PostgreSQL, Oracle y Microsoft SQL Server, cada uno con sus características, integraciones y limitaciones.

Entre sus características principales podemos destacar los backups automáticos con un tiempo de retención de hasta 35 días, es decir, si encontramos algún problema con nuestras bases de datos podemos restablecerlas a la hora, minuto y segundo que necesitemos dentro del periodo de retención. Recuerda que por defecto este periodo es de 7 días. También tenemos la opción de hacer backups manuales, podemos tomar snapshots manuales en cualquier momento si nuestra aplicación lo necesita. Además, AWS por defecto tomará un snapshot final de nuestras bases de datos antes de eliminarlas, así podremos restablecerla si tenemos algún inconveniente.

Todas las bases de datos relacionales utilizan un sistema de almacenamiento, si la carga de lectura y escritura son constantes, el sistema General Purpose funciona muy bien, sin embargo, podemos utilizar el sistema Provisioned Storage cuando requerimos de altas cantidades de consumo y operaciones de disco.

RDS es un sistema completamente administrado, esto quiere decir que AWS reduce nuestra carga operativa automatizando muchas tareas de nuestra base de datos, por ejemplo, las actualizaciones. A nivel de seguridad contamos con muchas opciones, una de ellas es la posibilidad de encriptar nuestra base de datos para que solo nosotros y las personas o roles que especifiquemos tengan acceso.

También tenemos integración con otros servicios de AWS, por ejemplo, IAM para administrar a los usuarios, roles, grupos y políticas de conexión a la base de datos por medio de tokens con máximo 20 conexiones por segundo (recomendado para escenarios de prueba), o la integración de Enhanced monitoring para hacer monitoreo en tiempo real nuestras bases de datos (recuerda que además de subir el precio, no está disponible para instancias small).

Lecturas recomendadas

https://docs.aws.amazon.com/rds/index.html

# 3. Desplegando nuestra primer base de datos

No me gusta Amazon, le da la espalda a estudiantes que quieren aprender y no tienen tarjeta de credito.

Si eres de Colombia, crea una cuenta de Daviplata (Por el celular lo puedes hacer), es facil de hacer. Cuando la crees, habrá una opción de crear una tarjeta virtual, no me acuerdo si debes meter dinero, pero no es demasiado, con 5000 o 10000 funciona. Cuando tengas la tarjeta, podras hacer el proceso de inscripción de AMAZON. Daviplata y la tarjeta virtual son cuentas aparte, eso creo.
Es posible que hallan actividades que necesiten hacer cosas de pago, pero trata de hacer todo con los servicios gratuitos. Lo importante es hacer lo que mas se pueda.

Todo lo contrario, sumado al comentario anterior se puede hacer esto para tener un mayor acceso
https://aws.amazon.com/education/awseducate/

# 4. Conexión gráfica a nuestra base de datos

En esta clase vamos a conectarnos a la base de datos que creamos en la clase anterior usando la herramienta MySQL Workbench, que nos permite ejecutar y visualizar nuestros comandos muy fácilmente.

Cuando utilizamos el servicio RDS con el motor de MySQL podemos crear multiples bases de datos con un solo endpoint (una sola conexión), ya que entre las características de este motor encontramos la cantidad de bases de datos ilimitada. Obviamente, debemos tener en cuenta que nuestras instancias deberían soportar la cantidad de bases de datos que vamos a utilizar, y las herramientas de monitoreo nos pueden ayudar a medir esta relación de tamaño y rendimiento.

Recuerda que si necesitamos un permiso de usuarios diferente para cada base de datos vamos a necesitar configuraciones diferentes en las keys (llaves de acceso) de nuestra instancia.

Lecturas recomendadas

MySQL :: MySQL Workbench

https://www.mysql.com/products/workbench/

# 5. Creación de una tabla

Tengan mucho cuidado con el presupuesto y especialmente con servicios como Glue, Kinesis y Managed Streaming for Apache Kafka. Yo estuve activa en la plataforma por 14 días mientras desarrollaba las actividades del curso y, al finalizar el mes, me generaron una factura por 785 dólares, por lo que me tocó abrir una disputa en AWS.

# 6. Conexión por consola a nuestra base de datos

En esta clase vamos a conectarnos a nuestra base de datos por medio del bash de Linux. Para esto, debemos crear la instancia de un servidor de AWS con un grupo de seguridad que posteriormente vamos a configurar para que la base de datos y el servidor sean accesibles entre ellos.

El desafió de esta clase es identificar al menos 2 características de RDS que actualmente no tenemos en otros sistemas bases de datos.

# 7. Base de Datos corporativa en RDS

¡Hola! Como primer proyecto para este curso vas a poner en práctica tus conocimientos para desplegar, conectar, consultar y recuperar una base de datos en RDS.

Eres el arquitecto de soluciones de una empresa y el CEO te ha pedido que despliegues una base de datos que contenga información de los trabajadores que ingresaron durante la primer semana del mes, la información es la siguiente:

Tabla # 1 - Trabajadores.

Captura de pantalla 2018-11-21 a la(s) 13.44.14.png
Despliega la Base de datos RDS (MySQL) y conéctate a través de MySQL Workbench.
Crea una tabla de trabajadores con los campos ID, Nombre, Fecha de Ingreso, Fecha de Nacimiento y Cargo.
Ingresa los datos mostrados en la tabla # 1 - Trabajadores.
Ahora conéctalos a la base de datos a través de una instancia EC2 usando la CLI y observa la tabla que creaste gráficamente.
Luego de haber creado la tabla, ingresó un empleado:
Juan Camilo Rodriguez.
Fecha de Ingreso → 10/10/2018
Fecha de Nacimiento → 25/08/1991
Cargo → Software Engineer Senior
Ingresar el registro del nuevo empleado.

Ahora quieres probar las funcionalidades de Backup de la base de datos y para eso, vas a restaurar la base de datos al momento anterior al cual agregaste el último ingreso (Juan Camilo Rodriguez).

Restaura la base de datos al momento anterior al ingreso del último usuario.
Consulta la tabla trabajadores y verifica su estado.
Verifica la tabla y evidencia que contenga solo los 5 registros iniciales.
Por último, envía un diagrama de arquitectura al CIO de la Base de Datos en Alta Disponibilidad y con optimización de performance.

# 8. Estrategias de backup

Los sistemas de backup manuales de RDS son completamente nuestra responsabilidad y debemos determinar cuándo tomar estos snapshots. Recuerda qué estos backups son incrementales, pueden mantener la información incluso cuando borramos la base de datos y nos permiten migrar la información entre diferentes regiones.

Por otra parte, los backups automáticos se hacen a diario, pero las operaciones de entrada y salida pueden quedar suspendidas por algunos segundos. Para solucionar este problema, es recomendado trabajar con despliegues Multi-AZ, que nos permiten utilizar una instancia de reserva de la base de datos cuando la instancia principal no se encuentra disponible.

El precio de nuestros backups depende de dos cosas: la retención (el tiempo que tenemos disponibles nuestros backups, máximo 35 días) y la cantidad almacenamiento que utilizamos (storage).

Lecturas recomendadas

Despliegues Multi-AZ de Amazon RDS

https://aws.amazon.com/es/rds/details/multi-az/

# 9. Demo estrategias de backup

# 10. Estrategias de performance en RDS

En esta clase vamos a aprender cómo identificar el rendimiento de nuestra base de datos, estrategias para mejorar su rendimiento actual y todas las opciones de performance de AWS.

A nivel de monitoreo, AWS nos provee un servicio llamado CloudWatch que nos permite visualizar los niveles de lectura, escritura, CPU, disco y memoria de la instancia dónde corre nuestra base de datos, también podemos analizar las métricas de conexiones para determinar la carga y la concurrencia de nuestras instancias.

La primer estrategia para mejorar el performance son las replicas de lectura, copias asíncronas de nuestra base de datos principal con un nuevo endpoint que vamos a utilizar solo en tareas de lectura, así obtenemos mucha más disponibilidad para tareas de escritura en nuestra base de datos principal. Recuerda que este servicio no esta disponible para los motores de Oracle y SQL Server.

También podemos mejorar el storage de nuestra base de datos utilizando provisioned iops para soportar altas operaciones de entrada y salida sobre la base de datos, principalmente para transacciones OLTP (OnLine Transaction Processing).

Existen otras alternativas como las bases de datos en memoria (ElastiCache, por ejemplo). Estas opciones resultan muy útiles para guardar la información más consultada en cache, así aliviamos un poco la carga de nuestra base de datos principal. Si estamos muy saturados y agotamos todas las opciones para mejorar el performance, la recomendación es dividir nuestra base de datos en otras más pequeñas.

# 11. Despliegues Multi AZ

El servicio de Multi AZ nos permite aumentar la disponibilidad de nuestro servicio realizando despliegues de nuestra base de datos en diferentes zonas. Cuando nuestra base de datos principal tenga problemas de disponibilidad, AWS automáticamente conectará nuestra aplicación con la base de datos replica en la segunda zona de disponibilidad. Recuerda que el precio de este servicio es equivalente a tener 2 bases de datos.

El desafío de esta clase es identificar un caso de uso en tu empresa, universidad o algún proyecto personal dónde podemos utilizar RDS, recuerda explicar cuál es la funcionalidad qué más llama tu atención y por qué.

# 12. Estrategias de migración a RDS

DMS (Database Migration Service) es un servicio de AWS que nos permite migrar nuestras bases de datos con otros motores al servicio de RDS u otros servicios de bases de datos en AWS.

Este servicio tiene las siguientes características:


 	-Podemos realizar migraciones de bases de datos on premise o en la nube a los servicios de bases de datos en AWS sin afectar el downtime de la base de datos que vamos a migrar.
 	-La carga de trabajo durante las migraciones es adaptable.
 	-Solo pagamos por los recursos que utilizamos en la migración.
 	-AWS administra la infraestructura necesaria para el trabajo de la migración, Hardware, Software, parches, etc.
 	-Conmutación por error automática, si AWS detecta un error en el proceso automáticamente creará una nueva instancia para remplazar la anterior, así el proceso de replicación no se ve afectado por estos problemas.
 	-Los datos en reposo están cifrados con KMS (Key Management Service) y la migración utiliza el protocolo de seguridad SSL.
  
# 13. Migraciones homogéneas y heterogéneas

Las migraciones homogéneas son migraciones donde la base de datos de origen y la de destino puede tener diferentes versiones del mismo motor, o son bases de datos compatibles entre sí (MySQL y Aurora, por ejemplo).

También podemos realizar migraciones heterogéneas, donde la base de datos de origen no es compatible con la de destino. Estas migraciones NO siempre son posibles, y antes de realizar la migración vamos a necesitar convertir el esquema de la base de datos con la herramienta AWS Schema Conversion Tool.

# 14. Casos de uso de RDS

# 15. Introducción a Aurora

Aurora es el motor de base de datos más robusto de AWS a nivel relacional. Entre sus características encontramos que AWS garantiza que utilizar Aurora nos asegura un performance 5 veces superior a MySQL y hasta 3 veces superior a PostgreSQL. También soporta hasta 64 TB de almacenamiento y 15 réplicas de lectura con niveles de latencia inferiores a 10 ms.

Cuando creamos una base de datos Aurora, realmente creamos un cluster de bases de datos compuesto por una instancia maestra y múltiples réplicas de lectura, todas desplegadas en diferentes zonas de disponibilidad dependiendo de la región que estamos utilizando.

Lecturas recomendadas

AdministraciÃ³n de un clÃºster de base de datos de Amazon Aurora - Amazon Aurora

https://docs.aws.amazon.com/es_es/AmazonRDS/latest/AuroraUserGuide/CHAP_Aurora.html

# 16. Características de Aurora

Además de ser una base de datos muy potente y robusta, Aurora nos permite un nivel de customización muy alto, puede crecer hasta 64 TB y nuestra data esta replicada en múltiples Az.

El endpoint de nuestra instancia principal nos permite conectarnos a la base de datos maestra y especificar las solicitudes de lectura y escritura, también tenemos endpoints para cada una de las replicas de lectura y un último endpoint a nivel de instancia que nos provee control sobre cargas de trabajo de la instancia principal y sus replicas, pero AWS nos recomienda NO utilizar este último endpoint de instancia.

Otras características de Aurora:

 	-Autoreparación: Guardar la información de la parte dañada en otra parte del disco y reparar el problema automáticamente.
 	-Cache Warm: Hacer un precalentamiento de la caché al iniciar las consultas más comunes y sus resultados.
 	-Recuperación de accidentes: Si falla la instancia principal, Aurora promueve una réplica de lectura o crea una nueva instancia principal.
Lecturas recomendadas

How to Stream Data from Amazon DynamoDB to Amazon Aurora using AWS Lambda and Amazon Kinesis Firehose | AWS Database Blog

https://aws.amazon.com/es/blogs/database/how-to-stream-data-from-amazon-dynamodb-to-amazon-aurora-using-aws-lambda-and-amazon-kinesis-firehose/

# 17. Aurora Serverless

Hasta el momento, la única base de datos relacional autoescalable que encontramos en el mercado es Aurora Serverless, una base de datos donde podemos seleccionar la mínima y máxima capacidad por instancia, a medida que la concurrencia sobre la base de datos va creciendo, esta capacidad mínima se incrementa hasta la capacidad máxima que nuestra aplicación debe soportar. Gracias a esto el precio de nuestros servicios disminuye, solo pagamos por el tiempo y la capacidad que realmente utilizamos.

Lecturas recomendadas

In The Works – Amazon Aurora Serverless | AWS News Blog

https://aws.amazon.com/es/blogs/aws/in-the-works-amazon-aurora-serverless/

# 18. Casos de uso de Aurora

Introducción a DynamoDB

# 19. Características de DynamoDB

DynamoDB es el servicio para bases de datos NOSQL de AWS completamente administrado (AWS se encarga de todo el background para que nosotros trabajemos nuestra aplicación), compuesto de varios nodos y distribuido en varias regiones (altamente disponible con replicación en diferentes locaciones), es una base de datos de baja latencia con almacenamiento en caché y es completamente escalable sin downtime de nuestra aplicación.

Este servicio se basa en dos conceptos importantes: las unidades en lectura (RCU, 4kb de bloques por segundo) y las unidades de escritura (WRU, 1kb de bloques por segundo). Con base en estos dos parámetros se determina el costo de nuestras bases de datos y el autoescalamiento.

La unidad fundamental de DynamoDB son las tablas, que están compuestas por items, que están compuestos por atributos (por ejemplo, la tabla trabajadores está compuesta por, trabajadores, cada uno con su nombre, edad, identificación y toda su información). También debemos entender los conceptos de partition key (llaves primarias para el espacio de almacenamiento) , sort keys (para organizar y ordenar la información) y local and global secondary index (otros atributos que podemos utilizar junto a las partition keys u otros atributos para obtener información más especifica y con mejor rendimiento).

Lecturas recomendadas

https://docs.aws.amazon.com/dynamodb/index.html#lang/es_es

https://docs.aws.amazon.com/dynamodb/index.html#lang/es_es

# 20. Consistencia en DynamoDB

La consistencia eventual de lectura NO puede mostrar los resultados de una tarea de escritura reciente cuando consultamos una tabla recién actualizada, además, consume los 4kb de bloques por segundo en las unidades de lectura.

Por otra parte, la consistencia fuerte de lectura funciona correctamente cuando consultamos una tabla y recibimos la respuesta más reciente, pero consume el doble que la consistencia eventual, así que será más costosa. Este tipo de consistencia es el adecuando para aplicaciones y casos de uso muy específicos donde la consulta y la escritura deben estar tan sincronizadas como sea posible.

# 21. Creando nuestra primer tabla en DynamoDB

# 22. Casos de uso en DynamoDB

El servicio de DynamoDB es muy útil en los siguientes casos:

Aplicaciones móviles

 	-Internet de las cosas (IoT, gracias al real time y su capacidad para ingesta de información)
 	-Aplicaciones Web
 	-Gaming (gracias a su alta disponibilidad, conexión y por ser no relacional)
 	-Manejo de sesiones
 	-RealTime (ya que no solo nos permite almacenar nuestra información, también podemos utilizar toda la data en tiempo real para alimentar otros servicios y generar otras arquitecturas)
  
-------

# Particiones e índice en dynamoDb

# 24. Índices y particiones en DynamoDB

Cuando utilizamos DynamoDB los datos se almacenan en particiones, al crear una tabla, la base de datos asigna su partición para que esta pueda satisfacer el desempeño aprovisionado, y en ciertas ocasiones puede aumentar el tamaño y la cantidad de particiones para mejorar el desempeño o cuando la partición está llena. El limite de las particiones es 10GB de almacenamiento, pero también necesitamos cambiar de partición cuando superamos los niveles de lectura y escritura (3.000 RCU y 1.000 WCU).

DynamoDB utiliza las claves principales simples y compuestas para almacenar y recuperar nuestros elementos y almacenar nuestra información con la función de hash. Cuando utilizamos claves compuestas debemos especificar los valores de la clave para leer los elementos, y el orden de los elementos depende de su clave de ordenación.

La base de datos esta optimizada para distribuir nuestros elementos de forma uniforme entre las particiones de una tabla, con independencia del número de particiones que configuramos. Sin embargo, la recomendación oficial es elegir una clave de partición con un amplio abanico de valores diferentes, es decir, claves tan aleatorias como sea posible en relación con el número de elementos de la tabla, así evitamos que la información se guarde en particiones cercanas o iguales para optimizar las tareas de lectura y escritura de la base de datos.
  
# 23. Base de Datos corporativa para encuestas en DynamoDB

¡Hola! Con este segundo proyecto del curso vas a aprender a poder poner en práctica tus conocimientos en la creación, configuración y conexión a tabla de DynamoDB.

Eres el arquitecto de soluciones de una empresa y el Director de Marketing le ha pedido que debe desplegar una base de datos en la cual se almacenen las respuestas de una encuesta de clima organizacional realizada a los trabajadores de la empresa.

La encuesta tiene 5 preguntas:
Pregunta 1 - ¿Cuál es su antigüedad en la empresa?
Pregunta 2 - ¿Está satisfecho con su asignación salarial?
Pregunta 3 - ¿Está contento con su posición actual?
Pregunta 4 - ¿Quién es su jefe inmediato?
Pregunta 5 - ¿Qué sugerencias tiene para la empresa?.

Screen Shot 2018-11-22 at 9.41.02 AM.png
Crea una tabla en DynamoDB con encriptación habilitada en la cual guardes las respuestas de los 5 trabajadores.
Configura la tabla con clave principal el ID EMPLEADO.
Haz una consulta a la tabla para identificar los trabajadores que en la pregunta 2 respondieron “No”.
Teniendo la tabla actual, tú como arquitecto ¿cuál considerarías que sería un buen índice secundario para agregar a la tabla?
No olvides compartir tus resultados, desafíos y aciertos en el panel de discusiones.

# 25. Operaciones Scan en DynamoDB

Las Operaciones Scan se encargan de escanear por completo nuestras tablas para examinar todos sus elementos y comprobar si presentan los valores solicitados, pero son muy poco eficientes ya que utilizan bastantes unidades de lectura y aumentan los costos de nuestra base de datos, debemos evitar estas operaciones para tablas grandes.

AWS nos recomienda realizar operaciones pequeñas a lo largo del tiempo en vez de hacer una sola operación muy larga, también podemos configurar límites de tamaño para evitar los escaneos completos y duplicar nuestras tablas para realizar estas operaciones sobre tablas no principales y no afectar su rendimiento.

# 26. Operaciones Query en DynamoDB

Las Operaciones Query (operaciones de consulta) nos permiten buscar elementos en cualquier tabla o índice secundario en base a su clave principal compuesta para optimizar la petición.

En vez de escanear toda la tabla (como en las operaciones Scan), vamos a especificar los criterios de búsqueda utilizando una expresión de condición clave (una cadena que determina los elementos que vamos a leer en la tabla o el índice), especificamos el nombre y valor la clave de partición como una condición de igualdad, podemos realizar consultas utilizando diferentes operadores para encontrar los resultados con mejor precisión.

También podemos limitar el número de elementos que esperamos en los resultados para agilizar las operaciones, pero no obtenemos información tan detallada de la capacidad de lectura que consumimos.

El desafío de esta clase es responder en la sección de comentarios un caso de uso de DynamoDB y cuáles serian sus ventajas frente a los servicios RDS.

# 27. Demo de operaciones Scan y Query en DynamoDB

# 28. ¿Qué es Local Seconday Index?

En una tabla de Dynamo cada ítem debe contener una clave primaria única. Esta llave debe tener una clave de partición y opcionalmente puede tener una range key (Sort Key). Dentro de la partición, los ítems son ordenados por la range key, en los casos donde la información que necesitemos coincida con nuestra range key el acceso a los elementos va a ser mucho más rápido.

En una tabla de Dynamo cada ítem debe contener una clave primaria única. Esta llave debe tener una clave de partición y opcionalmente puede tener una range key (Sort Key). Dentro de la partición, los ítems son ordenados por la range key, en los casos donde la información que necesitemos coincida con nuestra range key el acceso a los elementos va a ser mucho más rápido.

Por ejemplo si tenemos la una tabla que mantiene el puntaje de jugadores en diferentes juegos online.

La tabla Scores está conformada de la siguiente forma:

Llave de partición: GameName → Nombre del Juego

Llave de ordenamiento (Range o Sort Key): LastGameMatch → Fecha de la última partida disputada en el juego.

Para la tabla SCORE podríamos obtener información de los juegos y la fecha de la última partida disputada en el juego por diferente usuario.

Ahora supongamos que necesitamos responder preguntas diferentes como:

¿Cuál es el puntaje máximo en un determinado juego?

¿Cuál es la partida ganada más antigua en el juego?

No sería posible obtener la información solicitada con los índices que se tienen actualmente, tendríamos que hacer una operación SCAN que consumiría muchas unidades de lectura.

Para este caso la mejor solución sería utilizar LSI:

Para este caso la mejor solución sería utilizar LSI:

GameName y Score.

GameName y LastWin.

Con estos LSI podríamos consultar la data con la misma llave de partición (GameName) y obtener resultados sobre otras llaves range como Score y LastWin. Esto nos ayudaría en nuestra tabla a obtener los datos que necesitamos de forma más eficiente y también evitamos el consumo de unidades de lectura de la tabla RCU lo cual se verá reflejado en un ahorro de costos.

# DynamoDB Streams y Replicación

# 29. Características Streams y Replicación en DynamoDB

DynamoDB Streams nos proporciona una secuencia ordenada por tiempo de cambios de los elementos de cualquier tabla, es decir, guarda los cambios de nuestros elementos para que podamos procesar y consumir esta información, podemos ampliar el poder de DynamoDB con replicación entre regiones, análisis continuo con integración a Redshift, notificación de cambios y muchos otros escenarios.

Estos streams capturan una secuencia en orden cronológico de las modificaciones de los elementos de una tabla y almacenan la información por 24 horas. Cada registro de secuencia contiene la información sobre una sola modificación a los datos de un elemento de la tabla. Nuestras aplicaciones pueden obtener acceso a este registro y ver los elements de datos tal y como se encontraban antes y después.

# 30. Casos de uso Streams y Replicación en DynamoDB

# 31. DAX: DinamoDB Accelerator
DAX (DynamoDB Accelerator) es un cluster de caché completamente administrado por AWS y de alta disponibilidad para DynamoDB con un rendimiento de hasta 10 veces superior (de milisegundos a microsegundos) y soporta millones de solicitudes por segundo.

Entre sus características encontramos la encriptación en reposo, podemos utilizar hasta 10 nodos y se puede seleccionar la zona de disponibilidad donde se desplegará el cluster. Podemos utilizar instancias small y medium para cargas de prueba, de resto todas son de tipo R (optimizadas en memoria).

# 32. Conclusiones

¡Felicitaciones por terminar el curso! Aprendimos sobre los servicios de bases de datos relacionales y no relacionales en AWS, sus principales características, diferencias y casos de uso. Ahora tienes el criterio necesario para decidir cuándo utilizar estos servicios.

Conclusiones del servicio RDS:

 	-Siempre que desplegamos bases de datos en producción es muy recomendado utilizar los despliegues en diferentes zonas con el servicio Multi AZ.
 	-Tenemos diferentes estrategias para optimizar el performance de nuestra base de datos, por ejemplo, implementar réplicas de lectura, utilizar bases de datos en memoria y dividir la base de datos en otras más pequeñas.
 	-El periodo de retención de los backups de nuestra base de datos son máximo 35 días.
 	-Debemos tener en cuenta los tipos de migración (homogéneas y heterogéneas) cuando vamos a migrar nuestra base de datos.
 	-AuroraDB es la base de datos más robusta y potente para grandes cargas de trabajo de AWS, también es la única con servicio de serverless y autoescalamiento.
Conclusiones del servicio DynamoDB:

 	-Es recomendado evitar las operaciones Scan para no afectar la capacidad aprovisionada, en cambio, las operaciones Query funcionan mucho mejor para el rendimiento de la base de datos.
 	-La función de autoscaling se puede programar con lectura y escritura pero debemos tener en cuenta los costos.
 	-Es clave elegir una llave principal adecuada para no afectar el performance de nuestra base de datos, entre más aleatoria sea este valor, mejor será el rendimiento.
 	-Con DynamoDB Streams podemos crear arquitecturas en tiempo real para diferentes aplicaciones.
 	-Cuando tenemos una tabla muy grande, configurar el particionamiento y los límites del mismo son fundamentales.

