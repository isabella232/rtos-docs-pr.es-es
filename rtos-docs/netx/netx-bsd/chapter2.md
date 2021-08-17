---
title: 'Capítulo 2: Instalación y uso de BSD de Azure RTOS NetX'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente BSD de Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c04175ec18dff160faf853d675c9c85c9a0c6fbc5e834c410a7cb97a739c69f8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796708"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-bsd"></a>Capítulo 2: Instalación y uso de BSD de Azure RTOS NetX

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente BSD de Azure RTOS NetX.

## <a name="product-distribution"></a>Distribución del producto

El componente BSD de Azure RTOS NetX se puede obtener desde nuestro repositorio de código fuente público en [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/). El paquete incluye dos archivos de código fuente y un archivo PDF que contiene este documento, como se indica a continuación:

- **nx_bsd.h**: archivo de encabezado para BSD de NetX
- **nx_bsd.c**: archivo de código fuente C para BSD de NetX
- **nx_bsd.pdf**: guía de usuario para BSD de NetX

Archivos de demostración:
- **bsd_demo_tcp.c**
- **bsd_demo_udp.c**

## <a name="netx-bsd-installation"></a>Instalación de BSD de NetX

Para usar BSD de NetX, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX. Por ejemplo, si NetX se ha instalado en el directorio " *\threadx\arm7\green*", los archivos *nx_bsd.h* y *nx_bsd.c* deben copiarse en ese mismo directorio.

## <a name="building-the-threadx-and-netx-components-of-a-bsd-application"></a>Compilación de los componentes ThreadX y NetX de una aplicación BSD

### <a name="threadx"></a>ThreadX

La biblioteca de ThreadX debe definir *bsd_errno* en el almacenamiento local para el subproceso. Se recomienda el siguiente procedimiento:

1. En *tx_port.h*, establezca una de las macros TX_THREAD_EXTENSION como se indica a continuación:

  ```c
  #define TX_THREAD_EXTENSION_3     int bsd_errno
  ```

2. Recompile la biblioteca de ThreadX.

> [!NOTE]
> Si TX_THREAD_EXTENSION_3 ya está en uso, el usuario puede utilizar una de las otras macros TX_THREAD_EXTENSION.

### <a name="netx"></a>NetX

Antes de usar los servicios de BSD de NetX, la biblioteca de NetX debe compilarse con NX_ENABLE_EXTENDED_NOTIFY_SUPPORT definido (por ejemplo, en *nx_user.h*). De forma predeterminada, no está definido.

## <a name="using-netx-bsd"></a>Uso de BSD de NetX

El uso de BSD para NetX es sencillo. Básicamente, el código de la aplicación debe incluir *nx_bsd.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX, respectivamente. Una vez que se incluye *nx_bsd.h*, el código de aplicación puede usar los servicios BSD especificados más adelante en este manual. La aplicación también debe incluir *nx_bsd.c* en el proceso de compilación. Este archivo se debe compilar de la misma manera que otros archivos de aplicación y su forma de objeto debe vincularse junto con los archivos de la aplicación. Esto es todo lo que se necesita para usar BSD de NetX.

Para utilizar los servicios BSD de NetX, la aplicación debe crear una instancia de IP, un grupo de paquetes e inicializar los servicios BSD mediante llamadas a *bsd_initialize.* Esto se muestra en la sección "Ejemplo pequeño" más adelante en este manual. El prototipo se muestra a continuación:

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                  CHAR *free_memory_ptr, ULONG bsd_thread_stack_size,
                  UINT bsd_thread_priority);
