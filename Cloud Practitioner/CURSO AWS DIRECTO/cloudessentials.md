# AWS Cloud Practitioner Essentials

- EC2 Works for Server side
> EC2 is Elastic Cloud Compute, an AWS Service

Pay-as-you-go / Pay-for-use: paying just for the resources that you gonna use

Cloud computing: The on-demand delivery of IT Resources over the internet with a pay-as-you-go pricing.
> El objetivo de los cloud services es ofrecer toda la infraestructura de IT para que tú únicamente centres tu negocio en los contenidos que se hacen dentro de esa infraestructura pagando únicamente por los recursos que utilizas en el momento exacto en que los utilizas.

---

## Introduction to Amazon EC2

EC2 are virtual servers managed by Amazon, you can enter your request of the number of resources that you need instead of having a physical server running 24/7.

- Hypervisor: el software encargado de compartir o aislar los recursos entre VMs. Coordina el multitenancy.
- Multitenancy: Sharing underlying hardware between virtual machines.

Las instancias son seguras, ya que no se enteran entre ellas que existen, incluso si comparten recursos.

EC2 proporciona gran flexibilidad y control, también en la configuración de tus instancias.
- Puedes escoger el OS (Windows y Linux), que software quieres corriendo (programas de la empresa, web apps, databases, software de terceros, etc).
- Tienes completo control de qué corre en tu instance de EC2.

**Vertical Scaling**: que le puedas añadir más recursos a esa instancia en el momento que tú decidas. Incluso quitarle recursos.

- También puedes limitar los recursos de red de la instancia.

### Inconvenientes de usar On-premises servers

- Spend money upfront to purchase hardware.
- Wait for the servers to be delivered to you.
- Install the servers in your physical data center.
- Make all the necessary configurations.

### Ventajas de usar EC2

- You can provision and launch an Amazon EC2 instance within minutes.
- You can stop using it when you have finished running a workload.
- You pay only for the compute time you use when an instance is running, not when it is stopped or terminated.
- You can save costs by paying only for server capacity that you need or want.


### Cómo funciona EC2

- **Launch**: Lanzas una instancia, escogiendo una plantilla con configuraciones predenterminadas con componentes básicos, como el OS, las aplicaciones que va a llevar instaladas, el tipo de uso que se le va a usar, etc. También puedes escoger el *instance type* que hace referencia a la configuración de hardware que va a llevar el instance de EC2. Y también se puede especificar la configuración de seguridad y el tráfico de red que fluye en dicha instancia.
- **Connect**: Conectarse a la instancia, te puedes conectar a ella de diferentes formas, ya que esta cuenta con aplicaciones y configuraciones para conectarse e intercambiar datos. Los usuarios también pueden conectarse directamente loggeándose y accesando al escritorio.
- **Use**: Después de conectarse a la instancia, puedes empezar a usarla. Puedes correr comandos para instalar software, añadir almacenamiento, copiar y organizar archivos, etc etc.

---

## Amazon EC2 Instance types

Each EC2 instance type is grouped under an instance family. Cada una especializada en una tarea en concreto.
Cada tipo tiene una configuración distinta de CPU, RAM, almacenamiento y capacidades de red, dándote la capacidad específica para tus aplicaciones.

Las distintas familias de instances son:

- General purpose
1. Balanced resources
2. Diverse workloads (web servers or code repositories)
3. Small and medium databases

- Compute optimized
1. Compute intensive tasks (Gaming servers, High performance computing or scientific modeling)

- Memory optimized
1. Memory intensive tasks
2. Databases
3. Carga de trabajo que implique mucho uso de memoria ram

- Accelerated computing
1. Floating point number calculations
2. Graphics processing
3. Data pattern matching
4. Utilize hardware accelerators
5. Streaming de videojuegos y películas

- Storage optimized
1. High performance for locally storaged data
2. Read and write secuential data
3. Data warehousing applications (aplicaciones de almacenamiento de datos)
4. Distribución de datos
5. High-frecuencly Online Transaction Processing (OLTP) systems
6. **IOPS**: término para input/output operations per second, métrica que mide el rendimiento de un dispositivo de almacenamiento.


—

## Amazon EC2 Pricing

Para EC2 hay dos principales modos de cobro y presupuesto para EC2:

1. On-Demand: solo pagas por la duración del uso de tu instancia, por hora o segundo y variando del OS que usas. No necesitas hablar con Amazon para comenzar a usarlo. Puedes usarlo como una vara con la que medir tus costes.
    * Ideales para uso corto, carga de trabajo irregular y que no se puede interrumpir,
    * No te cobran por adelantado ni te piden un contrato mínimo.
    * Estas instancias corren continuamente hasta que las detengas y solo pagas por el tiempo que la utilizaste.
    * ==ES COMO IR AL CIBER==
