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