```

Los tres últimos parámetros se usan para crear un subproceso para realizar tareas periódicas, como comprobar los eventos TCP y definir el espacio de pila del subproceso.

> [!NOTE]
> A diferencia de los sockets BSD, que funcionan en la red por orden, NetX funciona por orden de bytes del host del procesador del host. Por motivos de compatibilidad de código fuente, se han definido las macros htons(), ntohs(), htonl() y ntohl(), pero no se modifica el argumento pasado.

## <a name="netx-bsd-limitations"></a>Limitaciones de BSD de NetX

Debido a problemas de rendimiento y arquitectura, BSD de NetX no admite todas las características de sockets de BSD 4.3:

Las marcas INT no se admiten para las llamadas a *send, recv, sendto* y *recvfrom*.

## <a name="netx-bsd-with-dns-support"></a>Compatibilidad de BSD de NetX con DNS

Si se define NX_BSD_ENABLE_DNS, NetX BDS puede enviar consultas de DNS para obtener la información de la IP del host o el nombre del host. Esta característica requiere que se cree previamente un cliente NetX DNS con el servicio *nx_dns_create*. Una o varias direcciones IP de servidor DNS conocidas deben registrarse con la instancia de DNS mediante *nx_dns_server_add* para agregar direcciones de servidor.

Los servicios DNS y la asignación de memoria se usan en los servicios *getaddrinfo* y *getnameinfo*:

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
              const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
              char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

Cuando la aplicación BSD llama a *getaddrinfo* con un nombre de host, BSD de NetX llamará a cualquiera de los servicios siguientes para obtener la dirección IP:

- nx_dns_ipv4_address_by_name_get
- nx_dns_cname_get

Para *nx_dns_ipv4_address_by_name_get*, BSD de NetX usa las áreas de memoria ipv4_addr_buffer. El tamaño de estos búferes se define mediante (`NX_BSD_IPV4_ADDR_PER_HOST * 4`).

Para devolver información de dirección de *getaddrinfo*, BSD de NetX usa la tabla de memoria de bloques de ThreadX *nx_bsd_addrinfo_pool_memory*, cuya área de memoria está definida por otro conjunto de opciones configurables, *NX_BSD_IPV4_ADDR_MAX_NUM*.

Consulte las **Opciones de configuración** para obtener más detalles sobre las opciones de configuración anteriores.

Además, si se define NX_DNS_ENABLE_EXTENDED_RR_TYPES y la entrada del host es un nombre canónico, BSD de NetX asignará dinámicamente la memoria de un grupo de bloques *_nx_bsd_cname_block_pool* creado previamente.

> [!NOTE]
> Después de llamar a *getaddrinfo*, la aplicación BSD es responsable de volver a liberar la memoria a la que apunta el argumento res de vuelta a la tabla de bloque mediante el servicio *freeaddrinfo*.

## <a name="configuration-options"></a>Opciones de configuración

Las opciones configurables por el usuario en *nx_bsd.h* permiten a la aplicación ajustar los sockets de BSD de NetX para sus requisitos de la aplicación concretos. A continuación, se muestra una lista de estos parámetros:

- **NX_BSD_TCP_WINDOW**: se usa en llamadas de creación de sockets TCP. 65535 es un tamaño de ventana típico de Ethernet de 100 Mb. El valor predeterminado es 65535.
- **NX_BSD_SOCKFD_START**: este es el índice lógico del valor de inicio del descriptor de archivo de socket BSD. De forma predeterminada, esta opción es 32.
- **NX_BSD_MAX_SOCKETS**: especifica el número máximo de sockets totales disponibles en la capa BSD y debe ser un múltiplo de 32. El valor predeterminado es 32.
- **NX_BSD_SOCKET_QUEUE_MAX**: especifica el número máximo de paquetes UDP almacenados en la cola de sockets de recepción. El valor predeterminado es 5.
- **NX_BSD_MAX_LISTEN_BACKLOG**: especifica el tamaño de la cola de escucha ("trabajo pendiente") para los sockets TCP de BSD. El valor predeterminado es 5.
- **NX_MICROSECOND_PER_CPU_TICK**: especifica el número de microsegundos por cada interrupción del temporizador.
- **NX_BSD_TIMEOUT**: especifica el tiempo de espera en tics de temporizador requerido por BSD en las llamadas internas de NetX. El valor predeterminado es 20*NX_IP_PERIODIC_RATE.
- **NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: especifica el tiempo de espera en tics de temporizador en la llamada de desconexión de NetX. El valor predeterminado es 1.
- **NX_BSD_PRINT_ERRORS**: si se establece, el estado de error devuelto de una función BSD devuelve un número de línea y un tipo de error, por ejemplo NX_SOC_ERROR, donde se produce el error. Esto requiere que el desarrollador de la aplicación defina la salida de la depuración. La configuración predeterminada está deshabilitada y no se especifica ninguna salida en *nx_bsd.h*.
- **NX_BSD_TIMER_RATE**: intervalo después del cual se ejecuta la tarea de temporizador periódica de BSD. El valor predeterminado es 1 segundo (1 * NX_IP_PERIODIC_RATE).
- **NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: si se establece, esta opción permite que el proceso de tiempo de espera de BSD se ejecute en el contexto del temporizador del sistema. De forma predeterminada está deshabilitado. Esta característica se describe con más detalle en el capítulo 2 "Instalación y uso de BSD de NetX".
- **NX_BSD_ENABLE_DNS**: si esta opción está habilitada, BSD de NetX enviará una consulta de DNS para un nombre de host o una dirección IP de host. Requiere que se cree e inicie previamente una instancia de cliente DNS. De forma predeterminada, no está habilitada.
- **NX_BSD_IPV4_ADDR_MAX_NUM**: número máximo de direcciones IPv4 devueltas por *getaddrinfo*. Esto, junto con NX_BSD_IPV4_ADDR_MAX_NUM, define el tamaño del grupo de bloques BSD de NetX nx_bsd_addrinfo_block_pool para asignar memoria de forma dinámica para el almacenamiento de información de direcciones en *getaddrinfo*. El valor predeterminado es 5.
- **NX_BSD_IPV4_ADDR_PER_HOST**: define el número máximo de direcciones IPv4 almacenadas por consulta de DNS. El valor predeterminado es 5.

## <a name="bsd-socket-options"></a>Opciones de socket BSD

La siguiente lista de opciones de socket BSD de NetX se puede habilitar (o deshabilitar) en tiempo de ejecución por socket mediante el servicio *setsockopt*:

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, const
                void *option_value, INT option_length);
```

