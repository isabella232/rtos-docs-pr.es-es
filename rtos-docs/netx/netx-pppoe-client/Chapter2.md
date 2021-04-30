---
title: 'Capítulo 2: Instalación y uso del cliente PPPoE de Azure RTOS NetX'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente de cliente PPPoE para Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 17d910647db7b207280b3fbd9e90c468293a8e67
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815145"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pppoe-client"></a>Capítulo 2: Instalación y uso del cliente PPPoE de Azure RTOS NetX

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente de cliente PPPoE para Azure RTOS NetX.

## <a name="product-distribution"></a>Distribución del producto

El cliente PPPoE para NetX está disponible en [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx). El paquete incluye los siguientes archivos:

 - **nx_pppoe_client.h**: archivo de encabezado del cliente PPPoE para NetX
 - **nx_pppoe_client.c**: archivo de código fuente C del cliente PPPoE para NetX
 - **nx_pppoe_client.pdf** descripción en PDF del cliente PPPoE para NetX
 - **demo_netx_pppoe_client.c**: demostración del cliente PPPoE de NetX

## <a name="pppoe-client-installation"></a>Instalación del cliente PPPoE

Para usar el cliente PPPoE para NetX, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX. Por ejemplo, si NetX está instalado en el directorio *“\threadx\arm7\green”* , los archivos *nx_pppoe_client.h* y *nx_pppoe_client.c* deben copiarse en ese mismo directorio.

## <a name="using-pppoe-client"></a>Uso del cliente PPPoE

Es fácil usar el cliente PPPoE para NetX. Básicamente, el código de la aplicación debe incluir *nx_pppoe_client.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX, respectivamente. Después de incluir *nx_pppoe_client.h*, el código de la aplicación puede realizar las llamadas de función de cliente PPPoE que se especifican más adelante en este manual. La aplicación también debe incluir *nx_pppoe_client.c* en el proceso de compilación. Este archivo se debe compilar de la misma manera que otros archivos de aplicación y su forma de objeto debe vincularse junto con los archivos de la aplicación. Esto es todo lo que se necesita para usar el cliente PPPoE de NetX.

## <a name="small-example-system"></a>Sistema de ejemplo pequeño

El siguiente es un ejemplo que muestra cómo usar el cliente PPPoE de NetX descrito en la figura 1.1. En este ejemplo, el archivo de inclusión del cliente PPPoE *nx_pppoe_client.h* se agrega en la línea 50. A continuación, se crea el cliente de PPPoE en *"thread_0_entry"* en la línea 238. Observe que el cliente de PPPoE debe crearse después de crear la instancia de IP. La instancia de IP y la instancia de PPP se crean e inicializan en las líneas 142-220. El bloque de control de cliente de PPPoE *"pppoe_client"* se definió como una variable global en la línea 75 anteriormente. Las funciones de envío y recepción se establecen en la línea 238.

En general, el módulo PPPoE se debe usar con el módulo PPP. En este ejemplo, el archivo de inclusión del cliente PPP *nx_ppp.h* se agrega en la línea 49. A continuación, se crea el cliente PPP en la línea 164. La línea 172 configura la función para enviar el paquete PPP. La línea 179-190 configura las direcciones IP y define el protocolo PAP. En la línea 104-129 se configura el nombre de usuario y la contraseña para el protocolo PAP.

Una vez establecida la sesión PPPoE. La aplicación puede llamar a *nx_pppoe_client_session_get* para obtener la información de la sesión (dirección MAC del servidor e identificador de sesión) en la línea 264. PPP o la aplicación puede llamar a *nx_pppoe_client_session_packet_send* para enviar el paquete PPPoE en la línea 283.

Cuando la aplicación ya no procesa el tráfico PPP, la aplicación puede llamar a *nx_pppoe_client_session_terminate* para finalizar la sesión de PPPoE.

Observe que, en este ejemplo, el cliente PPPoE funciona con la pila IP normal al mismo tiempo y comparte un controlador Ethernet. Pase el mismo controlador Ethernet para la instancia de IP normal en la línea 155 y la instancia de cliente de PPPoE en la línea 298.

> [!NOTE]
> Vuelva a definir **NX_PHYSICAL_HEADER** en 24 para asegurarse de que hay suficiente espacio para rellenar el encabezado físico. Encabezado físico: 14 (encabezado Ethernet) + 6 (encabezado PPPoE) + 2 (encabezado PPP) + 2 (alineación de cuatro bytes).

