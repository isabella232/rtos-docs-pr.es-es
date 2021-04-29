---
title: 'Apéndice A: códigos de error irrecuperables de SNTP de Azure RTOS NetX Duo'
description: Los siguientes códigos de error provocarán que el cliente SNTP de Azure RTOS NetX Duo anule las actualizaciones de tiempo con el servidor actual.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 065e7a3e65b3cf8d7fcfb34bb9568a673791609a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814561"
---
# <a name="appendix-a---azure-rtos-netx-duo-sntp-fatal-error-codes"></a><span data-ttu-id="43868-103">Apéndice A: Códigos de error irrecuperables de SNTP de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="43868-103">Appendix A - Azure RTOS NetX Duo SNTP Fatal Error Codes</span></span>

<span data-ttu-id="43868-104">Los siguientes códigos de error provocarán que el cliente SNTP de Azure RTOS NetX Duo anule las actualizaciones de tiempo con el servidor actual.</span><span class="sxs-lookup"><span data-stu-id="43868-104">The following error codes will result in the Azure RTOS NetX Duo SNTP Client aborting time updates with the current server.</span></span> <span data-ttu-id="43868-105">La aplicación será la que decidirá si el servidor debe quitarse de la lista que tiene disponibles el cliente SNTP o simplemente se debe cambiar al siguiente servidor disponible en la lista.</span><span class="sxs-lookup"><span data-stu-id="43868-105">It is up to the application to decide if the server should be removed from the SNTP Client list of available servers, or simply switch to the next available server on the list.</span></span> <span data-ttu-id="43868-106">La definición de cada estado de error se establece en \*nxd_sntp_client.h.</span><span class="sxs-lookup"><span data-stu-id="43868-106">The definition of each error status is defined in \*nxd_sntp_client.h.</span></span> *

<span data-ttu-id="43868-107">Cuando el cliente SNTP devuelve un error de la lista siguiente a la aplicación, es probable que el servidor deba reemplazarse por otro.</span><span class="sxs-lookup"><span data-stu-id="43868-107">When the SNTP Client returns an error from the list below to the application, the Server should probably be replaced with another Server.</span></span> <span data-ttu-id="43868-108">Tenga en cuenta que el estado de error NX_SNTP_KOD_REMOVE_SERVER se deja para que lo establezca el controlador que desencadena errores de tipo KOD (beso de la muerte) del cliente SNTP (función de devolución de llamada):</span><span class="sxs-lookup"><span data-stu-id="43868-108">Note that the NX_SNTP_KOD_REMOVE_SERVER error status is left to the SNTP Client kiss of death handler (callback function) to set:</span></span>

- <span data-ttu-id="43868-109">NX_SNTP_KOD_REMOVE_SERVER 0xD0C</span><span class="sxs-lookup"><span data-stu-id="43868-109">NX_SNTP_KOD_REMOVE_SERVER 0xD0C</span></span>  
- <span data-ttu-id="43868-110">NX_SNTP_SERVER_AUTH_FAIL 0xD0D</span><span class="sxs-lookup"><span data-stu-id="43868-110">NX_SNTP_SERVER_AUTH_FAIL 0xD0D</span></span>  
- <span data-ttu-id="43868-111">NX_SNTP_INVALID_NTP_VERSION 0xD11</span><span class="sxs-lookup"><span data-stu-id="43868-111">NX_SNTP_INVALID_NTP_VERSION 0xD11</span></span>  
- <span data-ttu-id="43868-112">NX_SNTP_INVALID_SERVER_MODE 0xD12</span><span class="sxs-lookup"><span data-stu-id="43868-112">NX_SNTP_INVALID_SERVER_MODE 0xD12</span></span>  
- <span data-ttu-id="43868-113">NX_SNTP_INVALID_SERVER_STRATUM 0xD15</span><span class="sxs-lookup"><span data-stu-id="43868-113">NX_SNTP_INVALID_SERVER_STRATUM 0xD15</span></span>  

<span data-ttu-id="43868-114">Cuando el cliente SNTP devuelve un error de la lista siguiente a la aplicación, es posible que no pueda proporcionar actualizaciones de hora válidas solo temporalmente y que no sea necesario eliminarlo:</span><span class="sxs-lookup"><span data-stu-id="43868-114">When the SNTP Client returns an error from the list below to the application, the Server may only temporarily be unable to provide valid time updates and need not be removed:</span></span>

- <span data-ttu-id="43868-115">HNX_SNTP_NO_UNICAST_FROM_SERVER 0xD09</span><span class="sxs-lookup"><span data-stu-id="43868-115">HNX_SNTP_NO_UNICAST_FROM_SERVER 0xD09</span></span>  
- <span data-ttu-id="43868-116">NX_SNTP_SERVER_CLOCK_NOT_SYNC 0xD0A</span><span class="sxs-lookup"><span data-stu-id="43868-116">NX_SNTP_SERVER_CLOCK_NOT_SYNC 0xD0A</span></span>  
- <span data-ttu-id="43868-117">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD0B</span><span class="sxs-lookup"><span data-stu-id="43868-117">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD0B</span></span>  
- <span data-ttu-id="43868-118">NX_SNTP_OVER_BAD_UPDATE_LIMIT 0xD17</span><span class="sxs-lookup"><span data-stu-id="43868-118">NX_SNTP_OVER_BAD_UPDATE_LIMIT 0xD17</span></span>  
- <span data-ttu-id="43868-119">NX_SNTP_BAD_SERVER_ROOT_DISPERSION 0xD16</span><span class="sxs-lookup"><span data-stu-id="43868-119">NX_SNTP_BAD_SERVER_ROOT_DISPERSION 0xD16</span></span>  
- <span data-ttu-id="43868-120">NX_SNTP_INVALID_RTT_TIME 0xD21</span><span class="sxs-lookup"><span data-stu-id="43868-120">NX_SNTP_INVALID_RTT_TIME 0xD21</span></span>  
- <span data-ttu-id="43868-121">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD24</span><span class="sxs-lookup"><span data-stu-id="43868-121">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD24</span></span>