Hay dos configuraciones diferentes para *option_level*.

El primer tipo de opciones de socket en tiempo de ejecución es SOL_SOCKET para las opciones de nivel de socket. Para habilitar una opción de nivel de socket es necesario llamar a *setsockopt* con option_level establecido en SOL_SOCKET y option_name establecido en la opción específica, por ejemplo, SO_BROADCAST. Para recuperar una configuración de opción, es necesario llamar a *getsockopt* para option_name con option_level de nuevo establecido en SOL_SOCKET.

A continuación se muestra la lista de opciones de nivel de socket en tiempo de ejecución.

- **SO_BROADCAST**: si se establece, habilita el envío y la recepción de paquetes de difusión de sockets NetX. Este es el comportamiento predeterminado para NetX. Todos los sockets tienen esta capacidad.
- **SO_ERROR**: se usa para obtener el estado del socket en la operación de socket anterior del socket especificado, mediante el servicio *getsockopt*. Todos los sockets tienen esta capacidad.
- **SO_KEEPALIVE**: si se establece, habilita la característica de mantenimiento de conexión TCP. Esto requiere que la biblioteca de NetX se compile con NX_TCP_ENABLE_KEEPALIVE definido en *nx_user.h*. Esta característica está deshabilitada de forma predeterminada.
- **SO_RCVTIMEO**: establece la opción de espera en segundos para recibir paquetes en sockets de BSD de NetX. El valor predeterminado es NX_WAIT_FOREVER (0xFFFFFFFF) o, si está habilitada la opción sin bloqueo, NX_NO_WAIT (0X0).
- **SO_RCVBUF**: establece el tamaño de la ventana del socket TCP. El valor predeterminado, NX_BSD_TCP_WINDOW, se establece en 64 k para sockets TCP de BSD. Para establecer un tamaño superior a 65535, es necesario que la biblioteca de NetX se compile con NX_TCP_ENABLE_WINDOW_SCALING definido.
- **SO_REUSEADDR**: si se establece, permite asignar varios sockets a un puerto. Por lo general se usa en el socket de servidor TCP. Este es el comportamiento predeterminado de los sockets de NetX.