```c
  1 /**************************************************************************/
  2 /**************************************************************************/
  3 /**                                                                       */
  4 /** NetX PPPoE Client stack Component                                     */
  5 /**                                                                       */
  6 /**   This is a small demo of the high-performance NetX PPPoE Client      */
  7 /**   stack. This demo includes IP instance, PPPoE Client and PPP Client  */
  8 /**   stack. Create one IP instance includes two interfaces to support    */
  9 /**   for normal IP stack and PPPoE Client, PPPoE Client can use the      */
 10 /**   mutex of IP instance to send PPPoE message when share one Ethernet  */
 11 /**   driver. PPPoE Client work with normal IP instance at the same time. */
 12 /**                                                                       */
 13 /**   Note1: Substitute your Ethernet driver instead of                   */
 14 /**   _nx_ram_network_driver before run this demo                         */
 15 /**                                                                       */
 16 /**   Note2: Prerequisite for using PPPoE.                                */
 17 /**   Redefine NX_PHYSICAL_HEADER to 24 to ensure enough space for filling*/
 18 /**   in physical header. Physical header:14(Ethernet header)             */
 19 /**    + 6(PPPoE header) + 2(PPP header) + 2(four-byte aligment)          */
 20 /**                                                                       */
 21 /**************************************************************************/
 22 /**************************************************************************/
 23
 24
 25       /*****************************************************************/
 26       /*                          NetX Stack                           */
 27       /*****************************************************************/
 28
 29                                             /***************************/
 30                                             /*        PPP Client       */
 31                                             /***************************/
 32
 33                                             /***************************/
 34                                             /*       PPPoE Client      */
 35                                             /***************************/
 36       /***************************/         /***************************/
 37       /*    Normal Ethernet Type */         /*    PPPoE Ethernet Type  */
 38       /***************************/         /***************************/
 39       /***************************/         /***************************/
 40       /*       Interface 0       */         /*       Interface 1       */
 41       /***************************/         /***************************/
 42
 43       /*****************************************************************/
 44       /*                       Ethernet Dirver                         */
 45       /*****************************************************************/
 46
 47 #include   "tx_api.h"
 48 #include   "nx_api.h"
 49 #include   "nx_ppp.h"
 50 #include   "nx_pppoe_client.h"
 51
 52 /* Defined NX_PPP_PPPOE_ENABLE if use Express Logic's PPP, since PPP module has been modified
       to match PPPoE moduler under this definition.  */
 53 #ifdef NX_PPP_PPPOE_ENABLE
 54
 55 /* If the driver is not initialized in other module, define NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE
       to initialize the driver in PPPoE module .
 56    In this demo, the driver has been initialized in IP module.  */
 57 #ifndef NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE
 58
 59 /* Define the block size.  */
 60 #define     NX_PACKET_POOL_SIZE     ((1536 + sizeof(NX_PACKET)) * 30)
 61 #define     DEMO_STACK_SIZE         2048
 62 #define     PPPOE_THREAD_SIZE       2048
 63
 64 /* Define the ThreadX and NetX object control blocks...  */
 65 TX_THREAD               thread_0;
 66
 67 /* Define the packet pool and IP instance for normal IP instnace.  */
 68 NX_PACKET_POOL          pool_0;
 69 NX_IP                   ip_0;
 70
71 /* Define the PPP Client instance.  */
 72 NX_PPP                  ppp_client;
 73
 74 /* Define the PPPoE Client instance.  */
 75 NX_PPPOE_CLIENT         pppoe_client;
 76
 77 /* Define the counters.  */
 78 CHAR                    *pointer;
 79 ULONG                   error_counter;
 80
 81 /* Define thread prototypes.  */
 82 void    thread_0_entry(ULONG thread_input);
 83
 84 /***** Substitute your PPP driver entry function here *********/
 85 extern void    _nx_ppp_driver(NX_IP_DRIVER *driver_req_ptr);
 86
 87 /***** Substitute your Ethernet driver entry function here *********/
 88 extern void    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
 89
 90 /* Define the porting layer function for Express Logic's PPP to simulate TTP's PPP.
 91    Functions to be provided by PPP for calling by the PPPoE Stack.  */
 92 void    ppp_client_packet_send(NX_PACKET *packet_ptr);
 93 void    pppoe_client_packet_receive(NX_PACKET *packet_ptr);
 94
 95 /* Define main entry point.  */
 96
 97 int main()
 98 {
 99
100     /* Enter the ThreadX kernel.  */
101     tx_kernel_enter();
102 }
103
104 UINT generate_login(CHAR *name, CHAR *password)
105 {
106
107     /* Make a name and password, called "myname" and "mypassword".  */
108     name[0] = 'm';
109     name[1] = 'y';
110     name[2] = 'n';
111     name[3] = 'a';
112     name[4] = 'm';
113     name[5] = 'e';
114     name[6] = (CHAR) 0;
115
116     password[0] = 'm';
117     password[1] = 'y';
118     password[2] = 'p';
119     password[3] = 'a';
120     password[4] = 's';
121     password[5] = 's';
122     password[6] = 'w';
123     password[7] = 'o';
124     password[8] = 'r';
125     password[9] = 'd';
126     password[10] = (CHAR) 0;
127
128     return(NX_SUCCESS);
129 }
130
131 /* Define what the initial system looks like.  */
132
133 void    tx_application_define(void *first_unused_memory)
134 {
135
136 UINT    status;
137
138     /* Setup the working pointer.  */
139     pointer =  (CHAR *) first_unused_memory;
140
141     /* Initialize the NetX system.  */
142     nx_system_initialize();
143
144     /* Create a packet pool for normal IP instance.  */
145     status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool",
146                                    (1536 + sizeof(NX_PACKET)),
147                                    pointer, NX_PACKET_POOL_SIZE);
148     pointer = pointer + NX_PACKET_POOL_SIZE;
149
150     /* Check for error.  */
151     if (status)
152         error_counter++;
153
154     /* Create an normal IP instance.  */
155     status = nx_ip_create(&ip_0, "NetX IP Instance", IP_ADDRESS(192, 168, 100, 44), 0xFFFFFF00UL,
156                           &pool_0, _nx_ram_network_driver, pointer, 2048, 1);
157     pointer = pointer + 2048;
158
159     /* Check for error.  */
160     if (status)
161         error_counter++;
162
163     /* Create the PPP instance.  */
164     status = nx_ppp_create(&ppp_client, "PPP Instance", &ip_0, pointer, 2048, 1,
165                            &pool_0, NX_NULL, NX_NULL); pointer = pointer + 2048;
166
167     /* Check for PPP create error.   */
168     if (status)
169         error_counter++;
170
171     /* Set the PPP packet send function.  */
172     status = nx_ppp_packet_send_set(&ppp_client, ppp_client_packet_send);
173
174     /* Check for PPP packet send function set error.   */
175     if (status)
176         error_counter++;
177
178     /* Define IP address. This PPP instance is effectively the client since it doesn't have
           any IP addresses. */
179     status = nx_ppp_ip_address_assign(&ppp_client, IP_ADDRESS(0, 0, 0, 0), IP_ADDRESS(0, 0, 0, 0));
180
181     /* Check for PPP IP address assign error.   */
182     if (status)
183         error_counter++;
184
185     /* Setup PAP, this PPP instance is effectively the since it generates the name and password
           for the peer..  */
186     status = nx_ppp_pap_enable(&ppp_client, generate_login, NX_NULL);
187
188     /* Check for PPP PAP enable error.  */
189     if (status)
190         error_counter++;
191
192     /* Attach an interface for PPP.  */
193     status = nx_ip_interface_attach(&ip_0, "Second Interface For PPP", IP_ADDRESS(0, 0, 0, 0), 0,
                                        nx_ppp_driver);
194
195     /* Check for error.  */
196     if (status)
197         error_counter++;
198
199     /* Enable ARP and supply ARP cache memory for Normal IP Instance.  */
200     status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
201     pointer = pointer + 1024;
202
203     /* Check for ARP enable errors.  */
204     if (status)
205         error_counter++;
206
207     /* Enable ICMP */
208     status = nx_icmp_enable(&ip_0);
209     if(status)
210         error_counter++;
211
212     /* Enable UDP traffic.  */
213     status =  nx_udp_enable(&ip_0);
214     if (status)
215         error_counter++;
216
217     /* Enable TCP traffic.  */
218     status =  nx_tcp_enable(&ip_0);
219     if (status)
220         error_counter++;
221
222     /* Create the main thread.  */
223     tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
224                      pointer, DEMO_STACK_SIZE,
225                      4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
226     pointer =  pointer + DEMO_STACK_SIZE;
227
228 }
229
230 /* Define the test threads.  */
231
232 void    thread_0_entry(ULONG thread_input)
233 {
234 UINT    status;
235 ULONG   ip_status;
236
237     /* Create the PPPoE instance.  */
238     status =  nx_pppoe_client_create(&pppoe_client, (UCHAR *)"PPPoE Client",  &ip_0,  0,
        &pool_0, pointer, PPPOE_THREAD_SIZE, 4, _nx_ram_network_driver, pppoe_client_packet_receive);
239     pointer = pointer + PPPOE_THREAD_SIZE;
240     if (status)
241     {
242         error_counter++;
243         return;
244     }
245
246     /* Establish PPPoE Client sessione.  */
247     status = nx_pppoe_client_session_connect(&pppoe_client, NX_WAIT_FOREVER);
248     if (status)
249     {
250         error_counter++;
251         return;
252     }
253
254     /* Wait for the link to come up.  */
255     status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_ADDRESS_RESOLVED,
                                              &ip_status, NX_WAIT_FOREVER);
256     if (status)
257     {
258         error_counter++;
259         return;
260     }
261
262     /* Get the PPPoE Server physical address and Session ID after establish PPPoE Session.  */
263     /*
264     status = nx_pppoe_client_session_get(&pppoe_client, &server_mac_msw,
                                             &server_mac_lsw, &session_id);
265     if (status)
266         error_counter++;
267     */
268 }
269
270 /* PPPoE Client receive function.  */
271 void    pppoe_client_packet_receive(NX_PACKET *packet_ptr)
272 {
273
274     /* Call PPP Client to receive the PPP data fame.  */
275     nx_ppp_packet_receive(&ppp_client, packet_ptr);
276 }
277
278 /* PPP Client send function.  */
279 void    ppp_client_packet_send(NX_PACKET *packet_ptr)
280 {
281
282     /* Directly Call PPPoE send function to send out the data through PPPoE module.  */
283     nx_pppoe_client_session_packet_send(&pppoe_client, packet_ptr);
284 }
285 #endif /* NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE  */
286
287 #endif /* NX_PPP_PPPOE_ENABLE  */
```