2. Savings plan: ofrece un precio todavía más bajo que el On-Demand pero limitado a solo un determinado uso, se mide en dólares/hora. Este tipo de presupuesto te puede ahorrar más del 70% del dinero estimado a gastar en AWS. Se paga en contratos de 1 a 3 años.
3. Reserved instances: específica para cargas de trabajo estables (steady-state workloads) o para aquellas con un uso predecible. Te puede ofrecer un descuento de hasta 75% comparado al on-demand. Se paga en contratos de 1 a 3 años con 3 opciones de pago:
    - All upfront: pagas todo de una en cuanto contratas.
    - Partial upfront: pagas una fracción al contratar.
    - No upfront: no pagas nada al contratar.
4. Spot instances: te permite solicitar poder de cómputo adicional de tu instancia de EC2, por hasta un 90% menos de precio que el On-Demand. El problema es que Amazon te puede decir "ya vete del ciber" cuando se le dé la gana y te va a avisar 2 minutos antes que dejes la compu y guardes lo que estás haciendo para continuar después. Esta es buena opción para cargas de trabajo que puedan ser interrumpidas.
5. Dedicated host: un server físico dedicado solo para tu uso de EC2. Son para usos muy muy específicos y nadie más que tú va a utilizar los recursos de ese server/host.


—

### Scaling Amazon EC2

Escalabilidad y Flexibilidad, cómo puedes hacer que la capacidad de tus centros de datos se adapten a tus necesidades basado en tus horas o periodos de tiempo de uso.
Las empresas que contratan o usan On-Demand no tienen forma de adaptar su capacidad al uso, debido a que siempre están págando por el 100% del hardware, aún cuando muchas veces no usen ni el 10% de todo su poder.
AWS permite utilizar los recursos para mantener el servicio activo, corriendo y adaptable sin puntos de falla.
Amazon EC2 tiene una función llamada **EC2 Auto Scaling** para satisfacer esa necesidad.

Within Amazon EC2 Auto Scaling, you can use two approaches: dynamic scaling and predictive scaling.

* _Dynamic scaling_ responds to changing demand. 
* _Predictive scaling _automatically schedules the right number of Amazon EC2 instances based on predicted demand.

**Tipos de escalabilidad**

- Vertical or scale up: meterle más recursos a la máquina que está corriendo el servicio. (Por sentido común sería lo óptimo, pero la mejor forma de verlo es imaginar una cafetería, con un cajero muy chingón pero que tiene que atender a un cliente bien wey teniendo una fila enorme de clientes esperando).
- Horizontal: añadir más computadoras para atender la carga de trabajo. Deja de ser óptimo cuando hay pocos clientes.

La ventaja que ofrece AWS es que permite tener el número correcto de instancias en el momento que los necesitas, de modo que las utilices del modo más eficiente.

**Concepto del Auto Scaling Group de EC2**

Puedes crear tu Auto Scaling Group, en el que estableces un mínimo, un deseado, y una capacidad máxima de instancias de EC2 que van a correr de acuerdo a la demanda de usuarios.
El mínimo son las instancias que van a iniciar nadamás encender el auto scaling group.
El desired van a correr en cuanto se superen las capacidades del minimo.
Y maximo solo durante picos de demanda.


### Directing Traffic with Elastic Load Balancing

Volvemos al ejemplo de la cafetería, supongamos que la gente está pendeja y todos se van a ser atendidos con el mismo cajero, dejando a los demás sin hacer nada. El problema es resuelto poniendo a alguien en la entrada a que cuente cuántas personas está atendiendo cada cajero para que los reparta de modo que sea eficiente.

A esto se le conoce en computación como un Load Balancer, debido a que todas las instancias deberían de ser capaces de correr lo mismo con la misma eficiencia. AWS ofrece varias soluciones para ello.

Tener un tráfico adecuado permite tener alto rendimiento, mayor eficiencia de costos, alta disponibilidad y escalamiento auitomático.

**Elastic Load Blancing** ELB, es uno de los que vamos a aprender. 
Regional construct, corre a nivel región, de modo que siempre está disponible. 
Es escalable, aumenta su capacidad conforme al número de demanda de usuarios.
ELB permite solicitar más y menos instancias de acuerdo a la demanda.
Funciona como un "puente" entre el frontend y el backend, en el que manda de forma ordenada las solicitudes al backend, y se entera de las capacidades del backend para distribuir mejor el tráfico de red. ESTO EVITA QUE CUANDO UNA INSTANCIA NUEVA SE ENCIENDA, NO SE TENGA QUE MANDAR ESA INFORMACIÓN AL FRONTEND, SOLAMENTE EL LOAD BALANCER SE ENTERA. El front end solamente se encarga de mandar solicitudes, no le importa quién las procese,