El segundo tipo de opciones de socket en tiempo de ejecución es el nivel de opción de IP. Para habilitar una opción de nivel de IP, es necesario llamar a *setsockopt* con option_level establecido en IP_PROTO y option_name establecido en la opción, por ejemplo, IP_MULTICAST_TTL. Para recuperar un valor de opción, es necesario llamar a *getsockopt* para option_name con option_level de nuevo establecido en IP_PROTO.

A continuación se muestra la lista de opciones de nivel de IP en tiempo de ejecución.

- **IP_MULTICAST_TTL**: establece el período de vida de los sockets UDP. El valor predeterminado es NX_IP_TIME_TO_LIVE (0x80) cuando se crea el socket. Este valor se puede reemplazar mediante una llamada a *setsockopt* con esta opción de socket.
- **IP_ADD_MEMBERSHIP**: si se establece, esta opción permite que el socket BSD (se aplica solo a los sockets UDP) se una al grupo IGMP especificado.
- **IP_ADD_MEMBERSHIP**: si se establece, esta opción permite que el socket BSD (se aplica solo a los sockets UDP) se una al grupo IGMP especificado.

## <a name="small-example-system"></a>Sistema de ejemplo pequeño

A continuación se muestra un ejemplo de cómo usar NetX en la figura 1.0. En este ejemplo, el archivo de inclusión *nx_bsd.h* se agrega en la línea 7. A continuación, la instancia de IP *bsd_ip* y el grupo de paquetes *bsd_pool* se crean como variables globales en las líneas 20 y 21. Observe que en esta demostración se usa un controlador de red (virtual) de RAM (línea 41). En este ejemplo, el cliente y el servidor compartirán la misma dirección IP en la instancia de IP única.

Los subprocesos del cliente y servidor se crean en la línea 303 y 309 en *tx_application_define* que configura la aplicación y se define en las líneas 293-361. Después de la creación correcta de la instancia de IP en la línea 327, la instancia de IP está habilitada para los servicios TCP en la línea 350. El último requisito antes de poder usar los servicios de BSD es llamar a *bsd_initialize* en la línea 360 para configurar todas las estructuras de datos y los recursos de NetX y ThreadX necesarios para BSD.

En la función de entrada de subproceso de servidor, *thread_1_entry,* que se define en las líneas 381-397, la aplicación espera a que el controlador inicialice NetX con parámetros de red. Una vez hecho esto, llama a *tcpServer,* que se define en las líneas 146-253, para controlar los detalles de la configuración del socket de servidor TCP.

*tcpServer* crea el socket maestro llamando al servicio de *socket* en la línea 159 y lo enlaza al socket de escucha mediante la llamada a *bind* en la línea 176. Después se configura para escuchar las solicitudes de conexión en la línea 191. Observe que el socket maestro no acepta una solicitud de conexión. Se ejecuta en un bucle continuo que llama a *select* cada vez para detectar solicitudes de conexión. A un socket BSD secundario elegido de una matriz de sockets BSD se le asigna la solicitud de conexión después de llamar al servicio *accept* en la línea 218.

En el lado del cliente, la función de entrada del subproceso del cliente, *thread_0_entry*, definida en las líneas 366-377, también debe esperar a que el controlador inicialice NetX. Aquí solo se espera a que el lado del servidor lo haga. A continuación, llama a *tcpClient* definido en la línea 54-142 para controlar los detalles de la configuración del socket de cliente TCP y la solicitud de una conexión TCP.

El socket de cliente TCP se crea en la línea 68. El socket se enlaza a la dirección IP especificada e intenta conectarse al servidor TCP que usa una llamada a *connect* en la línea 84. Ahora está listo para empezar a enviar y recibir paquetes.