**Figura 1.1 Ejemplo de uso del cliente de PPPoE con NetX**

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración para compilar el cliente PPPoE para NetX. En la lista siguiente se describe cada una de forma detallada:

- **NX_DISABLE_ERROR_CHECKING**: si está definida, esta opción quita la comprobación de errores básica del cliente PPPoE. Normalmente se utiliza después de depurar la aplicación.
- **NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE**: si se define, habilita la característica para inicializar el controlador Ethernet en el módulo PPPoE. Se deshabilita de forma predeterminada.
- **NX_PPPOE_CLIENT_THREAD_TIME_SLICE**: opción de porción de tiempo para el subproceso del cliente PPPoE. Este valor es TX_NO_TIME_SLICE de forma predeterminada.
- **NX_PPPOE_CLIENT_PADI_INIT_TIMEOUT**: define la porción de espera para los paquetes PADI de retransmisión inicial. De manera predeterminada, este valor es 1 segundo.
- **NX_PPPOE_CLIENT_PADI_COUNT**: define el número de retiradas de transmisión de PADI que se permiten antes de que se considere interrumpida la conexión. De manera predeterminada, este valor es 4
- **NX_PPPOE_CLIENT_PADR_INIT_TIMEOUT**: define la porción de espera para los paquetes PADR de retransmisión inicial. De manera predeterminada, este valor es 1 segundo.
- **NX_PPPOE_CLIENT_PADR_COUNT**: define el número de retiradas de transmisión de PADR que se permiten antes de que se considere interrumpida la conexión. De manera predeterminada, este valor es 4
- **NX_PPPOE_CLIENT_MAX_AC_NAME_SIZE**: esto define el tamaño máximo de AC-Name. De manera predeterminada, este valor es 32.
- **NX_PPPOE_CLIENT_MAX_AC_COOKIE_SIZE**: esto define el tamaño máximo de AC-Cookie. De manera predeterminada, este valor es 32.
- **NX_PPPOE_CLIENT_MAX_RELAY_SESSION_ID_SIZE**: define el tamaño máximo del identificador de sesión de retransmisión. De forma predeterminada, este valor es 12.
- **NX_PPPOE_CLIENT_MIN_PACKET_PAYLOAD_SIZE**: especifica el tamaño mínimo de carga de paquetes para el cliente PPPoE. Si el tamaño de la carga del paquete es mayor que este valor, puede evitar un encadenamiento de paquetes. De forma predeterminada, este valor es 1520 (tamaño máximo de carga de Ethernet 1500, encabezado de Ethernet 14, CRC 2 y alineación de cuatro bytes 4).