```c
1 /*  This is a small demo of BSD Wrapper for the high-performance NetX TCP/IP stack.
2     This demo demonstrate TCP connection, disconnection, sending, and receiving using
3     ARP and a simulated Ethernet driver. */
4
5 #include     "tx_api.h"
6 #include     "nx_api.h"
7 #include     "nx_bsd.h"
8 #include     <string.h>
9 #include     <stdlib.h>
10
11 #define         DEMO_STACK_SIZE         (16*1024)
12
13
14 /* Define the ThreadX and NetX object control blocks... */
15
16 TX_THREAD       thread_0;
17 TX_THREAD       thread_1;
18
19
20 NX_PACKET_POOL  bsd_pool;
21 NX_IP           bsd_ip;
22
23
24 /* Define the counters used in the demo application... */
25
26 ULONG           error_counter;
27
28 /* Define fd_set for select call */
29 fd_set          master_list,read_ready,read_ready1;
30
31
32 /* Define thread prototypes. */
33
34 VOID            thread_0_entry(ULONG thread_input);
35 VOID            thread_1_entry(ULONG thread_input);
36
37 VOID            tcpClient(CHAR *msg0);
38 VOID            tcpServer(VOID);
39 INT             HandleClient(INT sock);
40
41 VOID            _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
42
43
44 /* Define main entry point. */
45
46 int main()
47 {
48
49     /* Enter the ThreadX kernel. */
50     tx_kernel_enter();
51 }
52
53
54 VOID tcpClient(CHAR *msg0)
55 {
56
57 INT     status,status1,send_counter;
58 INT     sock_tcp_1,length,length1;
59 struct  sockaddr_in echoServAddr;       /* Echo server address */
60 struct  sockaddr_in localAddr;          /* Local address */
61 struct  sockaddr_in remoteAddr;         /* Remote address */
62
63 UINT    echoServPort; /* Echo Server Port */
64 CHAR    rcvBuffer1[32]
65
66
67     /* Create BSD TCP Socket */
68     sock_tcp_1 = **socket**( PF_INET, SOCK_STREAM, IPPROTO_TCP);
69     if (sock_tcp_1 == -1)
70     {
71         printf("\nError: BSD TCP Client socket create \n");
72         return;
73     }
74
75     printf("\nBSD TCP Client socket created %lu \n", sock_tcp_1);
76     /* Fill destination port and IP address */
77     echoServPort = 12;
78     memset(&echoServAddr, 0, sizeof(echoServAddr));
79     echoServAddr.sin_family = PF_INET;
80     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
81     echoServAddr.sin_port = echoServPort;
82
83     /* Now connect this client the server */
84     status1 = connect(sock_tcp_1, (struct sockaddr *)&echoServAddr, sizeof(echoServAddr));
85     /* Check for error. */
86     if (status1 != OK)
87     {
88         printf("\nError: BSD TCP Client socket Connect, %d \n",sock_tcp_1);
89         status = soc_close(sock_tcp_1);
90         if (status != ERROR)
91             printf("\nConnect ERROR so BSD Client Socket Closed: %d\n",sock_tcp_1);
92         else
93             printf("\nError: BSD Client Socket close %d\n",sock_tcp_1);
94         return;
95     }
96     /* Get and print source and destination information */
97     printf("\nBSD TCP Client socket: %d connected \n", sock_tcp_1);
98
99     status = getsockname(sock_tcp_1, (struct sockaddr *)&localAddr, &length);
100    printf("Client port = %lu , Client = %lu,", 
            localAddr.sin_port, localAddr.sin_addr.s_addr);
101    status = getpeername( sock_tcp_1, (struct sockaddr *) &remoteAddr, &length1);
102    printf("Remote port = %lu, Remote IP = %lu \n", 
            remoteAddr.sin_port remoteAddr.sin_addr.s_addr);
103
104    send_counter = 1;
105
106    /* Now receive the echoed packet from the server */
107    while(1)
108    {
109        tx_thread_sleep(2);
110
111        printf("\nClient sock: %d Sending packet No: %d to
                server\n",sock_tcp_1,send_counter);
112        status = send(sock_tcp_1,msg0, sizeof(msg0), 0);
113        if (status == ERROR)
114            printf("Error: BSD Client Socket send %d\n",sock_tcp_1);
115        else
116        {
117            printf("\nMessage sent: %s\n",msg0);
118            send_counter++;
119        }
120
121        status = recv(sock_tcp_1, (VOID *)rcvBuffer1, 31,0);
122        if (status == 0)
123            break;
124
125        rcvBuffer1[status] = 0;
126
127        if (status != ERROR)
128            printf("\nBSD Client Socket: %d received %lu bytes: %s ", 
                        sock_tcp_1,(ULONG)status,rcvBuffer1);
129        else
130            printf("\nError: BSD Client Socket receive %d \n",sock_tcp_1);
131
132    }
133
134    /* close this client socket */
135    status = soc_close(sock_tcp_1);
136    if (status != ERROR)
137        printf("\nBSD Client Socket Closed %d\n",sock_tcp_1);
138    else
139        printf("\nError: BSD Client Socket close %d \n",sock_tcp_1);
140
141    /* End */
142 }
143
144
145
146 void tcpServer(void)
147 {
148
149 INT         status,status1,sock,sock_tcp_2,i;
150 struct      sockaddr_in echoServAddr; /* Echo server address */
151 struct      sockaddr_in ClientAddr;
152
153 INT         Clientlen;
154 UINT        echoServPort; /* Echo Server Port */
155
156 INT         maxfd;
157
158 /* Create BSD TCP Server Socket */
159     sock_tcp_2 = socket( PF_INET, SOCK_STREAM, IPPROTO_TCP);
160     if (sock_tcp_2 == -1)
161     {
162         printf("Error: BSD TCP Server socket create\n");
163         return;
164     }
165     else
166         printf("BSD TCP Server socket created \n");
167
168     /* Now fill server side information */
169     echoServPort = 12;
170     memset(&echoServAddr, 0, sizeof(echoServAddr));
171     echoServAddr.sin_family = PF_INET;
172     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
173     echoServAddr.sin_port = echoServPort;
174
175     /* Bind this server socket */
176         status = bind(sock_tcp_2, (struct sockaddr *) &echoServAddr, sizeof(echoServAddr));
177     if (status < 0)
178     {
179         printf("Error: BSD TCP Server Socket Bind \n");
180         return;
181     }
182     else
183         printf("BSD TCP Server Socket bound \n");
184
185     FD_ZERO(&master_list);
186     FD_ZERO(&read_ready);
187     FD_SET(sock_tcp_2,&master_list);
188     maxfd = sock_tcp_2;
189
190     /* Now listen for any client connections for this server socket */
191     status = listen(sock_tcp_2,5);
192     if (status < 0)
193     {
194         printf("Error: BSD TCP Server Socket Listen\n");
195         return;
196     }
197     else
198         printf("BSD TCP Server Socket Listen complete, ");
199
200     /* All set to accept client connections */
201     printf("Now accepting client connections\n");
202
203     /* Loop to create and establish server connections. */
204     while(1)
205     {
206
207         read_ready = master_list;
208         tx_thread_sleep(2); /* Allow some time to other threads too */
209         status = select(maxfd+1,&read_ready,0,0,0);
210         if (status == ERROR)
211         {
212             continue;
213         }
214
215         status = FD_ISSET(sock_tcp_2,&read_ready);
216         if(status)
217         {
218             sock = accept(sock_tcp_2,(struct sockaddr*)&ClientAddr, &Clientlen);
219
220             /* Add this new connection to our master list */
221             FD_SET(sock,&master_list);
222             if ( sock \maxfd)
223             {
224                 maxfd = sock;
225             }
226
227             continue;
228         }
229         for (i = 0; i < (maxfd+1); i++)
230         {
231             if (( i != sock_tcp_2) && (FD_ISSET(i,&master_list)) && 
                    (FD_ISSET(i,&read_ready)))
232             {
233                 status1 = HandleClient(i);
234                 if (status1 == 0)
235                 {
236                     status1 = soc_close(i);
237                     if (status1 == OK)
238                     {
239                         FD_CLR(i,&master_list);
240                         printf("\nBSD Server Socket:%d closed\n",i);
241                     }
242                     else
243                         printf("\nError:BSD Server Socket:%d close\n",i);
244                 }
245
246             }
247         }
248
249         /* Loop back to check any next client connection */
250
251     } /* While(1) ends */
252
253 }
254
255 CHAR     rcvBuffer[128];
256
257 INT     HandleClient(INT sock)
258 {
259
260 INT     status;
261
262
263     status = recv(sock, (VOID *)rcvBuffer, 128,0);
264     if (status == ERROR )
265     {
266         printf("\n BSD Server Socket:%d receive \n",sock);
267         return(ERROR);
268     }
269
270     /* a zero return from a recv() call indicates client is terminated! */
271     if (status == 0)
272     {
273         /* Done with this client , close this secondary server socket */
274         return(status);
275     }
276
277     /* print data received from the client */
278     printf("\nBSD Server Socket:%d received %lu bytes: %s \n", sock, (ULONG)status,rcvBuffer);
279
280     /* And echo the same data to the client */
281     status = send(sock,rcvBuffer, status + 1, 0);
282     if (status == ERROR )
283     {
284         printf("\nError: BSD Server Socket:%d send \n",sock);
285         return(ERROR);
286     }
287     return(status);
288 }
289
290
291 /* Define what the initial system looks like. */
292
293 void     tx_application_define(void *first_unused_memory)
294 {
295
296 CHAR     *pointer;
297 UINT     status;
298
299     /* Setup the working pointer. */
300     pointer = (CHAR *) first_unused_memory;
301
302     /* Create a client thread. */
303     tx_thread_create(&thread_0, "Client1", thread_0_entry, 0,
304         pointer, DEMO_STACK_SIZE, 2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
305
306     pointer = pointer + DEMO_STACK_SIZE;
307
308     /* Create a server thread. */
309     tx_thread_create(&thread_1, "Server", thread_1_entry, 0,
310         pointer, DEMO_STACK_SIZE,1,1, TX_NO_TIME_SLICE, TX_AUTO_START);
311
312     pointer = pointer + DEMO_STACK_SIZE;
313
314     /* Initialize the NetX system. */
315     nx_system_initialize();
316
317     /* Create a BSD packet pool. */
318     status = nx_packet_pool_create(&bsd_pool,"NetX BSD Packet Pool", 128
                                        pointer, 16384);
319     pointer = pointer + 16384;
320     if (status)
321     {
322         error_counter++;
323         printf("Error in creating BSD packet pool\n!");
324     }
325
326     /* Create an IP instance for BSD. */
327     status = nx_ip_create(&bsd_ip, "NetX IP Instance 2", IP_ADDRESS(1, 2, 3, 4),
                              0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                              pointer, 2048, 1);
328
329     pointer = pointer + 2048;
330
331     if (status)
332     {
333         error_counter++;
334         printf("Error creating BSD IP instance\n!");
335     }
336
337     /* Enable ARP and supply ARP cache memory for BSD IP Instance */
338     status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
339     pointer = pointer + 1024;
340
341     /* Check ARP enable status. */
342     if (status)
343     {
344         error_counter++;
345         printf("Error in Enable ARP and supply ARP cache memory to BSD IP instance\n");
346     }
347
348     /* Enable TCP processing for BSD IP instances. */
349
350     status = nx_tcp_enable(&bsd_ip);
351
352     /* Check TCP enable status. */
353     if (status)
354     {
355         error_counter++;
356         printf("Error in Enable TCP \n");
357     }
358
359     /* Now initialize BSD Scoket Wrapper */
360     status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 1);
361 }
362
363
364 /* Define the test threads. */
365
366 void     thread_0_entry)ULONG thread_input)
367 {
368
369 CHAR     *msg0 = "Client 1:
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<> \
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";
370
371     /* Wait till Server side is all set */
372     tx_thread_sleep(2);
373     while (1)
374     {
375         tcpClient(msg0);
376         tx_thread_sleep(1);
377     }
378 }
379
380 /* Define the server thread entry function. */
381 void     thread_1_entry(ULONG thread_input)
382 {
383
384 UINT     status;
385 ULONG    actual_status;
386
387 /* Ensure the IP instance has been initialized. */
388 status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE, &actual_status, 100);
389
390 /* Check status... */
391 if (status != NX_SUCCESS)
392 {
393     error_counter++;
394     return;
395 }
396 /* Start a TCP Server */
397 tcpServer();
398 }
399
```
