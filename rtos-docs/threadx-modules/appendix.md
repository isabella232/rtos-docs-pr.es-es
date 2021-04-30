---
title: 'Apéndice: Ejemplos específicos de la distribución'
description: En este artículo se muestran ejemplos específicos de la distribución de ThreadX Modules.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b54b8b094e608052fdbfc392d93a57ebb34515ed
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815654"
---
# <a name="appendix---port-specific-examples"></a><span data-ttu-id="f9eb4-103">Apéndice: Ejemplos específicos de la distribución</span><span class="sxs-lookup"><span data-stu-id="f9eb4-103">Appendix - Port-specific examples</span></span>

## <a name="arm11-processor"></a><span data-ttu-id="f9eb4-104">Procesador ARM11</span><span class="sxs-lookup"><span data-stu-id="f9eb4-104">ARM11 processor</span></span>

### <a name="arm11-using-gcc"></a><span data-ttu-id="f9eb4-105">ARM11 con GCC</span><span class="sxs-lookup"><span data-stu-id="f9eb4-105">ARM11 using GCC</span></span>

#### <a name="module-preamble-for-arm11-using-gcc"></a><span data-ttu-id="f9eb4-106">Preámbulo de módulo para ARM11 con GCC</span><span class="sxs-lookup"><span data-stu-id="f9eb4-106">Module preamble for ARM11 using GCC</span></span>

```armasm
    .arm
    .section .preamble, "ax"

    /* Define the module preamble.  */

    .global _txm_module_preamble
_txm_module_preamble:
    .word       0x4D4F4455                                      @ Module ID
    .word       0x5                                             @ Module Major Version
    .word       0x6                                             @ Module Minor Version
    .word       32                                              @ Module Preamble Size in 32-bit words
    .word       0x12345678                                      @ Module ID (application defined)
    .word       0x02000000                                      @ Module Properties where:
                                                                @   Bits 31-24: Compiler ID
                                                                @           0 -> IAR
                                                                @           1 -> ARM
                                                                @           2 -> GNU
    .word       _txm_module_thread_shell_entry - . - 0          @ Module Shell Entry Point
    .word       demo_module_start - . - 0                       @ Module Start Thread Entry Point
    .word       0                                               @ Module Stop Thread Entry Point
    .word       1                                               @ Module Start/Stop Thread Priority
    .word       1024                                            @ Module Start/Stop Thread Stack Size
    .word       _txm_module_callback_request_thread_entry - . - 0   @ Module Callback Thread Entry
    .word       1                                               @ Module Callback Thread Priority
    .word       1024                                            @ Module Callback Thread Stack Size
    .word       __code_size__                                   @ Module Code Size
    .word       __data_size__                                   @ Module Data Size
    .word       0                                               @ Reserved 0
    .word       0                                               @ Reserved 1
    .word       0                                               @ Reserved 2
    .word       0                                               @ Reserved 3
    .word       0                                               @ Reserved 4
    .word       0                                               @ Reserved 5
    .word       0                                               @ Reserved 6
    .word       0                                               @ Reserved 7  
    .word       0                                               @ Reserved 8  
    .word       0                                               @ Reserved 9
    .word       0                                               @ Reserved 10
    .word       0                                               @ Reserved 11
    .word       0                                               @ Reserved 12
    .word       0                                               @ Reserved 13
    .word       0                                               @ Reserved 14
    .word       0                                               @ Reserved 15
```

#### <a name="module-properties-for-arm11-using-gcc"></a><span data-ttu-id="f9eb4-107">Propiedades de módulo para ARM11 con GCC</span><span class="sxs-lookup"><span data-stu-id="f9eb4-107">Module properties for ARM11 using GCC</span></span>

| <span data-ttu-id="f9eb4-108">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-108">Bit</span></span> | <span data-ttu-id="f9eb4-109">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-109">Value</span></span> | <span data-ttu-id="f9eb4-110">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-110">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-111">[23-0]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-111">[23-0]</span></span> | <span data-ttu-id="f9eb4-112">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-112">0</span></span> | <span data-ttu-id="f9eb4-113">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-113">Reserved</span></span>
| <span data-ttu-id="f9eb4-114">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-114">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-115">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-115">0x00</span></span><br /><span data-ttu-id="f9eb4-116">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-116">0x01</span></span><br /><span data-ttu-id="f9eb4-117">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-117">0x02</span></span> | <span data-ttu-id="f9eb4-118">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-118">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-119">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-119">IAR</span></span><br /><span data-ttu-id="f9eb4-120">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-120">ARM</span></span><br /><span data-ttu-id="f9eb4-121">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-121">GNU</span></span> |

#### <a name="module-linker-for-arm11-using-gcc"></a><span data-ttu-id="f9eb4-122">Enlazador de módulos para ARM11 con GCC</span><span class="sxs-lookup"><span data-stu-id="f9eb4-122">Module linker for ARM11 using GCC</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x080F0000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0x64001800, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x080F0000;
  __FLASH_segment_end__   = 0x080FFFFF;
  __RAM_segment_start__   = 0x64001800;
  __RAM_segment_end__     = 0x64011800;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  }
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);

  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-arm11-using-gcc"></a><span data-ttu-id="f9eb4-123">Compilación de módulos para ARM11 con GCC</span><span class="sxs-lookup"><span data-stu-id="f9eb4-123">Building Modules for ARM11 using GCC</span></span>

<span data-ttu-id="f9eb4-124">Ejemplo sencillo de línea de comandos para compilar un módulo de ARM11 con GCC:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-124">A simple command-line example for building an ARM11 module using GCC:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 txm_module_preamble.S
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 demo_threadx_module.c
arm-none-eabi-ld -A arm1136j-s -T demo_threadx_module.ld txm_module_preamble.o gcc_setup.o demo_threadx_module.o txm.a txm.a -o demo_threadx_module.out -M > demo_threadx_module.map
```

#### <a name="thread-extension-definition-for-arm11-using-gcc"></a><span data-ttu-id="f9eb4-125">Definición de extensión de subproceso para ARM11 con GCC</span><span class="sxs-lookup"><span data-stu-id="f9eb4-125">Thread extension definition for ARM11 using GCC</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;  \
                                VOID    *tx_thread_module_entry_info_ptr;
```

#### <a name="building-module-manager-for-arm11-using-gcc"></a><span data-ttu-id="f9eb4-126">Compilación de administrador de módulos para ARM11 con GCC</span><span class="sxs-lookup"><span data-stu-id="f9eb4-126">Building Module Manager for ARM11 using GCC</span></span>

<span data-ttu-id="f9eb4-127">No se proporciona ningún ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-127">No example is provided.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-arm11-using-gcc"></a><span data-ttu-id="f9eb4-128">Atributos de API de habilitación de memoria externa para ARM11 con GCC</span><span class="sxs-lookup"><span data-stu-id="f9eb4-128">Attributes for external memory enable API for ARM11 using GCC</span></span>

<span data-ttu-id="f9eb4-129">Esta característica no está habilitada en esta distribución.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-129">This feature not enabled on this port.</span></span>

### <a name="arm11-using-ac5"></a><span data-ttu-id="f9eb4-130">ARM11 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-130">ARM11 using AC5</span></span>

#### <a name="module-preamble-for-arm11-using-ac5"></a><span data-ttu-id="f9eb4-131">Preámbulo de módulo para ARM11 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-131">Module preamble for ARM11 using AC5</span></span>

```armasm
    AREA  Init, CODE, READONLY

;    /* Define public symbols.  */

    EXPORT __txm_module_preamble

;    /* Define application-specific start/stop entry points for the module.  */

    IMPORT demo_module_start

;    /* Define common external references.  */

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|

__txm_module_preamble
        DCD       0x4D4F4455                                        ; Module ID
        DCD       0x5                                               ; Module Major Version
        DCD       0x3                                               ; Module Minor Version
        DCD       32                                                ; Module Preamble Size in 32-bit words
        DCD       0x12345678                                        ; Module ID (application defined)
        DCD       0x01000000                                        ; Module Properties where:
                                                                    ;   Bits 31-24: Compiler ID
                                                                    ;           0 -> IAR
                                                                    ;           1 -> ARM
                                                                    ;           2 -> GNU
                                                                    ;   Bits 23-0:  Reserved
        DCD       _txm_module_thread_shell_entry - . + .            ; Module Shell Entry Point
        DCD       demo_module_start - . + .                         ; Module Start Thread Entry Point
        DCD       0                                                 ; Module Stop Thread Entry Point
        DCD       1                                                 ; Module Start/Stop Thread Priority
        DCD       1024                                              ; Module Start/Stop Thread Stack Size
        DCD       _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
        DCD       1                                                 ; Module Callback Thread Priority
        DCD       1024                                              ; Module Callback Thread Stack Size
        DCD       |Image$$ER_RO$$Length|                            ; Module Code Size
        DCD       0x4000                                            ; Module Data Size - default to 16K (need to make sure this is large enough for module's data needs!)
        DCD       0                                                 ; Reserved 0
        DCD       0                                                 ; Reserved 1
        DCD       0                                                 ; Reserved 2
        DCD       0                                                 ; Reserved 3
        DCD       0                                                 ; Reserved 4
        DCD       0                                                 ; Reserved 5
        DCD       0                                                 ; Reserved 6
        DCD       0                                                 ; Reserved 7
        DCD       0                                                 ; Reserved 8  
        DCD       0                                                 ; Reserved 9
        DCD       0                                                 ; Reserved 10
        DCD       0                                                 ; Reserved 11
        DCD       0                                                 ; Reserved 12
        DCD       0                                                 ; Reserved 13
        DCD       0                                                 ; Reserved 14
        DCD       0                                                 ; Reserved 15

        END
```

#### <a name="module-properties-for-arm11-using-ac5"></a><span data-ttu-id="f9eb4-132">Propiedades de módulo para ARM11 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-132">Module properties for ARM11 using AC5</span></span>

| <span data-ttu-id="f9eb4-133">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-133">Bit</span></span> | <span data-ttu-id="f9eb4-134">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-134">Value</span></span> | <span data-ttu-id="f9eb4-135">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-135">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-136">[23-0]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-136">[23-0]</span></span> | <span data-ttu-id="f9eb4-137">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-137">0</span></span> | <span data-ttu-id="f9eb4-138">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-138">Reserved</span></span>
| <span data-ttu-id="f9eb4-139">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-139">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-140">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-140">0x00</span></span><br /><span data-ttu-id="f9eb4-141">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-141">0x01</span></span><br /><span data-ttu-id="f9eb4-142">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-142">0x02</span></span> | <span data-ttu-id="f9eb4-143">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-143">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-144">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-144">IAR</span></span><br /><span data-ttu-id="f9eb4-145">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-145">ARM</span></span><br /><span data-ttu-id="f9eb4-146">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-146">GNU</span></span> |

#### <a name="module-linker-for-arm11-using-ac5"></a><span data-ttu-id="f9eb4-147">Enlazador de módulos para ARM11 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-147">Module linker for ARM11 using AC5</span></span>

<span data-ttu-id="f9eb4-148">Se compila en la línea de comandos; no hay ningún ejemplo de archivo de enlazador.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-148">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-arm11-using-ac5"></a><span data-ttu-id="f9eb4-149">Compilación de módulos para ARM11 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-149">Building Modules for ARM11 using AC5</span></span>

<span data-ttu-id="f9eb4-150">Ejemplo sencillo de línea de comandos para compilar un módulo de ARM11 con AC5:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-150">A simple command-line example for building an ARM11 module using AC5:</span></span>

```dos
armasm -g --cpu ARM1136J-S --apcs /interwork --apcs /ropi --apcs /rwpi txm_module_preamble.s
armcc -g -c -O0 --cpu ARM1136J-S --apcs /interwork --apcs /ropi --apcs /rwpi demo_threadx_module.c
armlink -d -o demo_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-arm11-using-ac5"></a><span data-ttu-id="f9eb4-151">Definición de extensión de subproceso para ARM11 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-151">Thread extension definition for ARM11 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;  \
                                VOID    *tx_thread_module_entry_info_ptr;
```

#### <a name="building-module-manager-for-arm11-using-ac5"></a><span data-ttu-id="f9eb4-152">Compilación de administrador de módulos para ARM11 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-152">Building Module Manager for ARM11 using AC5</span></span>

<span data-ttu-id="f9eb4-153">Ejemplo sencillo de línea de comandos para compilar un administrador de módulos de ARM11 con AC5:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-153">A simple command-line example for building an ARM11 module manager using AC5:</span></span>

```dos
armasm -g --cpu ARM1136J-S --apcs /interwork tx_initialize_low_level.s
armcc -g -c -O2 --cpu ARM1136J-S --apcs /interwork demo_threadx_module_manager.c
armcc -g -c -O2 --cpu ARM1136J-S --apcs /interwork module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0 --first tx_initialize_low_level.o(Init) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-arm11-using-ac5"></a><span data-ttu-id="f9eb4-154">Atributos de API de habilitación de memoria externa para ARM11 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-154">Attributes for external memory enable API for ARM11 using AC5</span></span>

<span data-ttu-id="f9eb4-155">Esta característica no está habilitada en esta distribución.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-155">This feature not enabled on this port.</span></span>

## <a name="cortex-a7-processor"></a><span data-ttu-id="f9eb4-156">Procesador Cortex-A7</span><span class="sxs-lookup"><span data-stu-id="f9eb4-156">Cortex-A7 processor</span></span>

### <a name="cortex-a7-using-ac5"></a><span data-ttu-id="f9eb4-157">Cortex-A7 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-157">Cortex-A7 using AC5</span></span>

#### <a name="module-preamble-for-cortex-a7-using-ac5"></a><span data-ttu-id="f9eb4-158">Preámbulo de módulo para Cortex-A7 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-158">Module preamble for Cortex-A7 using AC5</span></span>

```armasm
    AREA  Init, CODE, READONLY

;    /* Define public symbols.  */

    EXPORT __txm_module_preamble

;    /* Define application-specific start/stop entry points for the module.  */

    IMPORT demo_module_start

;    /* Define common external references.  */

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|

__txm_module_preamble
    DCD       0x4D4F4455                                        ; Module ID
    DCD       0x5                                               ; Module Major Version
    DCD       0x3                                               ; Module Minor Version
    DCD       32                                                ; Module Preamble Size in 32-bit words
    DCD       0x12345678                                        ; Module ID (application defined)
    DCD       0x01000001                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-1:  Reserved
                                                                ;   Bit 0:  0 -> Privileged mode execution (no MMU protection)
                                                                ;           1 -> User mode execution (MMU protection)
    DCD       _txm_module_thread_shell_entry - . + .            ; Module Shell Entry Point
    DCD       demo_module_start - . + .                         ; Module Start Thread Entry Point
    DCD       0                                                 ; Module Stop Thread Entry Point
    DCD       1                                                 ; Module Start/Stop Thread Priority
    DCD       1024                                              ; Module Start/Stop Thread Stack Size
    DCD       _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
    DCD       1                                                 ; Module Callback Thread Priority
    DCD       1024                                              ; Module Callback Thread Stack Size
    DCD       |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|   ; Module Code Size
    DCD       0x4000                                            ; Module Data Size - default to 16K (need to make sure this is large enough for module's data needs!)
    DCD       0                                                 ; Reserved 0
    DCD       0                                                 ; Reserved 1
    DCD       0                                                 ; Reserved 2
    DCD       0                                                 ; Reserved 3
    DCD       0                                                 ; Reserved 4
    DCD       0                                                 ; Reserved 5
    DCD       0                                                 ; Reserved 6
    DCD       0                                                 ; Reserved 7
    DCD       0                                                 ; Reserved 8
    DCD       0                                                 ; Reserved 9
    DCD       0                                                 ; Reserved 10
    DCD       0                                                 ; Reserved 11
    DCD       0                                                 ; Reserved 12
    DCD       0                                                 ; Reserved 13
    DCD       0                                                 ; Reserved 14
    DCD       0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-a7-using-ac5"></a><span data-ttu-id="f9eb4-159">Propiedades de módulo para Cortex-A7 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-159">Module properties for Cortex-A7 using AC5</span></span>

| <span data-ttu-id="f9eb4-160">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-160">Bit</span></span> | <span data-ttu-id="f9eb4-161">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-161">Value</span></span> | <span data-ttu-id="f9eb4-162">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-162">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-163">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-163">0</span></span> | <span data-ttu-id="f9eb4-164">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-164">0</span></span><br /><span data-ttu-id="f9eb4-165">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-165">1</span></span> | <span data-ttu-id="f9eb4-166">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-166">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-167">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-167">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-168">[23-1]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-168">[23-1]</span></span> | <span data-ttu-id="f9eb4-169">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-169">0</span></span> | <span data-ttu-id="f9eb4-170">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-170">Reserved</span></span>
| <span data-ttu-id="f9eb4-171">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-171">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-172">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-172">0x00</span></span><br /><span data-ttu-id="f9eb4-173">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-173">0x01</span></span><br /><span data-ttu-id="f9eb4-174">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-174">0x02</span></span> | <span data-ttu-id="f9eb4-175">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-175">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-176">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-176">IAR</span></span><br /><span data-ttu-id="f9eb4-177">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-177">ARM</span></span><br /><span data-ttu-id="f9eb4-178">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-178">GNU</span></span> |

#### <a name="module-linker-for-cortex-a7-using-ac5"></a><span data-ttu-id="f9eb4-179">Enlazador de módulos para Cortex-A7 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-179">Module linker for Cortex-A7 using AC5</span></span>

<span data-ttu-id="f9eb4-180">Se compila en la línea de comandos; no hay ningún ejemplo de archivo de enlazador.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-180">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-a7-using-ac5"></a><span data-ttu-id="f9eb4-181">Compilación de módulos para Cortex-A7 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-181">Building Modules for Cortex-A7 using AC5</span></span>

<span data-ttu-id="f9eb4-182">Ejemplo sencillo de línea de comandos para compilar un módulo de Cortex-A7 con AC5:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-182">A simple command-line example for building a Cortex-A7 module using AC5:</span></span>

```dos
armasm -g --cpu=cortex-a7.no_neon --fpu=softvfp --apcs=/interwork/ropi/rwpi txm_module_preamble.s
armcc  -g --cpu=cortex-a7.no_neon --fpu=softvfp -c --apcs=/interwork/ropi/rwpi --lower_ropi demo_threadx_module.c
armlink -d -o demo_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-a7-using-ac5"></a><span data-ttu-id="f9eb4-183">Definición de extensión de subproceso para Cortex-A7 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-183">Thread extension definition for Cortex-A7 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2   ULONG   tx_thread_vfp_enable;                   \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-a7-using-ac5"></a><span data-ttu-id="f9eb4-184">Compilación de administrador de módulos para Cortex-A7 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-184">Building Module Manager for Cortex-A7 using AC5</span></span>

<span data-ttu-id="f9eb4-185">Ejemplo sencillo de línea de comandos para compilar un administrador de módulos de Cortex-A7 con AC5:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-185">A simple command-line example for building a Cortex-A7 module manager using AC5:</span></span>

```dos
armasm -g --cpu=cortex-a7.no_neon --fpu=softvfp --apcs=interwork tx_initialize_low_level.s
armcc -g --cpu=cortex-a7.no_neon --fpu=softvfp -c demo_threadx_module_manager.c
armcc -g --cpu=cortex-a7.no_neon --fpu=softvfp -c module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0x80000000 --first tx_initialize_low_level.o(VECTORS) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-a7-using-ac5"></a><span data-ttu-id="f9eb4-186">Atributos de API de habilitación de memoria externa para Cortex-A7 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-186">Attributes for external memory enable API for Cortex-A7 using AC5</span></span>

<span data-ttu-id="f9eb4-187">Los siguientes atributos se pueden usar para configurar valores de memoria compartida:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-187">The following attributes can be used to set up shared memory settings:</span></span>
| <span data-ttu-id="f9eb4-188">Parámetro de atributo</span><span class="sxs-lookup"><span data-stu-id="f9eb4-188">Attribute parameter</span></span> | <span data-ttu-id="f9eb4-189">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-189">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f9eb4-190">TXM_MMU_ATTRIBUTE_XN</span><span class="sxs-lookup"><span data-stu-id="f9eb4-190">TXM_MMU_ATTRIBUTE_XN</span></span> | <span data-ttu-id="f9eb4-191">No ejecutar nunca</span><span class="sxs-lookup"><span data-stu-id="f9eb4-191">Execute Never</span></span> |
| <span data-ttu-id="f9eb4-192">TXM_MMU_ATTRIBUTE_B</span><span class="sxs-lookup"><span data-stu-id="f9eb4-192">TXM_MMU_ATTRIBUTE_B</span></span> | <span data-ttu-id="f9eb4-193">Valor B</span><span class="sxs-lookup"><span data-stu-id="f9eb4-193">B setting</span></span> |
| <span data-ttu-id="f9eb4-194">TXM_MMU_ATTRIBUTE_C</span><span class="sxs-lookup"><span data-stu-id="f9eb4-194">TXM_MMU_ATTRIBUTE_C</span></span> | <span data-ttu-id="f9eb4-195">Valor C</span><span class="sxs-lookup"><span data-stu-id="f9eb4-195">C setting</span></span> |
| <span data-ttu-id="f9eb4-196">TXM_MMU_ATTRIBUTE_AP</span><span class="sxs-lookup"><span data-stu-id="f9eb4-196">TXM_MMU_ATTRIBUTE_AP</span></span> | <span data-ttu-id="f9eb4-197">Valor AP</span><span class="sxs-lookup"><span data-stu-id="f9eb4-197">AP setting</span></span> |
| <span data-ttu-id="f9eb4-198">TXM_MMU_ATTRIBUTE_TEX</span><span class="sxs-lookup"><span data-stu-id="f9eb4-198">TXM_MMU_ATTRIBUTE_TEX</span></span> | <span data-ttu-id="f9eb4-199">Valor TEX</span><span class="sxs-lookup"><span data-stu-id="f9eb4-199">TEX setting</span></span> |

<span data-ttu-id="f9eb4-200">Consulte la documentación de ARM para ver cómo se configuran estos valores.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-200">See ARM documentation for how these settings are configured.</span></span>

## <a name="cortex-m3-processor"></a><span data-ttu-id="f9eb4-201">Procesador Cortex-M3</span><span class="sxs-lookup"><span data-stu-id="f9eb4-201">Cortex-M3 processor</span></span>

### <a name="cortex-m3-using-ac5"></a><span data-ttu-id="f9eb4-202">Cortex-M3 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-202">Cortex-M3 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m3-using-ac5"></a><span data-ttu-id="f9eb4-203">Preámbulo de módulo para Cortex-M3 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-203">Module preamble for Cortex-M3 using AC5</span></span>

```armasm
    AREA Init, CODE, READONLY

    PRESERVE8

    ; Define public symbols

    EXPORT __txm_module_preamble

    ; Define application-specific start/stop entry points for the module

    EXTERN demo_module_start

    ; Define common external references

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|
    IMPORT  |Image$$ER_RW$$RW$$Length|
    IMPORT  |Image$$ER_RW$$ZI$$Length|
    IMPORT  |Image$$ER_ZI$$ZI$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                          ; Module ID
    DCD     0x6                                                 ; Module Major Version
    DCD     0x1                                                 ; Module Minor Version
    DCD     32                                                  ; Module Preamble Size in 32-bit words
    DCD     0x12345678                                          ; Module ID (application defined)
    DCD     0x01000007                                          ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected)
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
    DCD     _txm_module_thread_shell_entry - __txm_module_preamble              ; Module Shell Entry Point
    DCD     demo_module_start - __txm_module_preamble           ; Module Start Thread Entry Point
    DCD     0                                                   ; Module Stop Thread Entry Point
    DCD     1                                                   ; Module Start/Stop Thread Priority
    DCD     1024                                                ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - __txm_module_preamble   ; Module Callback Thread Entry
    DCD     1                                                   ; Module Callback Thread Priority
    DCD     1024                                                ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|         ; Module Code Size
    DCD     |Image$$ER_RW$$Length| + |Image$$ER_ZI$$ZI$$Length| ; Module Data Size
    DCD     0                                                   ; Reserved 0
    DCD     0                                                   ; Reserved 1
    DCD     0                                                   ; Reserved 2
    DCD     0                                                   ; Reserved 3
    DCD     0                                                   ; Reserved 4
    DCD     0                                                   ; Reserved 5
    DCD     0                                                   ; Reserved 6
    DCD     0                                                   ; Reserved 7
    DCD     0                                                   ; Reserved 8
    DCD     0                                                   ; Reserved 9
    DCD     0                                                   ; Reserved 10
    DCD     0                                                   ; Reserved 11
    DCD     0                                                   ; Reserved 12
    DCD     0                                                   ; Reserved 13
    DCD     0                                                   ; Reserved 14
    DCD     0                                                   ; Reserved 15

    END

```

#### <a name="module-properties-for-cortex-m3-using-ac5"></a><span data-ttu-id="f9eb4-204">Propiedades de módulo para Cortex-M3 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-204">Module properties for Cortex-M3 using AC5</span></span>

| <span data-ttu-id="f9eb4-205">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-205">Bit</span></span> | <span data-ttu-id="f9eb4-206">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-206">Value</span></span> | <span data-ttu-id="f9eb4-207">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-207">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-208">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-208">0</span></span> | <span data-ttu-id="f9eb4-209">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-209">0</span></span><br /><span data-ttu-id="f9eb4-210">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-210">1</span></span> | <span data-ttu-id="f9eb4-211">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-211">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-212">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-212">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-213">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-213">1</span></span> | <span data-ttu-id="f9eb4-214">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-214">0</span></span><br /><span data-ttu-id="f9eb4-215">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-215">1</span></span> | <span data-ttu-id="f9eb4-216">Sin protección de MPU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-216">No MPU protection</span></span><br /><span data-ttu-id="f9eb4-217">Protección de MPU (debe estar seleccionado el modo de usuario)</span><span class="sxs-lookup"><span data-stu-id="f9eb4-217">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f9eb4-218">2</span><span class="sxs-lookup"><span data-stu-id="f9eb4-218">2</span></span> | <span data-ttu-id="f9eb4-219">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-219">0</span></span><br /><span data-ttu-id="f9eb4-220">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-220">1</span></span> | <span data-ttu-id="f9eb4-221">Deshabilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-221">Disable shared/external memory access</span></span><br /><span data-ttu-id="f9eb4-222">Habilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-222">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f9eb4-223">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-223">[23-3]</span></span> | <span data-ttu-id="f9eb4-224">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-224">0</span></span> | <span data-ttu-id="f9eb4-225">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-225">Reserved</span></span>
| <span data-ttu-id="f9eb4-226">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-226">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-227">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-227">0x00</span></span><br /><span data-ttu-id="f9eb4-228">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-228">0x01</span></span><br /><span data-ttu-id="f9eb4-229">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-229">0x02</span></span> | <span data-ttu-id="f9eb4-230">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-230">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-231">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-231">IAR</span></span><br /><span data-ttu-id="f9eb4-232">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-232">ARM</span></span><br /><span data-ttu-id="f9eb4-233">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-233">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-ac5"></a><span data-ttu-id="f9eb4-234">Enlazador de módulos para Cortex-M3 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-234">Module linker for Cortex-M3 using AC5</span></span>

<span data-ttu-id="f9eb4-235">No se proporciona ningún archivo de enlazador de ejemplo; el enlace se realiza en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-235">No example linker file is provided; linking is done on the command line.</span></span> <span data-ttu-id="f9eb4-236">Consulte la siguiente sección.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-236">See next section.</span></span>

#### <a name="building-modules-for-cortex-m3-using-ac5"></a><span data-ttu-id="f9eb4-237">Compilación de módulos para Cortex-M3 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-237">Building Modules for Cortex-M3 using AC5</span></span>

<span data-ttu-id="f9eb4-238">A continuación se muestra un script de compilación de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-238">An example build script is provided:</span></span>

```dos
armasm -g --cpu=cortex-m3 --apcs=/interwork/ropi/rwpi txm_module_preamble.S
armcc  -g --cpu=cortex-m3 -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro=0x30000 --rw=0x40000 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m3-using-ac5"></a><span data-ttu-id="f9eb4-239">Definición de extensión de subproceso para Cortex-M3 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-239">Thread extension definition for Cortex-M3 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m3-using-ac5"></a><span data-ttu-id="f9eb4-240">Compilación de administrador de módulos para Cortex-M3 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-240">Building Module Manager for Cortex-M3 using AC5</span></span>

<span data-ttu-id="f9eb4-241">Consulte el archivo build_threadx_module_manager_demo.bat de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-241">See example build_threadx_module_manager_demo.bat:</span></span>

```dos
armasm -g --cpu=cortex-m3 --apcs=interwork tx_initialize_low_level.S
armcc -g --cpu=cortex-m3 -c -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module_manager.c
armlink -d -o sample_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list sample_threadx_module_manager.map tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-ac5"></a><span data-ttu-id="f9eb4-242">Atributos de API de habilitación de memoria externa para Cortex-M3 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-242">Attributes for external memory enable API for Cortex-M3 using AC5</span></span>

<span data-ttu-id="f9eb4-243">El módulo siempre tiene acceso de lectura a la memoria compartida.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-243">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="f9eb4-244">Parámetro de atributo</span><span class="sxs-lookup"><span data-stu-id="f9eb4-244">Attribute parameter</span></span> | <span data-ttu-id="f9eb4-245">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-245">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f9eb4-246">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-246">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f9eb4-247">Acceso de escritura</span><span class="sxs-lookup"><span data-stu-id="f9eb4-247">Write access</span></span> |

### <a name="cortex-m3-using-ac6"></a><span data-ttu-id="f9eb4-248">Cortex-M3 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-248">Cortex-M3 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m3-using-ac6"></a><span data-ttu-id="f9eb4-249">Preámbulo de módulo para Cortex-M3 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-249">Module preamble for Cortex-M3 using AC6</span></span>

```armasm
    .text
    .align 4
    .syntax unified
    .section Init
    
    // Define public symbols
    .global __txm_module_preamble

    // Define application-specific start/stop entry points for the module
    .global demo_module_start

    // Define common external references
    .global  _txm_module_thread_shell_entry
    .global  _txm_module_callback_request_thread_entry

    .eabi_attribute Tag_ABI_PCS_RO_data, 1
    .eabi_attribute Tag_ABI_PCS_R9_use,  1
    .eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
    .dc.l   0x4D4F4455                                          // Module ID
    .dc.l   0x6                                                 // Module Major Version
    .dc.l   0x1                                                 // Module Minor Version
    .dc.l   32                                                  // Module Preamble Size in 32-bit words
    .dc.l   0x12345678                                          // Module ID (application defined)
    .dc.l   0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    .dc.l   _txm_module_thread_shell_entry - __txm_module_preamble // Module Shell Entry Point
    .dc.l   demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    .dc.l   0                                                   // Module Stop Thread Entry Point
    .dc.l   1                                                   // Module Start/Stop Thread Priority
    .dc.l   1024                                                // Module Start/Stop Thread Stack Size
    .dc.l   _txm_module_callback_request_thread_entry - __txm_module_preamble // Module Callback Thread Entry
    .dc.l   1                                                   // Module Callback Thread Priority
    .dc.l   1024                                                // Module Callback Thread Stack Size
    .dc.l   0x10000                                             // Module Code Size
    .dc.l   0x10000                                             // Module Data Size
    .dc.l   0                                                   // Reserved 0
    .dc.l   0                                                   // Reserved 1
    .dc.l   0                                                   // Reserved 2
    .dc.l   0                                                   // Reserved 3
    .dc.l   0                                                   // Reserved 4
    .dc.l   0                                                   // Reserved 5
    .dc.l   0                                                   // Reserved 6
    .dc.l   0                                                   // Reserved 7
    .dc.l   0                                                   // Reserved 8
    .dc.l   0                                                   // Reserved 9
    .dc.l   0                                                   // Reserved 10
    .dc.l   0                                                   // Reserved 11
    .dc.l   0                                                   // Reserved 12
    .dc.l   0                                                   // Reserved 13
    .dc.l   0                                                   // Reserved 14
    .dc.l   0                                                   // Reserved 15
```

#### <a name="module-properties-for-cortex-m3-using-ac6"></a><span data-ttu-id="f9eb4-250">Propiedades de módulo para Cortex-M3 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-250">Module properties for Cortex-M3 using AC6</span></span>

| <span data-ttu-id="f9eb4-251">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-251">Bit</span></span> | <span data-ttu-id="f9eb4-252">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-252">Value</span></span> | <span data-ttu-id="f9eb4-253">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-253">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-254">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-254">0</span></span> | <span data-ttu-id="f9eb4-255">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-255">0</span></span><br /><span data-ttu-id="f9eb4-256">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-256">1</span></span> | <span data-ttu-id="f9eb4-257">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-257">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-258">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-258">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-259">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-259">1</span></span> | <span data-ttu-id="f9eb4-260">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-260">0</span></span><br /><span data-ttu-id="f9eb4-261">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-261">1</span></span> | <span data-ttu-id="f9eb4-262">Sin protección de MPU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-262">No MPU protection</span></span><br /><span data-ttu-id="f9eb4-263">Protección de MPU (debe estar seleccionado el modo de usuario)</span><span class="sxs-lookup"><span data-stu-id="f9eb4-263">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f9eb4-264">2</span><span class="sxs-lookup"><span data-stu-id="f9eb4-264">2</span></span> | <span data-ttu-id="f9eb4-265">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-265">0</span></span><br /><span data-ttu-id="f9eb4-266">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-266">1</span></span> | <span data-ttu-id="f9eb4-267">Deshabilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-267">Disable shared/external memory access</span></span><br /><span data-ttu-id="f9eb4-268">Habilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-268">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f9eb4-269">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-269">[23-3]</span></span> | <span data-ttu-id="f9eb4-270">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-270">0</span></span> | <span data-ttu-id="f9eb4-271">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-271">Reserved</span></span>
| <span data-ttu-id="f9eb4-272">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-272">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-273">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-273">0x00</span></span><br /><span data-ttu-id="f9eb4-274">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-274">0x01</span></span><br /><span data-ttu-id="f9eb4-275">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-275">0x02</span></span> | <span data-ttu-id="f9eb4-276">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-276">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-277">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-277">IAR</span></span><br /><span data-ttu-id="f9eb4-278">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-278">ARM</span></span><br /><span data-ttu-id="f9eb4-279">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-279">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-ac6"></a><span data-ttu-id="f9eb4-280">Enlazador de módulos para Cortex-M3 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-280">Module linker for Cortex-M3 using AC6</span></span>

<span data-ttu-id="f9eb4-281">No se usa ningún archivo de enlazador.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-281">No linker file is used.</span></span> <span data-ttu-id="f9eb4-282">Consulte la configuración del proyecto.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-282">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m3-using-ac6"></a><span data-ttu-id="f9eb4-283">Compilación de módulos para Cortex-M3 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-283">Building Modules for Cortex-M3 using AC6</span></span>

<span data-ttu-id="f9eb4-284">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-284">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-285">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de muestra y el proyecto de administrador de módulos de muestra.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-285">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m3-using-ac6"></a><span data-ttu-id="f9eb4-286">Definición de extensión de subproceso para Cortex-M3 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-286">Thread extension definition for Cortex-M3 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m3-using-ac6"></a><span data-ttu-id="f9eb4-287">Compilación de administrador de módulos para Cortex-M3 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-287">Building Module Manager for Cortex-M3 using AC6</span></span>

<span data-ttu-id="f9eb4-288">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-288">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-289">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de muestra y el proyecto de administrador de módulos de muestra.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-289">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-ac6"></a><span data-ttu-id="f9eb4-290">Atributos de API de habilitación de memoria externa para Cortex-M3 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-290">Attributes for external memory enable API for Cortex-M3 using AC6</span></span>

<span data-ttu-id="f9eb4-291">El módulo siempre tiene acceso de lectura a la memoria compartida.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-291">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="f9eb4-292">Parámetro de atributo</span><span class="sxs-lookup"><span data-stu-id="f9eb4-292">Attribute parameter</span></span> | <span data-ttu-id="f9eb4-293">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-293">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f9eb4-294">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-294">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f9eb4-295">Acceso de escritura</span><span class="sxs-lookup"><span data-stu-id="f9eb4-295">Write access</span></span> |

### <a name="cortex-m3-using-gnu"></a><span data-ttu-id="f9eb4-296">Cortex-M3 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-296">Cortex-M3 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m3-using-gnu"></a><span data-ttu-id="f9eb4-297">Preámbulo de módulo para Cortex-M3 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-297">Module preamble for Cortex-M3 using GNU</span></span>

```armasm
    .text
    .align 4
    .syntax unified

    /* Define public symbols.  */
    .global __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    .global demo_module_start

    /* Define common external refrences.  */
    .global _txm_module_thread_shell_entry
    .global _txm_module_callback_request_thread_entry

__txm_module_preamble:
    .dc.l      0x4D4F4455                                       // Module ID
    .dc.l      0x6                                              // Module Major Version
    .dc.l      0x1                                              // Module Minor Version
    .dc.l      32                                               // Module Preamble Size in 32-bit words
    .dc.l      0x12345678                                       // Module ID (application defined)
    .dc.l      0x02000007                                       // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    .dc.l      _txm_module_thread_shell_entry - . - 0           // Module Shell Entry Point
    .dc.l      demo_module_start - . - 0                        // Module Start Thread Entry Point
    .dc.l      0                                                // Module Stop Thread Entry Point 
    .dc.l      1                                                // Module Start/Stop Thread Priority
    .dc.l      1024                                             // Module Start/Stop Thread Stack Size
    .dc.l      _txm_module_callback_request_thread_entry - . - 0 // Module Callback Thread Entry
    .dc.l      1                                                // Module Callback Thread Priority
    .dc.l      1024                                             // Module Callback Thread Stack Size
    .dc.l      __code_size__                                    // Module Code Size
    .dc.l      __data_size__                                    // Module Data Size
    .dc.l      0                                                // Reserved 0
    .dc.l      0                                                // Reserved 1
    .dc.l      0                                                // Reserved 2
    .dc.l      0                                                // Reserved 3
    .dc.l      0                                                // Reserved 4
    .dc.l      0                                                // Reserved 5
    .dc.l      0                                                // Reserved 6
    .dc.l      0                                                // Reserved 7
    .dc.l      0                                                // Reserved 8
    .dc.l      0                                                // Reserved 9
    .dc.l      0                                                // Reserved 10
    .dc.l      0                                                // Reserved 11
    .dc.l      0                                                // Reserved 12
    .dc.l      0                                                // Reserved 13
    .dc.l      0                                                // Reserved 14
    .dc.l      0                                                // Reserved 15

```

#### <a name="module-properties-for-cortex-m3-using-gnu"></a><span data-ttu-id="f9eb4-298">Propiedades de módulo para Cortex-M3 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-298">Module properties for Cortex-M3 using GNU</span></span>

| <span data-ttu-id="f9eb4-299">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-299">Bit</span></span> | <span data-ttu-id="f9eb4-300">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-300">Value</span></span> | <span data-ttu-id="f9eb4-301">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-301">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-302">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-302">0</span></span> | <span data-ttu-id="f9eb4-303">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-303">0</span></span><br /><span data-ttu-id="f9eb4-304">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-304">1</span></span> | <span data-ttu-id="f9eb4-305">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-305">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-306">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-306">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-307">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-307">1</span></span> | <span data-ttu-id="f9eb4-308">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-308">0</span></span><br /><span data-ttu-id="f9eb4-309">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-309">1</span></span> | <span data-ttu-id="f9eb4-310">Sin protección de MPU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-310">No MPU protection</span></span><br /><span data-ttu-id="f9eb4-311">Protección de MPU (debe estar seleccionado el modo de usuario)</span><span class="sxs-lookup"><span data-stu-id="f9eb4-311">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f9eb4-312">2</span><span class="sxs-lookup"><span data-stu-id="f9eb4-312">2</span></span> | <span data-ttu-id="f9eb4-313">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-313">0</span></span><br /><span data-ttu-id="f9eb4-314">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-314">1</span></span> | <span data-ttu-id="f9eb4-315">Deshabilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-315">Disable shared/external memory access</span></span><br /><span data-ttu-id="f9eb4-316">Habilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-316">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f9eb4-317">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-317">[23-3]</span></span> | <span data-ttu-id="f9eb4-318">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-318">0</span></span> | <span data-ttu-id="f9eb4-319">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-319">Reserved</span></span>
| <span data-ttu-id="f9eb4-320">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-320">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-321">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-321">0x00</span></span><br /><span data-ttu-id="f9eb4-322">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-322">0x01</span></span><br /><span data-ttu-id="f9eb4-323">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-323">0x02</span></span> | <span data-ttu-id="f9eb4-324">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-324">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-325">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-325">IAR</span></span><br /><span data-ttu-id="f9eb4-326">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-326">ARM</span></span><br /><span data-ttu-id="f9eb4-327">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-327">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-gnu"></a><span data-ttu-id="f9eb4-328">Enlazador de módulos para Cortex-M3 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-328">Module linker for Cortex-M3 using GNU</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x00030000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x00030000;
  __FLASH_segment_end__   = 0x00040000;
  __RAM_segment_start__   = 0;
  __RAM_segment_end__     = 0x8000;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  } 
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);
 
  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-cortex-m3-using-gnu"></a><span data-ttu-id="f9eb4-329">Compilación de módulos para Cortex-M3 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-329">Building Modules for Cortex-M3 using GNU</span></span>

<span data-ttu-id="f9eb4-330">Consulte el archivo build_threadx_module_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-330">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m3 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m3-using-gnu"></a><span data-ttu-id="f9eb4-331">Definición de extensión de subproceso para Cortex-M3 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-331">Thread extension definition for Cortex-M3 using GNU</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m3-using-gnu"></a><span data-ttu-id="f9eb4-332">Compilación de administrador de módulos para Cortex-M3 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-332">Building Module Manager for Cortex-M3 using GNU</span></span>

<span data-ttu-id="f9eb4-333">Consulte el archivo build_threadx_module_manager_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-333">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb tx_simulator_startup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb cortexm_crt0.S
arm-none-eabi-ld -A cortex-m3 -ereset_handler -T sample_threadx.ld tx_simulator_startup.o cortexm_crt0.o sample_threadx_module_manager.o tx.a  libc.a -o sample_threadx_module_manager.axf -M > sample_threadx_module_manager.map
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-gnu"></a><span data-ttu-id="f9eb4-334">Atributos de API de habilitación de memoria externa para Cortex-M3 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-334">Attributes for external memory enable API for Cortex-M3 using GNU</span></span>

<span data-ttu-id="f9eb4-335">El módulo siempre tiene acceso de lectura a la memoria compartida.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-335">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="f9eb4-336">Parámetro de atributo</span><span class="sxs-lookup"><span data-stu-id="f9eb4-336">Attribute parameter</span></span> | <span data-ttu-id="f9eb4-337">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-337">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f9eb4-338">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-338">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f9eb4-339">Acceso de escritura</span><span class="sxs-lookup"><span data-stu-id="f9eb4-339">Write access</span></span> |

### <a name="cortex-m3-using-iar"></a><span data-ttu-id="f9eb4-340">Cortex-M3 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-340">Cortex-M3 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m3-using-iar"></a><span data-ttu-id="f9eb4-341">Preámbulo de módulo para Cortex-M3 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-341">Module preamble for Cortex-M3 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external references.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000007                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-3: Reserved
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution


    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m3-using-iar"></a><span data-ttu-id="f9eb4-342">Propiedades de módulo para Cortex-M3 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-342">Module properties for Cortex-M3 using IAR</span></span>

| <span data-ttu-id="f9eb4-343">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-343">Bit</span></span> | <span data-ttu-id="f9eb4-344">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-344">Value</span></span> | <span data-ttu-id="f9eb4-345">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-345">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-346">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-346">0</span></span> | <span data-ttu-id="f9eb4-347">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-347">0</span></span><br /><span data-ttu-id="f9eb4-348">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-348">1</span></span> | <span data-ttu-id="f9eb4-349">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-349">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-350">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-350">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-351">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-351">1</span></span> | <span data-ttu-id="f9eb4-352">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-352">0</span></span><br /><span data-ttu-id="f9eb4-353">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-353">1</span></span> | <span data-ttu-id="f9eb4-354">Sin protección de MPU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-354">No MPU protection</span></span><br /><span data-ttu-id="f9eb4-355">Protección de MPU (debe estar seleccionado el modo de usuario)</span><span class="sxs-lookup"><span data-stu-id="f9eb4-355">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f9eb4-356">2</span><span class="sxs-lookup"><span data-stu-id="f9eb4-356">2</span></span> | <span data-ttu-id="f9eb4-357">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-357">0</span></span><br /><span data-ttu-id="f9eb4-358">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-358">1</span></span> | <span data-ttu-id="f9eb4-359">Deshabilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-359">Disable shared/external memory access</span></span><br /><span data-ttu-id="f9eb4-360">Habilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-360">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f9eb4-361">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-361">[23-3]</span></span> | <span data-ttu-id="f9eb4-362">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-362">0</span></span> | <span data-ttu-id="f9eb4-363">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-363">Reserved</span></span>
| <span data-ttu-id="f9eb4-364">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-364">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-365">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-365">0x00</span></span><br /><span data-ttu-id="f9eb4-366">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-366">0x01</span></span><br /><span data-ttu-id="f9eb4-367">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-367">0x02</span></span> | <span data-ttu-id="f9eb4-368">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-368">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-369">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-369">IAR</span></span><br /><span data-ttu-id="f9eb4-370">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-370">ARM</span></span><br /><span data-ttu-id="f9eb4-371">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-371">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-iar"></a><span data-ttu-id="f9eb4-372">Enlazador de módulos para Cortex-M3 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-372">Module linker for Cortex-M3 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__ = 0x0;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x080f0000;
define symbol __ICFEDIT_region_ROM_end__   = 0x080fffff;
define symbol __ICFEDIT_region_RAM_start__ = 0x64002800;
define symbol __ICFEDIT_region_RAM_end__   = 0x64100000;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

//define block CSTACK    with alignment = 8, size = __ICFEDIT_size_cstack__   { };
//define block SVC_STACK with alignment = 8, size = __ICFEDIT_size_svcstack__ { };
//define block IRQ_STACK with alignment = 8, size = __ICFEDIT_size_irqstack__ { };
//define block FIQ_STACK with alignment = 8, size = __ICFEDIT_size_fiqstack__ { };
//define block UND_STACK with alignment = 8, size = __ICFEDIT_size_undstack__ { };
//define block ABT_STACK with alignment = 8, size = __ICFEDIT_size_abtstack__ { };
define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

//place at address mem:__ICFEDIT_intvec_start__ { readonly section .intvec };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble_stm32f2xx.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m3-using-iar"></a><span data-ttu-id="f9eb4-373">Compilación de módulos para Cortex-M3 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-373">Building Modules for Cortex-M3 using IAR</span></span>

<span data-ttu-id="f9eb4-374">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-374">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-375">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de demostración y el proyecto de administrador de módulos de demostración.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-375">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m3-using-iar"></a><span data-ttu-id="f9eb4-376">Definición de extensión de subproceso para Cortex-M3 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-376">Thread extension definition for Cortex-M3 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m3-using-iar"></a><span data-ttu-id="f9eb4-377">Compilación de administrador de módulos para Cortex-M3 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-377">Building Module Manager for Cortex-M3 using IAR</span></span>

<span data-ttu-id="f9eb4-378">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-378">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-379">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de demostración y el proyecto de administrador de módulos de demostración.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-379">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-iar"></a><span data-ttu-id="f9eb4-380">Atributos de API de habilitación de memoria externa para Cortex-M3 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-380">Attributes for external memory enable API for Cortex-M3 using IAR</span></span>

<span data-ttu-id="f9eb4-381">El módulo siempre tiene acceso de lectura a la memoria compartida.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-381">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="f9eb4-382">Parámetro de atributo</span><span class="sxs-lookup"><span data-stu-id="f9eb4-382">Attribute parameter</span></span> | <span data-ttu-id="f9eb4-383">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-383">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f9eb4-384">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-384">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f9eb4-385">Acceso de escritura</span><span class="sxs-lookup"><span data-stu-id="f9eb4-385">Write access</span></span> |

## <a name="cortex-m33-processor"></a><span data-ttu-id="f9eb4-386">Procesador Cortex-M33</span><span class="sxs-lookup"><span data-stu-id="f9eb4-386">Cortex-M33 processor</span></span>

### <a name="cortex-m33-using-ac6"></a><span data-ttu-id="f9eb4-387">Cortex-M33 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-387">Cortex-M33 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m33-using-ac6"></a><span data-ttu-id="f9eb4-388">Preámbulo de módulo para Cortex-M33 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-388">Module preamble for Cortex-M33 using AC6</span></span>

```c
    .text
    .align 4
    .syntax unified
    .section RESET
    
    // Define public symbols
    .global __txm_module_preamble

    // Define application-specific start/stop entry points for the module
    .global demo_module_start

    // Define common external references
    .global  _txm_module_thread_shell_entry
    .global  _txm_module_callback_request_thread_entry

    .eabi_attribute Tag_ABI_PCS_RO_data, 1
    .eabi_attribute Tag_ABI_PCS_R9_use,  1
    .eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
    .dc.l   0x4D4F4455                                          // Module ID
    .dc.l   0x6                                                 // Module Major Version
    .dc.l   0x1                                                 // Module Minor Version
    .dc.l   32                                                  // Module Preamble Size in 32-bit words
    .dc.l   0x12345678                                          // Module ID (application defined)
    .dc.l   0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    .dc.l   _txm_module_thread_shell_entry - __txm_module_preamble // Module Shell Entry Point
    .dc.l   demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    .dc.l   0                                                   // Module Stop Thread Entry Point
    .dc.l   1                                                   // Module Start/Stop Thread Priority
    .dc.l   1024                                                // Module Start/Stop Thread Stack Size
    .dc.l   _txm_module_callback_request_thread_entry - __txm_module_preamble // Module Callback Thread Entry
    .dc.l   1                                                   // Module Callback Thread Priority
    .dc.l   1024                                                // Module Callback Thread Stack Size
    //the tools can't add two symbols together, but it should look like this:
    //.dc.l   Image$$ER_RO$$Length + Image$$ER_RW$$Length         // Module Code Size
    //.dc.l   Image$$ER_RW$$Length + Image$$ER_ZI$$ZI$$Length     // Module Data Size
    //so instead we'll define hard values:
    .dc.l   0x4000                                              // Module Code Size
    .dc.l   0x4000                                              // Module Data Size
    .dc.l   0                                                   // Reserved 0
    .dc.l   0                                                   // Reserved 1
    .dc.l   0                                                   // Reserved 2
    .dc.l   0                                                   // Reserved 3
    .dc.l   0                                                   // Reserved 4
    .dc.l   0                                                   // Reserved 5
    .dc.l   0                                                   // Reserved 6
    .dc.l   0                                                   // Reserved 7
    .dc.l   0                                                   // Reserved 8
    .dc.l   0                                                   // Reserved 9
    .dc.l   0                                                   // Reserved 10
    .dc.l   0                                                   // Reserved 11
    .dc.l   0                                                   // Reserved 12
    .dc.l   0                                                   // Reserved 13
    .dc.l   0                                                   // Reserved 14
    .dc.l   0                                                   // Reserved 15
```

#### <a name="module-properties-for-cortex-m33-using-ac6"></a><span data-ttu-id="f9eb4-389">Propiedades de módulo para Cortex-M33 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-389">Module properties for Cortex-M33 using AC6</span></span>

| <span data-ttu-id="f9eb4-390">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-390">Bit</span></span> | <span data-ttu-id="f9eb4-391">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-391">Value</span></span> | <span data-ttu-id="f9eb4-392">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-392">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-393">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-393">0</span></span> | <span data-ttu-id="f9eb4-394">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-394">0</span></span><br /><span data-ttu-id="f9eb4-395">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-395">1</span></span> | <span data-ttu-id="f9eb4-396">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-396">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-397">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-397">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-398">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-398">1</span></span> | <span data-ttu-id="f9eb4-399">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-399">0</span></span><br /><span data-ttu-id="f9eb4-400">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-400">1</span></span> | <span data-ttu-id="f9eb4-401">Sin protección de MPU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-401">No MPU protection</span></span><br /><span data-ttu-id="f9eb4-402">Protección de MPU (debe estar seleccionado el modo de usuario)</span><span class="sxs-lookup"><span data-stu-id="f9eb4-402">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f9eb4-403">2</span><span class="sxs-lookup"><span data-stu-id="f9eb4-403">2</span></span> | <span data-ttu-id="f9eb4-404">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-404">0</span></span><br /><span data-ttu-id="f9eb4-405">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-405">1</span></span> | <span data-ttu-id="f9eb4-406">Deshabilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-406">Disable shared/external memory access</span></span><br /><span data-ttu-id="f9eb4-407">Habilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-407">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f9eb4-408">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-408">[23-3]</span></span> | <span data-ttu-id="f9eb4-409">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-409">0</span></span> | <span data-ttu-id="f9eb4-410">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-410">Reserved</span></span>
| <span data-ttu-id="f9eb4-411">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-411">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-412">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-412">0x00</span></span><br /><span data-ttu-id="f9eb4-413">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-413">0x01</span></span><br /><span data-ttu-id="f9eb4-414">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-414">0x02</span></span> | <span data-ttu-id="f9eb4-415">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-415">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-416">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-416">IAR</span></span><br /><span data-ttu-id="f9eb4-417">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-417">ARM</span></span><br /><span data-ttu-id="f9eb4-418">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-418">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-ac6"></a><span data-ttu-id="f9eb4-419">Enlazador de módulos para Cortex-M33 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-419">Module linker for Cortex-M33 using AC6</span></span>

<span data-ttu-id="f9eb4-420">No se necesita ningún archivo de enlazador para la cadena de herramientas Keil.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-420">No linker file needed for Keil toolchain.</span></span> <span data-ttu-id="f9eb4-421">Consulte la configuración de compilación en el proyecto de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-421">See build settings in example project.</span></span>
<span data-ttu-id="f9eb4-422">A continuación se enumeran opciones importantes del enlazador:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-422">Important linker options are listed below:</span></span>

```c
--entry demo_module_start --first __txm_module_preamble
```

#### <a name="building-modules-for-cortex-m33-using-ac6"></a><span data-ttu-id="f9eb4-423">Compilación de módulos para Cortex-M33 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-423">Building Modules for Cortex-M33 using AC6</span></span>

<span data-ttu-id="f9eb4-424">Configuración del compilador:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-424">Compiler settings:</span></span>

```c
-xc -std=c99 --target=arm-arm-none-eabi -mcpu=cortex-m33 -mfpu=fpv5-sp-d16 -mfloat-abi=hard -c
-fno-rtti -funsigned-char -fshort-enums -fshort-wchar
-mlittle-endian -gdwarf-3 -fropi -frwpi -O1 -ffunction-sections -Wno-packed -Wno-missing-variable-declarations -Wno-missing-prototypes -Wno-missing-noreturn -Wno-sign-conversion -Wno-nonportable-include-path -Wno-reserved-id-macro -Wno-unused-macros -Wno-documentation-unknown-command -Wno-documentation -Wno-license-management -Wno-parentheses-equality -I ../../../../../common_modules/inc -I ../../../../../common/inc -I ../../../../../ports_module/cortex_m33/ac6/inc -I ../demo_secure_zone
-I./RTE/_FVP_Simulation_Model
-IC:/Users/your_path/AppData/Local/Arm/Packs/ARM/CMSIS/5.5.1/CMSIS/Core/Include
-IC:/Users/your_path/AppData/Local/Arm/Packs/ARM/CMSIS/5.5.1/Device/ARM/ARMCM33/Include
-D__UVISION_VERSION="531" -D_RTE_ -DARMCM33_DSP_FP_TZ -D_RTE_
-o ./Objects/*.o -MD
```

#### <a name="thread-extension-definition-for-cortex-m33-using-ac6"></a><span data-ttu-id="f9eb4-425">Definición de extensión de subproceso para Cortex-M33 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-425">Thread extension definition for Cortex-M33 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2                   VOID    *tx_thread_module_instance_ptr;         \
                                                VOID    *tx_thread_module_entry_info_ptr;       \
                                                ULONG   tx_thread_module_current_user_mode;     \
                                                ULONG   tx_thread_module_user_mode;             \
                                                ULONG   tx_thread_module_saved_lr;              \
                                                VOID    *tx_thread_module_kernel_stack_start;   \
                                                VOID    *tx_thread_module_kernel_stack_end;     \
                                                ULONG   tx_thread_module_kernel_stack_size;     \
                                                VOID    *tx_thread_module_stack_ptr;            \
                                                VOID    *tx_thread_module_stack_start;          \
                                                VOID    *tx_thread_module_stack_end;            \
                                                ULONG   tx_thread_module_stack_size;            \
                                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m33-using-ac6"></a><span data-ttu-id="f9eb4-426">Compilación de administrador de módulos para Cortex-M33 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-426">Building Module Manager for Cortex-M33 using AC6</span></span>

<span data-ttu-id="f9eb4-427">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-427">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-428">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules y los proyectos sample_threadx_module y demo_threadx_non-secure_zone.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-428">Build the ThreadX library, ThreadX Modules library, sample_threadx_module project, and demo_threadx_non-secure_zone project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-ac6"></a><span data-ttu-id="f9eb4-429">Atributos de API de habilitación de memoria externa para Cortex-M33 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-429">Attributes for external memory enable API for Cortex-M33 using AC6</span></span>

| <span data-ttu-id="f9eb4-430">Parámetro de atributo</span><span class="sxs-lookup"><span data-stu-id="f9eb4-430">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="f9eb4-431">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-431">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="f9eb4-432">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-432">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="f9eb4-433">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-433">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="f9eb4-434">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-434">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="f9eb4-435">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="f9eb4-435">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

### <a name="cortex-m33-using-gnu"></a><span data-ttu-id="f9eb4-436">Cortex-M33 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-436">Cortex-M33 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m33-using-gnu"></a><span data-ttu-id="f9eb4-437">Preámbulo de módulo para Cortex-M33 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-437">Module preamble for Cortex-M33 using GNU</span></span>

#### <a name="module-properties-for-cortex-m33-using-gnu"></a><span data-ttu-id="f9eb4-438">Propiedades de módulo para Cortex-M33 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-438">Module properties for Cortex-M33 using GNU</span></span>

| <span data-ttu-id="f9eb4-439">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-439">Bit</span></span> | <span data-ttu-id="f9eb4-440">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-440">Value</span></span> | <span data-ttu-id="f9eb4-441">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-441">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-442">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-442">0</span></span> | <span data-ttu-id="f9eb4-443">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-443">0</span></span><br /><span data-ttu-id="f9eb4-444">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-444">1</span></span> | <span data-ttu-id="f9eb4-445">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-445">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-446">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-446">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-447">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-447">1</span></span> | <span data-ttu-id="f9eb4-448">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-448">0</span></span><br /><span data-ttu-id="f9eb4-449">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-449">1</span></span> | <span data-ttu-id="f9eb4-450">Sin protección de MPU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-450">No MPU protection</span></span><br /><span data-ttu-id="f9eb4-451">Protección de MPU (debe estar seleccionado el modo de usuario)</span><span class="sxs-lookup"><span data-stu-id="f9eb4-451">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f9eb4-452">2</span><span class="sxs-lookup"><span data-stu-id="f9eb4-452">2</span></span> | <span data-ttu-id="f9eb4-453">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-453">0</span></span><br /><span data-ttu-id="f9eb4-454">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-454">1</span></span> | <span data-ttu-id="f9eb4-455">Deshabilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-455">Disable shared/external memory access</span></span><br /><span data-ttu-id="f9eb4-456">Habilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-456">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f9eb4-457">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-457">[23-3]</span></span> | <span data-ttu-id="f9eb4-458">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-458">0</span></span> | <span data-ttu-id="f9eb4-459">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-459">Reserved</span></span>
| <span data-ttu-id="f9eb4-460">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-460">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-461">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-461">0x00</span></span><br /><span data-ttu-id="f9eb4-462">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-462">0x01</span></span><br /><span data-ttu-id="f9eb4-463">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-463">0x02</span></span> | <span data-ttu-id="f9eb4-464">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-464">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-465">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-465">IAR</span></span><br /><span data-ttu-id="f9eb4-466">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-466">ARM</span></span><br /><span data-ttu-id="f9eb4-467">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-467">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-gnu"></a><span data-ttu-id="f9eb4-468">Enlazador de módulos para Cortex-M33 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-468">Module linker for Cortex-M33 using GNU</span></span>

#### <a name="building-modules-for-cortex-m33-using-gnu"></a><span data-ttu-id="f9eb4-469">Compilación de módulos para Cortex-M33 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-469">Building Modules for Cortex-M33 using GNU</span></span>

#### <a name="thread-extension-definition-for-cortex-m33-using-gnu"></a><span data-ttu-id="f9eb4-470">Definición de extensión de subproceso para Cortex-M33 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-470">Thread extension definition for Cortex-M33 using GNU</span></span>

#### <a name="building-module-manager-for-cortex-m33-using-gnu"></a><span data-ttu-id="f9eb4-471">Compilación de administrador de módulos para Cortex-M33 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-471">Building Module Manager for Cortex-M33 using GNU</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-gnu"></a><span data-ttu-id="f9eb4-472">Atributos de API de habilitación de memoria externa para Cortex-M33 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-472">Attributes for external memory enable API for Cortex-M33 using GNU</span></span>

| <span data-ttu-id="f9eb4-473">Parámetro de atributo</span><span class="sxs-lookup"><span data-stu-id="f9eb4-473">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="f9eb4-474">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-474">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="f9eb4-475">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-475">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="f9eb4-476">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-476">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="f9eb4-477">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-477">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="f9eb4-478">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="f9eb4-478">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

### <a name="cortex-m33-using-iar"></a><span data-ttu-id="f9eb4-479">Cortex-M33 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-479">Cortex-M33 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m33-using-iar"></a><span data-ttu-id="f9eb4-480">Preámbulo de módulo para Cortex-M33 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-480">Module preamble for Cortex-M33 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external refrences.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        // Module ID
    DC32      0x6                                               // Module Major Version
    DC32      0x1                                               // Module Minor Version
    DC32      32                                                // Module Preamble Size in 32-bit words
    DC32      0x12345678                                        // Module ID (application defined)
    DC32      0x00000007                                        // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    DC32      _txm_module_thread_shell_entry - . - 0            // Module Shell Entry Point
    DC32      demo_module_start - . - 0                         // Module Start Thread Entry Point
    DC32      0                                                 // Module Stop Thread Entry Point
    DC32      1                                                 // Module Start/Stop Thread Priority
    DC32      1024                                              // Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 // Module Callback Thread Entry
    DC32      1                                                 // Module Callback Thread Priority
    DC32      1024                                              // Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      // Module Code Size
    DC32      RWPI$$Length                                      // Module Data Size
    DC32      0                                                 // Reserved 0
    DC32      0                                                 // Reserved 1
    DC32      0                                                 // Reserved 2
    DC32      0                                                 // Reserved 3
    DC32      0                                                 // Reserved 4
    DC32      0                                                 // Reserved 5
    DC32      0                                                 // Reserved 6
    DC32      0                                                 // Reserved 7
    DC32      0                                                 // Reserved 8
    DC32      0                                                 // Reserved 9
    DC32      0                                                 // Reserved 10
    DC32      0                                                 // Reserved 11
    DC32      0                                                 // Reserved 12
    DC32      0                                                 // Reserved 13
    DC32      0                                                 // Reserved 14
    DC32      0                                                 // Reserved 15

    END

```

#### <a name="module-properties-for-cortex-m33-using-iar"></a><span data-ttu-id="f9eb4-481">Propiedades de módulo para Cortex-M33 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-481">Module properties for Cortex-M33 using IAR</span></span>

| <span data-ttu-id="f9eb4-482">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-482">Bit</span></span> | <span data-ttu-id="f9eb4-483">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-483">Value</span></span> | <span data-ttu-id="f9eb4-484">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-484">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-485">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-485">0</span></span> | <span data-ttu-id="f9eb4-486">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-486">0</span></span><br /><span data-ttu-id="f9eb4-487">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-487">1</span></span> | <span data-ttu-id="f9eb4-488">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-488">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-489">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-489">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-490">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-490">1</span></span> | <span data-ttu-id="f9eb4-491">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-491">0</span></span><br /><span data-ttu-id="f9eb4-492">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-492">1</span></span> | <span data-ttu-id="f9eb4-493">Sin protección de MPU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-493">No MPU protection</span></span><br /><span data-ttu-id="f9eb4-494">Protección de MPU (debe estar seleccionado el modo de usuario)</span><span class="sxs-lookup"><span data-stu-id="f9eb4-494">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f9eb4-495">2</span><span class="sxs-lookup"><span data-stu-id="f9eb4-495">2</span></span> | <span data-ttu-id="f9eb4-496">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-496">0</span></span><br /><span data-ttu-id="f9eb4-497">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-497">1</span></span> | <span data-ttu-id="f9eb4-498">Deshabilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-498">Disable shared/external memory access</span></span><br /><span data-ttu-id="f9eb4-499">Habilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-499">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f9eb4-500">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-500">[23-3]</span></span> | <span data-ttu-id="f9eb4-501">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-501">0</span></span> | <span data-ttu-id="f9eb4-502">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-502">Reserved</span></span>
| <span data-ttu-id="f9eb4-503">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-503">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-504">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-504">0x00</span></span><br /><span data-ttu-id="f9eb4-505">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-505">0x01</span></span><br /><span data-ttu-id="f9eb4-506">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-506">0x02</span></span> | <span data-ttu-id="f9eb4-507">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-507">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-508">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-508">IAR</span></span><br /><span data-ttu-id="f9eb4-509">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-509">ARM</span></span><br /><span data-ttu-id="f9eb4-510">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-510">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-iar"></a><span data-ttu-id="f9eb4-511">Enlazador de módulos para Cortex-M33 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-511">Module linker for Cortex-M33 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__ = 0x0;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x080f0000;
define symbol __ICFEDIT_region_ROM_end__   = 0x080fffff;
define symbol __ICFEDIT_region_RAM_start__ = 0x64002800;
define symbol __ICFEDIT_region_RAM_end__   = 0x64100000;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

//define block CSTACK    with alignment = 8, size = __ICFEDIT_size_cstack__   { };
//define block SVC_STACK with alignment = 8, size = __ICFEDIT_size_svcstack__ { };
//define block IRQ_STACK with alignment = 8, size = __ICFEDIT_size_irqstack__ { };
//define block FIQ_STACK with alignment = 8, size = __ICFEDIT_size_fiqstack__ { };
//define block UND_STACK with alignment = 8, size = __ICFEDIT_size_undstack__ { };
//define block ABT_STACK with alignment = 8, size = __ICFEDIT_size_abtstack__ { };
define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

//place at address mem:__ICFEDIT_intvec_start__ { readonly section .intvec };

define movable block ROPI with alignment = 4, fixed order 
{ 
  ro object txm_module_preamble.o,
  ro, 
  ro data 
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m33-using-iar"></a><span data-ttu-id="f9eb4-512">Compilación de módulos para Cortex-M33 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-512">Building Modules for Cortex-M33 using IAR</span></span>

#### <a name="thread-extension-definition-for-cortex-m33-using-iar"></a><span data-ttu-id="f9eb4-513">Definición de extensión de subproceso para Cortex-M33 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-513">Thread extension definition for Cortex-M33 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2                   VOID    *tx_thread_module_instance_ptr;         \
                                                VOID    *tx_thread_module_entry_info_ptr;       \
                                                ULONG   tx_thread_module_current_user_mode;     \
                                                ULONG   tx_thread_module_user_mode;             \
                                                ULONG   tx_thread_module_saved_lr;              \
                                                VOID    *tx_thread_module_kernel_stack_start;   \
                                                VOID    *tx_thread_module_kernel_stack_end;     \
                                                ULONG   tx_thread_module_kernel_stack_size;     \
                                                VOID    *tx_thread_module_stack_ptr;            \
                                                VOID    *tx_thread_module_stack_start;          \
                                                VOID    *tx_thread_module_stack_end;            \
                                                ULONG   tx_thread_module_stack_size;            \
                                                VOID    *tx_thread_module_reserved;             \
                                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m33-using-iar"></a><span data-ttu-id="f9eb4-514">Compilación de administrador de módulos para Cortex-M33 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-514">Building Module Manager for Cortex-M33 using IAR</span></span>

<span data-ttu-id="f9eb4-515">Todavía no se ha proporcionado ningún área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-515">An example workspace is not yet provided.</span></span> <span data-ttu-id="f9eb4-516">Próximamente.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-516">Coming soon.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-iar"></a><span data-ttu-id="f9eb4-517">Atributos de API de habilitación de memoria externa para Cortex-M33 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-517">Attributes for external memory enable API for Cortex-M33 using IAR</span></span>

| <span data-ttu-id="f9eb4-518">Parámetro de atributo</span><span class="sxs-lookup"><span data-stu-id="f9eb4-518">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="f9eb4-519">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-519">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="f9eb4-520">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-520">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="f9eb4-521">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-521">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="f9eb4-522">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-522">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="f9eb4-523">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="f9eb4-523">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

## <a name="cortex-m4-processor"></a><span data-ttu-id="f9eb4-524">Procesador Cortex-M4</span><span class="sxs-lookup"><span data-stu-id="f9eb4-524">Cortex-M4 processor</span></span>

### <a name="cortex-m4-using-ac5"></a><span data-ttu-id="f9eb4-525">Cortex-M4 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-525">Cortex-M4 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m4-using-ac5"></a><span data-ttu-id="f9eb4-526">Preámbulo de módulo para Cortex-M4 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-526">Module preamble for Cortex-M4 using AC5</span></span>

```armasm
    AREA Init, CODE, READONLY

    PRESERVE8

    /* Define public symbols.  */

    EXPORT __txm_module_preamble

    ; Define application-specific start/stop entry points for the module

    EXTERN demo_module_start

    /* Define common external references.  */

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|
    IMPORT  |Image$$ER_RW$$RW$$Length|
    IMPORT  |Image$$ER_RW$$ZI$$Length|
    IMPORT  |Image$$ER_ZI$$ZI$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                          // Module ID
    DCD     0x6                                                 // Module Major Version
    DCD     0x1                                                 // Module Minor Version
    DCD     32                                                  // Module Preamble Size in 32-bit words
    DCD     0x12345678                                          // Module ID (application defined)
    DCD     0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    DCD     _txm_module_thread_shell_entry - __txm_module_preamble              // Module Shell Entry Point
    DCD     demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    DCD     0                                                   // Module Stop Thread Entry Point
    DCD     1                                                   // Module Start/Stop Thread Priority
    DCD     1024                                                // Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - __txm_module_preamble   // Module Callback Thread Entry
    DCD     1                                                   // Module Callback Thread Priority
    DCD     1024                                                // Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|     // Module Code Size
    DCD     |Image$$ER_RW$$Length| + |Image$$ER_ZI$$ZI$$Length| // Module Data Size
    DCD     0                                                   // Reserved 0
    DCD     0                                                   // Reserved 1
    DCD     0                                                   // Reserved 2
    DCD     0                                                   // Reserved 3
    DCD     0                                                   // Reserved 4
    DCD     0                                                   // Reserved 5
    DCD     0                                                   // Reserved 6
    DCD     0                                                   // Reserved 7
    DCD     0                                                   // Reserved 8
    DCD     0                                                   // Reserved 9
    DCD     0                                                   // Reserved 10
    DCD     0                                                   // Reserved 11
    DCD     0                                                   // Reserved 12
    DCD     0                                                   // Reserved 13
    DCD     0                                                   // Reserved 14
    DCD     0                                                   // Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m4-using-ac5"></a><span data-ttu-id="f9eb4-527">Propiedades de módulo para Cortex-M4 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-527">Module properties for Cortex-M4 using AC5</span></span>

| <span data-ttu-id="f9eb4-528">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-528">Bit</span></span> | <span data-ttu-id="f9eb4-529">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-529">Value</span></span> | <span data-ttu-id="f9eb4-530">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-530">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-531">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-531">0</span></span> | <span data-ttu-id="f9eb4-532">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-532">0</span></span><br /><span data-ttu-id="f9eb4-533">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-533">1</span></span> | <span data-ttu-id="f9eb4-534">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-534">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-535">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-535">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-536">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-536">1</span></span> | <span data-ttu-id="f9eb4-537">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-537">0</span></span><br /><span data-ttu-id="f9eb4-538">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-538">1</span></span> | <span data-ttu-id="f9eb4-539">Sin protección de MPU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-539">No MPU protection</span></span><br /><span data-ttu-id="f9eb4-540">Protección de MPU (debe estar seleccionado el modo de usuario)</span><span class="sxs-lookup"><span data-stu-id="f9eb4-540">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f9eb4-541">2</span><span class="sxs-lookup"><span data-stu-id="f9eb4-541">2</span></span> | <span data-ttu-id="f9eb4-542">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-542">0</span></span><br /><span data-ttu-id="f9eb4-543">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-543">1</span></span> | <span data-ttu-id="f9eb4-544">Deshabilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-544">Disable shared/external memory access</span></span><br /><span data-ttu-id="f9eb4-545">Habilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-545">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f9eb4-546">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-546">[23-3]</span></span> | <span data-ttu-id="f9eb4-547">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-547">0</span></span> | <span data-ttu-id="f9eb4-548">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-548">Reserved</span></span>
| <span data-ttu-id="f9eb4-549">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-549">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-550">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-550">0x00</span></span><br /><span data-ttu-id="f9eb4-551">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-551">0x01</span></span><br /><span data-ttu-id="f9eb4-552">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-552">0x02</span></span> | <span data-ttu-id="f9eb4-553">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-553">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-554">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-554">IAR</span></span><br /><span data-ttu-id="f9eb4-555">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-555">ARM</span></span><br /><span data-ttu-id="f9eb4-556">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-556">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-ac5"></a><span data-ttu-id="f9eb4-557">Enlazador de módulos para Cortex-M4 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-557">Module linker for Cortex-M4 using AC5</span></span>

<span data-ttu-id="f9eb4-558">No se proporciona ningún archivo de enlazador de ejemplo; el enlace se realiza en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-558">No example linker file is provided; linking is done on the command line.</span></span> <span data-ttu-id="f9eb4-559">Consulte la siguiente sección.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-559">See next section.</span></span>

#### <a name="building-modules-for-cortex-m4-using-ac5"></a><span data-ttu-id="f9eb4-560">Compilación de módulos para Cortex-M4 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-560">Building Modules for Cortex-M4 using AC5</span></span>

<span data-ttu-id="f9eb4-561">Consulte el archivo build_threadx_module_demo.bat de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-561">See example build_threadx_module_demo.bat:</span></span>

```dos
armasm -g --cpreproc --cpu=cortex-m4 --fpu=vfpv4 --apcs=/interwork/ropi/rwpi txm_module_preamble.S
armcc  -g --cpu=cortex-m4 --fpu=vfpv4 -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro=0x30000 --rw=0x40000 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m4-using-ac5"></a><span data-ttu-id="f9eb4-562">Definición de extensión de subproceso para Cortex-M4 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-562">Thread extension definition for Cortex-M4 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m4-using-ac5"></a><span data-ttu-id="f9eb4-563">Compilación de administrador de módulos para Cortex-M4 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-563">Building Module Manager for Cortex-M4 using AC5</span></span>

<span data-ttu-id="f9eb4-564">Consulte el archivo build_threadx_module_manager_demo.bat de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-564">See example build_threadx_module_manager_demo.bat:</span></span>

```dos
armasm -g --cpreproc --cpu=cortex-m4 --fpu=vfpv4 --apcs=/interwork tx_initialize_low_level.S
armcc -g --cpu=cortex-m4 --fpu=vfpv4 -c -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module_manager.c
armlink -d -o sample_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list sample_threadx_module_manager.map tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-ac5"></a><span data-ttu-id="f9eb4-565">Atributos de API de habilitación de memoria externa para Cortex-M4 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-565">Attributes for external memory enable API for Cortex-M4 using AC5</span></span>

<span data-ttu-id="f9eb4-566">El módulo siempre tiene acceso de lectura a la memoria compartida.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-566">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="f9eb4-567">Parámetro de atributo</span><span class="sxs-lookup"><span data-stu-id="f9eb4-567">Attribute parameter</span></span> | <span data-ttu-id="f9eb4-568">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-568">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f9eb4-569">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-569">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f9eb4-570">Acceso de escritura</span><span class="sxs-lookup"><span data-stu-id="f9eb4-570">Write access</span></span> |

### <a name="cortex-m4-using-ac6"></a><span data-ttu-id="f9eb4-571">Cortex-M4 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-571">Cortex-M4 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m4-using-ac6"></a><span data-ttu-id="f9eb4-572">Preámbulo de módulo para Cortex-M4 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-572">Module preamble for Cortex-M4 using AC6</span></span>

```armasm
    .text
    .align 4
    .syntax unified
    .section Init
    
    // Define public symbols
    .global __txm_module_preamble

    // Define application-specific start/stop entry points for the module
    .global demo_module_start

    // Define common external references
    .global  _txm_module_thread_shell_entry
    .global  _txm_module_callback_request_thread_entry

    .eabi_attribute Tag_ABI_PCS_RO_data, 1
    .eabi_attribute Tag_ABI_PCS_R9_use,  1
    .eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
    .dc.l   0x4D4F4455                                          // Module ID
    .dc.l   0x6                                                 // Module Major Version
    .dc.l   0x1                                                 // Module Minor Version
    .dc.l   32                                                  // Module Preamble Size in 32-bit words
    .dc.l   0x12345678                                          // Module ID (application defined)
    .dc.l   0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    .dc.l   _txm_module_thread_shell_entry - __txm_module_preamble // Module Shell Entry Point
    .dc.l   demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    .dc.l   0                                                   // Module Stop Thread Entry Point
    .dc.l   1                                                   // Module Start/Stop Thread Priority
    .dc.l   1024                                                // Module Start/Stop Thread Stack Size
    .dc.l   _txm_module_callback_request_thread_entry - __txm_module_preamble // Module Callback Thread Entry
    .dc.l   1                                                   // Module Callback Thread Priority
    .dc.l   1024                                                // Module Callback Thread Stack Size
    .dc.l   0x10000                                             // Module Code Size
    .dc.l   0x10000                                             // Module Data Size
    .dc.l   0                                                   // Reserved 0
    .dc.l   0                                                   // Reserved 1
    .dc.l   0                                                   // Reserved 2
    .dc.l   0                                                   // Reserved 3
    .dc.l   0                                                   // Reserved 4
    .dc.l   0                                                   // Reserved 5
    .dc.l   0                                                   // Reserved 6
    .dc.l   0                                                   // Reserved 7
    .dc.l   0                                                   // Reserved 8
    .dc.l   0                                                   // Reserved 9
    .dc.l   0                                                   // Reserved 10
    .dc.l   0                                                   // Reserved 11
    .dc.l   0                                                   // Reserved 12
    .dc.l   0                                                   // Reserved 13
    .dc.l   0                                                   // Reserved 14
    .dc.l   0                                                   // Reserved 15
```

#### <a name="module-properties-for-cortex-m4-using-ac6"></a><span data-ttu-id="f9eb4-573">Propiedades de módulo para Cortex-M4 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-573">Module properties for Cortex-M4 using AC6</span></span>

| <span data-ttu-id="f9eb4-574">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-574">Bit</span></span> | <span data-ttu-id="f9eb4-575">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-575">Value</span></span> | <span data-ttu-id="f9eb4-576">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-576">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-577">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-577">0</span></span> | <span data-ttu-id="f9eb4-578">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-578">0</span></span><br /><span data-ttu-id="f9eb4-579">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-579">1</span></span> | <span data-ttu-id="f9eb4-580">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-580">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-581">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-581">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-582">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-582">1</span></span> | <span data-ttu-id="f9eb4-583">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-583">0</span></span><br /><span data-ttu-id="f9eb4-584">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-584">1</span></span> | <span data-ttu-id="f9eb4-585">Sin protección de MPU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-585">No MPU protection</span></span><br /><span data-ttu-id="f9eb4-586">Protección de MPU (debe estar seleccionado el modo de usuario)</span><span class="sxs-lookup"><span data-stu-id="f9eb4-586">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f9eb4-587">2</span><span class="sxs-lookup"><span data-stu-id="f9eb4-587">2</span></span> | <span data-ttu-id="f9eb4-588">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-588">0</span></span><br /><span data-ttu-id="f9eb4-589">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-589">1</span></span> | <span data-ttu-id="f9eb4-590">Deshabilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-590">Disable shared/external memory access</span></span><br /><span data-ttu-id="f9eb4-591">Habilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-591">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f9eb4-592">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-592">[23-3]</span></span> | <span data-ttu-id="f9eb4-593">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-593">0</span></span> | <span data-ttu-id="f9eb4-594">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-594">Reserved</span></span>
| <span data-ttu-id="f9eb4-595">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-595">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-596">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-596">0x00</span></span><br /><span data-ttu-id="f9eb4-597">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-597">0x01</span></span><br /><span data-ttu-id="f9eb4-598">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-598">0x02</span></span> | <span data-ttu-id="f9eb4-599">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-599">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-600">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-600">IAR</span></span><br /><span data-ttu-id="f9eb4-601">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-601">ARM</span></span><br /><span data-ttu-id="f9eb4-602">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-602">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-ac6"></a><span data-ttu-id="f9eb4-603">Enlazador de módulos para Cortex-M4 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-603">Module linker for Cortex-M4 using AC6</span></span>

<span data-ttu-id="f9eb4-604">No se usa ningún archivo de enlazador.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-604">No linker file is used.</span></span> <span data-ttu-id="f9eb4-605">Consulte la configuración del proyecto.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-605">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m4-using-ac6"></a><span data-ttu-id="f9eb4-606">Compilación de módulos para Cortex-M4 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-606">Building Modules for Cortex-M4 using AC6</span></span>

<span data-ttu-id="f9eb4-607">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-607">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-608">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de muestra y el proyecto de administrador de módulos de muestra.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-608">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m4-using-ac6"></a><span data-ttu-id="f9eb4-609">Definición de extensión de subproceso para Cortex-M4 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-609">Thread extension definition for Cortex-M4 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m4-using-ac6"></a><span data-ttu-id="f9eb4-610">Compilación de administrador de módulos para Cortex-M4 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-610">Building Module Manager for Cortex-M4 using AC6</span></span>

<span data-ttu-id="f9eb4-611">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-611">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-612">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de muestra y el proyecto de administrador de módulos de muestra.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-612">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-ac6"></a><span data-ttu-id="f9eb4-613">Atributos de API de habilitación de memoria externa para Cortex-M4 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-613">Attributes for external memory enable API for Cortex-M4 using AC6</span></span>

<span data-ttu-id="f9eb4-614">El módulo siempre tiene acceso de lectura a la memoria compartida.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-614">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="f9eb4-615">Parámetro de atributo</span><span class="sxs-lookup"><span data-stu-id="f9eb4-615">Attribute parameter</span></span> | <span data-ttu-id="f9eb4-616">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-616">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f9eb4-617">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-617">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f9eb4-618">Acceso de escritura</span><span class="sxs-lookup"><span data-stu-id="f9eb4-618">Write access</span></span> |

### <a name="cortex-m4-using-gnu"></a><span data-ttu-id="f9eb4-619">Cortex-M4 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-619">Cortex-M4 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m4-using-gnu"></a><span data-ttu-id="f9eb4-620">Preámbulo de módulo para Cortex-M4 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-620">Module preamble for Cortex-M4 using GNU</span></span>

```armasm
    .text
    .align 4
    .syntax unified

    /* Define public symbols.  */
    .global __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    .global demo_module_start

    /* Define common external refrences.  */
    .global _txm_module_thread_shell_entry
    .global _txm_module_callback_request_thread_entry

__txm_module_preamble:
    .dc.l      0x4D4F4455                                       // Module ID
    .dc.l      0x6                                              // Module Major Version
    .dc.l      0x1                                              // Module Minor Version
    .dc.l      32                                               // Module Preamble Size in 32-bit words
    .dc.l      0x12345678                                       // Module ID (application defined)
    .dc.l      0x02000007                                       // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    .dc.l      _txm_module_thread_shell_entry - . - 0           // Module Shell Entry Point
    .dc.l      demo_module_start - . - 0                        // Module Start Thread Entry Point
    .dc.l      0                                                // Module Stop Thread Entry Point 
    .dc.l      1                                                // Module Start/Stop Thread Priority
    .dc.l      1024                                             // Module Start/Stop Thread Stack Size
    .dc.l      _txm_module_callback_request_thread_entry - . - 0 // Module Callback Thread Entry
    .dc.l      1                                                // Module Callback Thread Priority
    .dc.l      1024                                             // Module Callback Thread Stack Size
    .dc.l      __code_size__                                    // Module Code Size
    .dc.l      __data_size__                                    // Module Data Size
    .dc.l      0                                                // Reserved 0
    .dc.l      0                                                // Reserved 1
    .dc.l      0                                                // Reserved 2
    .dc.l      0                                                // Reserved 3
    .dc.l      0                                                // Reserved 4
    .dc.l      0                                                // Reserved 5
    .dc.l      0                                                // Reserved 6
    .dc.l      0                                                // Reserved 7
    .dc.l      0                                                // Reserved 8
    .dc.l      0                                                // Reserved 9
    .dc.l      0                                                // Reserved 10
    .dc.l      0                                                // Reserved 11
    .dc.l      0                                                // Reserved 12
    .dc.l      0                                                // Reserved 13
    .dc.l      0                                                // Reserved 14
    .dc.l      0                                                // Reserved 15
```

#### <a name="module-properties-for-cortex-m4-using-gnu"></a><span data-ttu-id="f9eb4-621">Propiedades de módulo para Cortex-M4 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-621">Module properties for Cortex-M4 using GNU</span></span>

| <span data-ttu-id="f9eb4-622">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-622">Bit</span></span> | <span data-ttu-id="f9eb4-623">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-623">Value</span></span> | <span data-ttu-id="f9eb4-624">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-624">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-625">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-625">0</span></span> | <span data-ttu-id="f9eb4-626">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-626">0</span></span><br /><span data-ttu-id="f9eb4-627">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-627">1</span></span> | <span data-ttu-id="f9eb4-628">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-628">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-629">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-629">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-630">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-630">1</span></span> | <span data-ttu-id="f9eb4-631">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-631">0</span></span><br /><span data-ttu-id="f9eb4-632">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-632">1</span></span> | <span data-ttu-id="f9eb4-633">Sin protección de MPU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-633">No MPU protection</span></span><br /><span data-ttu-id="f9eb4-634">Protección de MPU (debe estar seleccionado el modo de usuario)</span><span class="sxs-lookup"><span data-stu-id="f9eb4-634">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f9eb4-635">2</span><span class="sxs-lookup"><span data-stu-id="f9eb4-635">2</span></span> | <span data-ttu-id="f9eb4-636">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-636">0</span></span><br /><span data-ttu-id="f9eb4-637">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-637">1</span></span> | <span data-ttu-id="f9eb4-638">Deshabilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-638">Disable shared/external memory access</span></span><br /><span data-ttu-id="f9eb4-639">Habilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-639">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f9eb4-640">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-640">[23-3]</span></span> | <span data-ttu-id="f9eb4-641">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-641">0</span></span> | <span data-ttu-id="f9eb4-642">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-642">Reserved</span></span>
| <span data-ttu-id="f9eb4-643">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-643">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-644">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-644">0x00</span></span><br /><span data-ttu-id="f9eb4-645">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-645">0x01</span></span><br /><span data-ttu-id="f9eb4-646">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-646">0x02</span></span> | <span data-ttu-id="f9eb4-647">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-647">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-648">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-648">IAR</span></span><br /><span data-ttu-id="f9eb4-649">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-649">ARM</span></span><br /><span data-ttu-id="f9eb4-650">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-650">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-gnu"></a><span data-ttu-id="f9eb4-651">Enlazador de módulos para Cortex-M4 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-651">Module linker for Cortex-M4 using GNU</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x00030000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x00030000;
  __FLASH_segment_end__   = 0x00040000;
  __RAM_segment_start__   = 0;
  __RAM_segment_end__     = 0x8000;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  } 
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);
 
  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-cortex-m4-using-gnu"></a><span data-ttu-id="f9eb4-652">Compilación de módulos para Cortex-M4 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-652">Building Modules for Cortex-M4 using GNU</span></span>

<span data-ttu-id="f9eb4-653">Consulte el archivo build_threadx_module_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-653">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m4 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m4-using-gnu"></a><span data-ttu-id="f9eb4-654">Definición de extensión de subproceso para Cortex-M4 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-654">Thread extension definition for Cortex-M4 using GNU</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m4-using-gnu"></a><span data-ttu-id="f9eb4-655">Compilación de administrador de módulos para Cortex-M4 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-655">Building Module Manager for Cortex-M4 using GNU</span></span>

<span data-ttu-id="f9eb4-656">Consulte el archivo build_threadx_module_manager_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-656">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb cortexm_vectors.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb cortexm_crt0.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb tx_initialize_low_level.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb -T sample_threadx.ld -ereset_handler -nostartfiles -o sample_threadx_module_manager.out -Wl,-Map=sample_threadx_module_manager.map cortexm_vectors.o cortexm_crt0.o tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-gnu"></a><span data-ttu-id="f9eb4-657">Atributos de API de habilitación de memoria externa para Cortex-M4 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-657">Attributes for external memory enable API for Cortex-M4 using GNU</span></span>

<span data-ttu-id="f9eb4-658">El módulo siempre tiene acceso de lectura a la memoria compartida.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-658">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="f9eb4-659">Parámetro de atributo</span><span class="sxs-lookup"><span data-stu-id="f9eb4-659">Attribute parameter</span></span> | <span data-ttu-id="f9eb4-660">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-660">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f9eb4-661">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-661">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f9eb4-662">Acceso de escritura</span><span class="sxs-lookup"><span data-stu-id="f9eb4-662">Write access</span></span> |

### <a name="cortex-m4-using-iar"></a><span data-ttu-id="f9eb4-663">Cortex-M4 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-663">Cortex-M4 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m4-using-iar"></a><span data-ttu-id="f9eb4-664">Preámbulo de módulo para Cortex-M4 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-664">Module preamble for Cortex-M4 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external references.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000007                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-3: Reserved
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution


    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m4-using-iar"></a><span data-ttu-id="f9eb4-665">Propiedades de módulo para Cortex-M4 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-665">Module properties for Cortex-M4 using IAR</span></span>

| <span data-ttu-id="f9eb4-666">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-666">Bit</span></span> | <span data-ttu-id="f9eb4-667">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-667">Value</span></span> | <span data-ttu-id="f9eb4-668">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-668">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-669">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-669">0</span></span> | <span data-ttu-id="f9eb4-670">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-670">0</span></span><br /><span data-ttu-id="f9eb4-671">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-671">1</span></span> | <span data-ttu-id="f9eb4-672">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-672">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-673">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-673">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-674">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-674">1</span></span> | <span data-ttu-id="f9eb4-675">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-675">0</span></span><br /><span data-ttu-id="f9eb4-676">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-676">1</span></span> | <span data-ttu-id="f9eb4-677">Sin protección de MPU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-677">No MPU protection</span></span><br /><span data-ttu-id="f9eb4-678">Protección de MPU (debe estar seleccionado el modo de usuario)</span><span class="sxs-lookup"><span data-stu-id="f9eb4-678">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f9eb4-679">2</span><span class="sxs-lookup"><span data-stu-id="f9eb4-679">2</span></span> | <span data-ttu-id="f9eb4-680">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-680">0</span></span><br /><span data-ttu-id="f9eb4-681">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-681">1</span></span> | <span data-ttu-id="f9eb4-682">Deshabilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-682">Disable shared/external memory access</span></span><br /><span data-ttu-id="f9eb4-683">Habilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-683">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f9eb4-684">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-684">[23-3]</span></span> | <span data-ttu-id="f9eb4-685">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-685">0</span></span> | <span data-ttu-id="f9eb4-686">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-686">Reserved</span></span>
| <span data-ttu-id="f9eb4-687">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-687">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-688">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-688">0x00</span></span><br /><span data-ttu-id="f9eb4-689">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-689">0x01</span></span><br /><span data-ttu-id="f9eb4-690">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-690">0x02</span></span> | <span data-ttu-id="f9eb4-691">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-691">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-692">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-692">IAR</span></span><br /><span data-ttu-id="f9eb4-693">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-693">ARM</span></span><br /><span data-ttu-id="f9eb4-694">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-694">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-iar"></a><span data-ttu-id="f9eb4-695">Enlazador de módulos para Cortex-M4 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-695">Module linker for Cortex-M4 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__ = 0x0;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x080f0000;
define symbol __ICFEDIT_region_ROM_end__   = 0x080fffff;
define symbol __ICFEDIT_region_RAM_start__ = 0x64002800;
define symbol __ICFEDIT_region_RAM_end__   = 0x64100000;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

//define block CSTACK    with alignment = 8, size = __ICFEDIT_size_cstack__   { };
//define block SVC_STACK with alignment = 8, size = __ICFEDIT_size_svcstack__ { };
//define block IRQ_STACK with alignment = 8, size = __ICFEDIT_size_irqstack__ { };
//define block FIQ_STACK with alignment = 8, size = __ICFEDIT_size_fiqstack__ { };
//define block UND_STACK with alignment = 8, size = __ICFEDIT_size_undstack__ { };
//define block ABT_STACK with alignment = 8, size = __ICFEDIT_size_abtstack__ { };
define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

//place at address mem:__ICFEDIT_intvec_start__ { readonly section .intvec };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble_stm32f4xx.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m4-using-iar"></a><span data-ttu-id="f9eb4-696">Compilación de módulos para Cortex-M4 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-696">Building Modules for Cortex-M4 using IAR</span></span>

<span data-ttu-id="f9eb4-697">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-697">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-698">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de demostración y el proyecto de administrador de módulos de demostración.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-698">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m4-using-iar"></a><span data-ttu-id="f9eb4-699">Definición de extensión de subproceso para Cortex-M4 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-699">Thread extension definition for Cortex-M4 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m4-using-iar"></a><span data-ttu-id="f9eb4-700">Compilación de administrador de módulos para Cortex-M4 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-700">Building Module Manager for Cortex-M4 using IAR</span></span>

<span data-ttu-id="f9eb4-701">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-701">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-702">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de demostración y el proyecto de administrador de módulos de demostración.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-702">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-iar"></a><span data-ttu-id="f9eb4-703">Atributos de API de habilitación de memoria externa para Cortex-M4 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-703">Attributes for external memory enable API for Cortex-M4 using IAR</span></span>

<span data-ttu-id="f9eb4-704">El módulo siempre tiene acceso de lectura a la memoria compartida.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-704">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="f9eb4-705">Parámetro de atributo</span><span class="sxs-lookup"><span data-stu-id="f9eb4-705">Attribute parameter</span></span> | <span data-ttu-id="f9eb4-706">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-706">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f9eb4-707">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-707">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f9eb4-708">Acceso de escritura</span><span class="sxs-lookup"><span data-stu-id="f9eb4-708">Write access</span></span> |

## <a name="cortex-m7-processor"></a><span data-ttu-id="f9eb4-709">Procesador Cortex-M7</span><span class="sxs-lookup"><span data-stu-id="f9eb4-709">Cortex-M7 processor</span></span>

### <a name="cortex-m7-using-ac5"></a><span data-ttu-id="f9eb4-710">Cortex-M7 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-710">Cortex-M7 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m7-using-ac5"></a><span data-ttu-id="f9eb4-711">Preámbulo de módulo para Cortex-M7 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-711">Module preamble for Cortex-M7 using AC5</span></span>

```c
    AREA Init, CODE, READONLY

    PRESERVE8

    ; Define public symbols

    EXPORT __txm_module_preamble


    ; Define application-specific start/stop entry points for the module

    EXTERN demo_module_start


    ; Define common external references

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|
    IMPORT  |Image$$ER_RW$$RW$$Length|
    IMPORT  |Image$$ER_RW$$ZI$$Length|
    IMPORT  |Image$$ER_ZI$$ZI$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                          ; Module ID
    DCD     0x5                                                 ; Module Major Version
    DCD     0x6                                                 ; Module Minor Version
    DCD     32                                                  ; Module Preamble Size in 32-bit words
    DCD     0x12345678                                          ; Module ID (application defined)
    DCD     0x01000007                                          ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected)
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
    DCD     _txm_module_thread_shell_entry - __txm_module_preamble              ; Module Shell Entry Point
    DCD     demo_module_start - __txm_module_preamble           ; Module Start Thread Entry Point
    DCD     0                                                   ; Module Stop Thread Entry Point
    DCD     1                                                   ; Module Start/Stop Thread Priority
    DCD     1024                                                ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - __txm_module_preamble   ; Module Callback Thread Entry
    DCD     1                                                   ; Module Callback Thread Priority
    DCD     1024                                                ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|         ; Module Code Size
    DCD     |Image$$ER_RW$$Length| + |Image$$ER_ZI$$ZI$$Length| ; Module Data Size
    DCD     0                                                   ; Reserved 0
    DCD     0                                                   ; Reserved 1
    DCD     0                                                   ; Reserved 2
    DCD     0                                                   ; Reserved 3
    DCD     0                                                   ; Reserved 4
    DCD     0                                                   ; Reserved 5
    DCD     0                                                   ; Reserved 6
    DCD     0                                                   ; Reserved 7
    DCD     0                                                   ; Reserved 8
    DCD     0                                                   ; Reserved 9
    DCD     0                                                   ; Reserved 10
    DCD     0                                                   ; Reserved 11
    DCD     0                                                   ; Reserved 12
    DCD     0                                                   ; Reserved 13
    DCD     0                                                   ; Reserved 14
    DCD     0                                                   ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m7-using-ac5"></a><span data-ttu-id="f9eb4-712">Propiedades de módulo para Cortex-M7 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-712">Module properties for Cortex-M7 using AC5</span></span>

| <span data-ttu-id="f9eb4-713">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-713">Bit</span></span> | <span data-ttu-id="f9eb4-714">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-714">Value</span></span> | <span data-ttu-id="f9eb4-715">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-715">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-716">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-716">0</span></span> | <span data-ttu-id="f9eb4-717">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-717">0</span></span><br /><span data-ttu-id="f9eb4-718">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-718">1</span></span> | <span data-ttu-id="f9eb4-719">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-719">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-720">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-720">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-721">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-721">1</span></span> | <span data-ttu-id="f9eb4-722">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-722">0</span></span><br /><span data-ttu-id="f9eb4-723">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-723">1</span></span> | <span data-ttu-id="f9eb4-724">Sin protección de MPU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-724">No MPU protection</span></span><br /><span data-ttu-id="f9eb4-725">Protección de MPU (debe estar seleccionado el modo de usuario)</span><span class="sxs-lookup"><span data-stu-id="f9eb4-725">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f9eb4-726">2</span><span class="sxs-lookup"><span data-stu-id="f9eb4-726">2</span></span> | <span data-ttu-id="f9eb4-727">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-727">0</span></span><br /><span data-ttu-id="f9eb4-728">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-728">1</span></span> | <span data-ttu-id="f9eb4-729">Deshabilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-729">Disable shared/external memory access</span></span><br /><span data-ttu-id="f9eb4-730">Habilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-730">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f9eb4-731">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-731">[23-3]</span></span> | <span data-ttu-id="f9eb4-732">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-732">0</span></span> | <span data-ttu-id="f9eb4-733">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-733">Reserved</span></span>
| <span data-ttu-id="f9eb4-734">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-734">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-735">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-735">0x00</span></span><br /><span data-ttu-id="f9eb4-736">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-736">0x01</span></span><br /><span data-ttu-id="f9eb4-737">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-737">0x02</span></span> | <span data-ttu-id="f9eb4-738">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-738">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-739">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-739">IAR</span></span><br /><span data-ttu-id="f9eb4-740">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-740">ARM</span></span><br /><span data-ttu-id="f9eb4-741">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-741">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-ac5"></a><span data-ttu-id="f9eb4-742">Enlazador de módulos para Cortex-M7 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-742">Module linker for Cortex-M7 using AC5</span></span>

<span data-ttu-id="f9eb4-743">Se compila en la línea de comandos; no hay ningún ejemplo de archivo de enlazador.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-743">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-m7-using-ac5"></a><span data-ttu-id="f9eb4-744">Compilación de módulos para Cortex-M7 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-744">Building Modules for Cortex-M7 using AC5</span></span>

<span data-ttu-id="f9eb4-745">Ejemplo sencillo de línea de comandos para compilar un módulo de Cortex-M7 con AC5:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-745">A simple command-line example for building a Cortex-M7 module using AC5:</span></span>

```dos
armasm -g --cpu=cortex-m7 --fpu=softvfp --apcs=/interwork/ropi/rwpi txm_module_preamble.s
armcc  -g --cpu=cortex-m7 --fpu=softvfp -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m7-using-ac5"></a><span data-ttu-id="f9eb4-746">Definición de extensión de subproceso para Cortex-M7 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-746">Thread extension definition for Cortex-M7 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m7-using-ac5"></a><span data-ttu-id="f9eb4-747">Compilación de administrador de módulos para Cortex-M7 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-747">Building Module Manager for Cortex-M7 using AC5</span></span>

<span data-ttu-id="f9eb4-748">Ejemplo sencillo de línea de comandos para compilar un administrador de módulos de Cortex-M7 con AC5:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-748">A simple command-line example for building a Cortex-M7 module manager using AC5:</span></span>

```dos
armasm -g --cpu=cortex-m7 --fpu=softvfp --apcs=interwork tx_initialize_low_level.s
armcc -g --cpu=cortex-m7 --fpu=softvfp -c demo_threadx_module_manager.c
armcc -g --cpu=cortex-m7 --fpu=softvfp -c module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-ac5"></a><span data-ttu-id="f9eb4-749">Atributos de API de habilitación de memoria externa para Cortex-M7 con AC5</span><span class="sxs-lookup"><span data-stu-id="f9eb4-749">Attributes for external memory enable API for Cortex-M7 using AC5</span></span>

### <a name="cortex-m7-using-ac6"></a><span data-ttu-id="f9eb4-750">Cortex-M7 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-750">Cortex-M7 using AC6</span></span>

#### <a name="module-properties-for-cortex-m7-using-ac6"></a><span data-ttu-id="f9eb4-751">Propiedades de módulo para Cortex-M7 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-751">Module properties for Cortex-M7 using AC6</span></span>

| <span data-ttu-id="f9eb4-752">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-752">Bit</span></span> | <span data-ttu-id="f9eb4-753">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-753">Value</span></span> | <span data-ttu-id="f9eb4-754">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-754">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-755">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-755">0</span></span> | <span data-ttu-id="f9eb4-756">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-756">0</span></span><br /><span data-ttu-id="f9eb4-757">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-757">1</span></span> | <span data-ttu-id="f9eb4-758">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-758">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-759">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-759">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-760">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-760">1</span></span> | <span data-ttu-id="f9eb4-761">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-761">0</span></span><br /><span data-ttu-id="f9eb4-762">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-762">1</span></span> | <span data-ttu-id="f9eb4-763">Sin protección de MPU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-763">No MPU protection</span></span><br /><span data-ttu-id="f9eb4-764">Protección de MPU (debe estar seleccionado el modo de usuario)</span><span class="sxs-lookup"><span data-stu-id="f9eb4-764">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f9eb4-765">2</span><span class="sxs-lookup"><span data-stu-id="f9eb4-765">2</span></span> | <span data-ttu-id="f9eb4-766">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-766">0</span></span><br /><span data-ttu-id="f9eb4-767">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-767">1</span></span> | <span data-ttu-id="f9eb4-768">Deshabilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-768">Disable shared/external memory access</span></span><br /><span data-ttu-id="f9eb4-769">Habilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-769">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f9eb4-770">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-770">[23-3]</span></span> | <span data-ttu-id="f9eb4-771">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-771">0</span></span> | <span data-ttu-id="f9eb4-772">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-772">Reserved</span></span>
| <span data-ttu-id="f9eb4-773">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-773">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-774">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-774">0x00</span></span><br /><span data-ttu-id="f9eb4-775">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-775">0x01</span></span><br /><span data-ttu-id="f9eb4-776">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-776">0x02</span></span> | <span data-ttu-id="f9eb4-777">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-777">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-778">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-778">IAR</span></span><br /><span data-ttu-id="f9eb4-779">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-779">ARM</span></span><br /><span data-ttu-id="f9eb4-780">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-780">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-ac6"></a><span data-ttu-id="f9eb4-781">Enlazador de módulos para Cortex-M7 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-781">Module linker for Cortex-M7 using AC6</span></span>

<span data-ttu-id="f9eb4-782">No se usa ningún archivo de enlazador.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-782">No linker file is used.</span></span> <span data-ttu-id="f9eb4-783">Consulte la configuración del proyecto.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-783">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m7-using-ac6"></a><span data-ttu-id="f9eb4-784">Compilación de módulos para Cortex-M7 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-784">Building Modules for Cortex-M7 using AC6</span></span>

<span data-ttu-id="f9eb4-785">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-785">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-786">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de muestra y el proyecto de administrador de módulos de muestra.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-786">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m7-using-ac6"></a><span data-ttu-id="f9eb4-787">Definición de extensión de subproceso para Cortex-M7 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-787">Thread extension definition for Cortex-M7 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m7-using-ac6"></a><span data-ttu-id="f9eb4-788">Compilación de administrador de módulos para Cortex-M7 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-788">Building Module Manager for Cortex-M7 using AC6</span></span>

<span data-ttu-id="f9eb4-789">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-789">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-790">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de muestra y el proyecto de administrador de módulos de muestra.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-790">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-ac6"></a><span data-ttu-id="f9eb4-791">Atributos de API de habilitación de memoria externa para Cortex-M7 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-791">Attributes for external memory enable API for Cortex-M7 using AC6</span></span>

<span data-ttu-id="f9eb4-792">El módulo siempre tiene acceso de lectura a la memoria compartida.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-792">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="f9eb4-793">Parámetro de atributo</span><span class="sxs-lookup"><span data-stu-id="f9eb4-793">Attribute parameter</span></span> | <span data-ttu-id="f9eb4-794">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-794">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f9eb4-795">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-795">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f9eb4-796">Acceso de escritura</span><span class="sxs-lookup"><span data-stu-id="f9eb4-796">Write access</span></span> |

### <a name="cortex-m7-using-gnu"></a><span data-ttu-id="f9eb4-797">Cortex-M7 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-797">Cortex-M7 using GNU</span></span>

#### <a name="module-properties-for-cortex-m7-using-gnu"></a><span data-ttu-id="f9eb4-798">Propiedades de módulo para Cortex-M7 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-798">Module properties for Cortex-M7 using GNU</span></span>

| <span data-ttu-id="f9eb4-799">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-799">Bit</span></span> | <span data-ttu-id="f9eb4-800">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-800">Value</span></span> | <span data-ttu-id="f9eb4-801">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-801">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-802">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-802">0</span></span> | <span data-ttu-id="f9eb4-803">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-803">0</span></span><br /><span data-ttu-id="f9eb4-804">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-804">1</span></span> | <span data-ttu-id="f9eb4-805">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-805">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-806">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-806">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-807">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-807">1</span></span> | <span data-ttu-id="f9eb4-808">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-808">0</span></span><br /><span data-ttu-id="f9eb4-809">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-809">1</span></span> | <span data-ttu-id="f9eb4-810">Sin protección de MPU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-810">No MPU protection</span></span><br /><span data-ttu-id="f9eb4-811">Protección de MPU (debe estar seleccionado el modo de usuario)</span><span class="sxs-lookup"><span data-stu-id="f9eb4-811">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f9eb4-812">2</span><span class="sxs-lookup"><span data-stu-id="f9eb4-812">2</span></span> | <span data-ttu-id="f9eb4-813">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-813">0</span></span><br /><span data-ttu-id="f9eb4-814">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-814">1</span></span> | <span data-ttu-id="f9eb4-815">Deshabilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-815">Disable shared/external memory access</span></span><br /><span data-ttu-id="f9eb4-816">Habilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-816">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f9eb4-817">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-817">[23-3]</span></span> | <span data-ttu-id="f9eb4-818">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-818">0</span></span> | <span data-ttu-id="f9eb4-819">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-819">Reserved</span></span>
| <span data-ttu-id="f9eb4-820">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-820">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-821">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-821">0x00</span></span><br /><span data-ttu-id="f9eb4-822">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-822">0x01</span></span><br /><span data-ttu-id="f9eb4-823">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-823">0x02</span></span> | <span data-ttu-id="f9eb4-824">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-824">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-825">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-825">IAR</span></span><br /><span data-ttu-id="f9eb4-826">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-826">ARM</span></span><br /><span data-ttu-id="f9eb4-827">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-827">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-gnu"></a><span data-ttu-id="f9eb4-828">Enlazador de módulos para Cortex-M7 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-828">Module linker for Cortex-M7 using GNU</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x00030000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x00030000;
  __FLASH_segment_end__   = 0x00040000;
  __RAM_segment_start__   = 0;
  __RAM_segment_end__     = 0x8000;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  } 
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);
 
  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-cortex-m7-using-gnu"></a><span data-ttu-id="f9eb4-829">Compilación de módulos para Cortex-M7 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-829">Building Modules for Cortex-M7 using GNU</span></span>

<span data-ttu-id="f9eb4-830">Consulte el archivo build_threadx_module_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-830">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m7 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m7-using-gnu"></a><span data-ttu-id="f9eb4-831">Definición de extensión de subproceso para Cortex-M7 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-831">Thread extension definition for Cortex-M7 using GNU</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m7-using-gnu"></a><span data-ttu-id="f9eb4-832">Compilación de administrador de módulos para Cortex-M7 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-832">Building Module Manager for Cortex-M7 using GNU</span></span>

<span data-ttu-id="f9eb4-833">Consulte el archivo build_threadx_module_manager_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-833">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb tx_simulator_startup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb cortexm_crt0.S
arm-none-eabi-gcc -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb -nostartfiles -ereset_handler -T sample_threadx.ld tx_simulator_startup.o cortexm_crt0.o sample_threadx_module_manager.o tx.a -o sample_threadx_module_manager.axf -Wl,-Map=sample_threadx_module_manager.map
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-gnu"></a><span data-ttu-id="f9eb4-834">Atributos de API de habilitación de memoria externa para Cortex-M7 con GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-834">Attributes for external memory enable API for Cortex-M7 using GNU</span></span>

<span data-ttu-id="f9eb4-835">El módulo siempre tiene acceso de lectura a la memoria compartida.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-835">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="f9eb4-836">Parámetro de atributo</span><span class="sxs-lookup"><span data-stu-id="f9eb4-836">Attribute parameter</span></span> | <span data-ttu-id="f9eb4-837">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-837">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f9eb4-838">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-838">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f9eb4-839">Acceso de escritura</span><span class="sxs-lookup"><span data-stu-id="f9eb4-839">Write access</span></span> |

### <a name="cortex-m7-using-iar"></a><span data-ttu-id="f9eb4-840">Cortex-M7 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-840">Cortex-M7 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m7-using-iar"></a><span data-ttu-id="f9eb4-841">Preámbulo de módulo para Cortex-M7 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-841">Module preamble for Cortex-M7 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external references.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000007                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-3: Reserved
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution


    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m7-using-iar"></a><span data-ttu-id="f9eb4-842">Propiedades de módulo para Cortex-M7 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-842">Module properties for Cortex-M7 using IAR</span></span>

| <span data-ttu-id="f9eb4-843">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-843">Bit</span></span> | <span data-ttu-id="f9eb4-844">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-844">Value</span></span> | <span data-ttu-id="f9eb4-845">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-845">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-846">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-846">0</span></span> | <span data-ttu-id="f9eb4-847">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-847">0</span></span><br /><span data-ttu-id="f9eb4-848">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-848">1</span></span> | <span data-ttu-id="f9eb4-849">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-849">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-850">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-850">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-851">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-851">1</span></span> | <span data-ttu-id="f9eb4-852">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-852">0</span></span><br /><span data-ttu-id="f9eb4-853">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-853">1</span></span> | <span data-ttu-id="f9eb4-854">Sin protección de MPU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-854">No MPU protection</span></span><br /><span data-ttu-id="f9eb4-855">Protección de MPU (debe estar seleccionado el modo de usuario)</span><span class="sxs-lookup"><span data-stu-id="f9eb4-855">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f9eb4-856">2</span><span class="sxs-lookup"><span data-stu-id="f9eb4-856">2</span></span> | <span data-ttu-id="f9eb4-857">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-857">0</span></span><br /><span data-ttu-id="f9eb4-858">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-858">1</span></span> | <span data-ttu-id="f9eb4-859">Deshabilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-859">Disable shared/external memory access</span></span><br /><span data-ttu-id="f9eb4-860">Habilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-860">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f9eb4-861">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-861">[23-3]</span></span> | <span data-ttu-id="f9eb4-862">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-862">0</span></span> | <span data-ttu-id="f9eb4-863">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-863">Reserved</span></span>
| <span data-ttu-id="f9eb4-864">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-864">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-865">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-865">0x00</span></span><br /><span data-ttu-id="f9eb4-866">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-866">0x01</span></span><br /><span data-ttu-id="f9eb4-867">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-867">0x02</span></span> | <span data-ttu-id="f9eb4-868">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-868">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-869">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-869">IAR</span></span><br /><span data-ttu-id="f9eb4-870">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-870">ARM</span></span><br /><span data-ttu-id="f9eb4-871">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-871">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-iar"></a><span data-ttu-id="f9eb4-872">Enlazador de módulos para Cortex-M7 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-872">Module linker for Cortex-M7 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\cortex_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__     = 0x00400000;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_RAM_start__ = 0x20450000;
define symbol __ICFEDIT_region_RAM_end__   = 0x2045f000 -1;
define symbol __ICFEDIT_region_RAM_NOCACHE_start__ = 0x2045f000;
define symbol __ICFEDIT_region_RAM_NOCACHE_end__   = 0x20460000 -1;
define symbol __ICFEDIT_region_ROM_start__ = 0x00500000;
define symbol __ICFEDIT_region_ROM_end__   = 0x00600000 -1;
define symbol __ICFEDIT_region_SDRAM_start__ = 0x70000000;
define symbol __ICFEDIT_region_SDRAM_end__   = 0x70200000 -1;

/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__      = 0x2000;
define symbol __ICFEDIT_size_heap__        = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region RAM_region    = mem:[from __ICFEDIT_region_RAM_start__ to __ICFEDIT_region_RAM_end__];
define region RAM_NOCACHE_region = mem:[from __ICFEDIT_region_RAM_NOCACHE_start__ to __ICFEDIT_region_RAM_NOCACHE_end__];
define region ROM_region    = mem:[from __ICFEDIT_region_ROM_start__ to __ICFEDIT_region_ROM_end__];
define region SDRAM_region  = mem:[from __ICFEDIT_region_SDRAM_start__ to __ICFEDIT_region_SDRAM_end__];

define block HEAP   with alignment = 8, size = __ICFEDIT_size_heap__   { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m7-using-iar"></a><span data-ttu-id="f9eb4-873">Compilación de módulos para Cortex-M7 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-873">Building Modules for Cortex-M7 using IAR</span></span>

<span data-ttu-id="f9eb4-874">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-874">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-875">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de demostración y el proyecto de administrador de módulos de demostración.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-875">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m7-using-iar"></a><span data-ttu-id="f9eb4-876">Definición de extensión de subproceso para Cortex-M7 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-876">Thread extension definition for Cortex-M7 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m7-using-iar"></a><span data-ttu-id="f9eb4-877">Compilación de administrador de módulos para Cortex-M7 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-877">Building Module Manager for Cortex-M7 using IAR</span></span>

<span data-ttu-id="f9eb4-878">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-878">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-879">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de demostración y el proyecto de administrador de módulos de demostración.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-879">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-iar"></a><span data-ttu-id="f9eb4-880">Atributos de API de habilitación de memoria externa para Cortex-M7 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-880">Attributes for external memory enable API for Cortex-M7 using IAR</span></span>

<span data-ttu-id="f9eb4-881">El módulo siempre tiene acceso de lectura a la memoria compartida.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-881">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="f9eb4-882">Parámetro de atributo</span><span class="sxs-lookup"><span data-stu-id="f9eb4-882">Attribute parameter</span></span> | <span data-ttu-id="f9eb4-883">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-883">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f9eb4-884">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-884">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f9eb4-885">Acceso de escritura</span><span class="sxs-lookup"><span data-stu-id="f9eb4-885">Write access</span></span> |

## <a name="cortex-r4-processor"></a><span data-ttu-id="f9eb4-886">Procesador Cortex-R4</span><span class="sxs-lookup"><span data-stu-id="f9eb4-886">Cortex-R4 processor</span></span>

### <a name="cortex-r4-using-ac6"></a><span data-ttu-id="f9eb4-887">Cortex-R4 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-887">Cortex-R4 using AC6</span></span>

#### <a name="module-preamble-for-cortex-r4-using-ac6"></a><span data-ttu-id="f9eb4-888">Preámbulo de módulo para Cortex-R4 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-888">Module preamble for Cortex-R4 using AC6</span></span>

```c
    .text

/* Define common external references.  */

.global     _txm_module_thread_shell_entry
.global     demo_module_start
.global     _txm_module_callback_request_thread_entry
.global     Image$$ER_RO$$Length
.global     Image$$ER_RW$$Length
.global     Image$$ER_ZI$$ZI$$Length

/* Stack aligned, ROPI and RWPI, R9 used as data offset register.  */
.eabi_attribute Tag_ABI_align_preserved, 1
.eabi_attribute Tag_ABI_PCS_RO_data, 1
.eabi_attribute Tag_ABI_PCS_R9_use,  1
.eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
.word   0x4D4F4455                                          /* Module ID  */
.word   0x5                                                 /* Module Major Version  */
.word   0x3                                                 /* Module Minor Version  */
.word   32                                                  /* Module Preamble Size in 32-bit words  */
.word   0x12345678                                          /* Module ID (application defined)  */
.word   0x01000001                                          /* Module Properties where:
                                                               Bits 31-24: Compiler ID
                                                                       0 -> IAR
                                                                       1 -> RVDS/ARM
                                                                       2 -> GNU
                                                               Bits 23-1:  Reserved
                                                               Bit 0:  0 -> Privileged mode execution (no MMU protection)
                                                                       1 -> User mode execution (MMU protection)  */
.word   _txm_module_thread_shell_entry - __txm_module_preamble  /* Module Shell Entry Point  */
.word   demo_module_start - __txm_module_preamble           /* Module Start Thread Entry Point  */
.word   0                                                   /* Module Stop Thread Entry Point   */
.word   1                                                   /* Module Start/Stop Thread Priority  */
.word   1024                                                /* Module Start/Stop Thread Stack Size  */
.word   _txm_module_callback_request_thread_entry - __txm_module_preamble   /* Module Callback Thread Entry  */
.word   1                                                   /* Module Callback Thread Priority  */
.word   1024                                                /* Module Callback Thread Stack Size  */
.word   9000                                                /* Module Code Size */
.word   11000                                               /* Module Data Size */
.word   0                                                   /* Reserved 0  */
.word   0                                                   /* Reserved 1  */
.word   0                                                   /* Reserved 2  */
.word   0                                                   /* Reserved 3  */
.word   0                                                   /* Reserved 4  */
.word   0                                                   /* Reserved 5  */
.word   0                                                   /* Reserved 6  */
.word   0                                                   /* Reserved 7  */
.word   0                                                   /* Reserved 8  */
.word   0                                                   /* Reserved 9  */
.word   0                                                   /* Reserved 10  */
.word   0                                                   /* Reserved 11  */
.word   0                                                   /* Reserved 12  */
.word   0                                                   /* Reserved 13  */
.word   0                                                   /* Reserved 14  */
.word   0                                                   /* Reserved 15  */
```

#### <a name="module-properties-for-cortex-r4-using-ac6"></a><span data-ttu-id="f9eb4-889">Propiedades de módulo para Cortex-R4 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-889">Module properties for Cortex-R4 using AC6</span></span>

| <span data-ttu-id="f9eb4-890">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-890">Bit</span></span> | <span data-ttu-id="f9eb4-891">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-891">Value</span></span> | <span data-ttu-id="f9eb4-892">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-892">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-893">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-893">0</span></span> | <span data-ttu-id="f9eb4-894">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-894">0</span></span><br /><span data-ttu-id="f9eb4-895">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-895">1</span></span> | <span data-ttu-id="f9eb4-896">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-896">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-897">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-897">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-898">[23-1]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-898">[23-1]</span></span> | <span data-ttu-id="f9eb4-899">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-899">0</span></span> | <span data-ttu-id="f9eb4-900">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-900">Reserved</span></span>
| <span data-ttu-id="f9eb4-901">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-901">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-902">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-902">0x00</span></span><br /><span data-ttu-id="f9eb4-903">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-903">0x01</span></span><br /><span data-ttu-id="f9eb4-904">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-904">0x02</span></span> | <span data-ttu-id="f9eb4-905">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-905">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-906">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-906">IAR</span></span><br /><span data-ttu-id="f9eb4-907">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-907">ARM</span></span><br /><span data-ttu-id="f9eb4-908">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-908">GNU</span></span> |

#### <a name="module-linker-for-cortex-r4-using-ac6"></a><span data-ttu-id="f9eb4-909">Enlazador de módulos para Cortex-R4 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-909">Module linker for Cortex-R4 using AC6</span></span>

<span data-ttu-id="f9eb4-910">Se compila en la línea de comandos; no hay ningún ejemplo de archivo de enlazador.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-910">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-r4-using-ac6"></a><span data-ttu-id="f9eb4-911">Compilación de módulos para Cortex-R4 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-911">Building Modules for Cortex-R4 using AC6</span></span>

<span data-ttu-id="f9eb4-912">Ejemplo sencillo de línea de comandos para compilar un módulo de Cortex-R4 con AC6:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-912">A simple command-line example for building a Cortex-R4 module using AC6:</span></span>

```dos
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 demo_threadx_module.c
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 txm_module_preamble.S
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 semihosting.c
armlink -d -o demo_threadx_module.axf --elf --ro 0x00100000 --first txm_module_preamble.o --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --datacompressor=off --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o semihosting.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-r4-using-ac6"></a><span data-ttu-id="f9eb4-913">Definición de extensión de subproceso para Cortex-R4 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-913">Thread extension definition for Cortex-R4 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2   ULONG   tx_thread_vfp_enable;                   \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-r4-using-ac6"></a><span data-ttu-id="f9eb4-914">Compilación de administrador de módulos para Cortex-R4 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-914">Building Module Manager for Cortex-R4 using AC6</span></span>

<span data-ttu-id="f9eb4-915">Ejemplo sencillo de línea de comandos para compilar un administrador de módulos de Cortex-R4 con AC6:</span><span class="sxs-lookup"><span data-stu-id="f9eb4-915">A simple command-line example for building a Cortex-R4 module manager using AC6:</span></span>

```dos
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 demo_threadx_module_manager.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 timer.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 gic.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 tx_initialize_low_level.S
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 startup.S
armlink -d -o demo_threadx_module_manager.axf --elf --scatter=demo_threadx.scat --remove --map --symbols --list demo_threadx_module_manager.map startup.o timer.o gic.o demo_threadx_module_manager.o tx_initialize_low_level.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-r4-using-ac6"></a><span data-ttu-id="f9eb4-916">Atributos de API de habilitación de memoria externa para Cortex-R4 con AC6</span><span class="sxs-lookup"><span data-stu-id="f9eb4-916">Attributes for external memory enable API for Cortex-R4 using AC6</span></span>

<span data-ttu-id="f9eb4-917">El módulo siempre tiene acceso de lectura a la memoria compartida.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-917">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="f9eb4-918">Parámetro de atributo</span><span class="sxs-lookup"><span data-stu-id="f9eb4-918">Attribute parameter</span></span> | <span data-ttu-id="f9eb4-919">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-919">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f9eb4-920">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-920">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f9eb4-921">Acceso de escritura</span><span class="sxs-lookup"><span data-stu-id="f9eb4-921">Write access</span></span> |

### <a name="cortex-r4-using-iar"></a><span data-ttu-id="f9eb4-922">Cortex-R4 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-922">Cortex-R4 using IAR</span></span>

#### <a name="module-preamble-for-cortex-r4-using-iar"></a><span data-ttu-id="f9eb4-923">Preámbulo de módulo para Cortex-R4 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-923">Module preamble for Cortex-R4 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */
    PUBLIC __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    EXTERN demo_module_start

    /* Define common external references.  */
    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000001                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-1: Reserved
                                                                ;   Bit 0:  0 -> Privileged mode execution (no MPU protection)
                                                                ;           1 -> User mode execution (MPU protection)
    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-r4-using-iar"></a><span data-ttu-id="f9eb4-924">Propiedades de módulo para Cortex-R4 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-924">Module properties for Cortex-R4 using IAR</span></span>

| <span data-ttu-id="f9eb4-925">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-925">Bit</span></span> | <span data-ttu-id="f9eb4-926">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-926">Value</span></span> | <span data-ttu-id="f9eb4-927">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-927">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-928">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-928">0</span></span> | <span data-ttu-id="f9eb4-929">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-929">0</span></span><br /><span data-ttu-id="f9eb4-930">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-930">1</span></span> | <span data-ttu-id="f9eb4-931">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-931">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-932">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-932">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-933">[23-1]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-933">[23-1]</span></span> | <span data-ttu-id="f9eb4-934">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-934">0</span></span> | <span data-ttu-id="f9eb4-935">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-935">Reserved</span></span>
| <span data-ttu-id="f9eb4-936">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-936">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-937">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-937">0x00</span></span><br /><span data-ttu-id="f9eb4-938">0x01</span><span class="sxs-lookup"><span data-stu-id="f9eb4-938">0x01</span></span><br /><span data-ttu-id="f9eb4-939">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-939">0x02</span></span> | <span data-ttu-id="f9eb4-940">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-940">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-941">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-941">IAR</span></span><br /><span data-ttu-id="f9eb4-942">ARM</span><span class="sxs-lookup"><span data-stu-id="f9eb4-942">ARM</span></span><br /><span data-ttu-id="f9eb4-943">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-943">GNU</span></span> |

#### <a name="module-linker-for-cortex-r4-using-iar"></a><span data-ttu-id="f9eb4-944">Enlazador de módulos para Cortex-R4 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-944">Module linker for Cortex-R4 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x00100000;
define symbol __ICFEDIT_region_ROM_end__   = 0x0013FFFF;
define symbol __ICFEDIT_region_RAM_start__ = 0x08000000;
define symbol __ICFEDIT_region_RAM_end__   = 0x0800FFFF;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x100;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-r4-using-iar"></a><span data-ttu-id="f9eb4-945">Compilación de módulos para Cortex-R4 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-945">Building Modules for Cortex-R4 using IAR</span></span>

<span data-ttu-id="f9eb4-946">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-946">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-947">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de demostración y el proyecto de administrador de módulos de demostración.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-947">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-r4-using-iar"></a><span data-ttu-id="f9eb4-948">Definición de extensión de subproceso para Cortex-R4 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-948">Thread extension definition for Cortex-R4 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   ULONG   tx_thread_vfp_enable;                   \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-r4-using-iar"></a><span data-ttu-id="f9eb4-949">Compilación de administrador de módulos para Cortex-R4 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-949">Building Module Manager for Cortex-R4 using IAR</span></span>

<span data-ttu-id="f9eb4-950">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-950">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-951">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de demostración y el proyecto de administrador de módulos de demostración.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-951">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-r4-using-iar"></a><span data-ttu-id="f9eb4-952">Atributos de API de habilitación de memoria externa para Cortex-R4 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-952">Attributes for external memory enable API for Cortex-R4 using IAR</span></span>

<span data-ttu-id="f9eb4-953">El módulo siempre tiene acceso de lectura a la memoria compartida.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-953">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="f9eb4-954">Parámetro de atributo</span><span class="sxs-lookup"><span data-stu-id="f9eb4-954">Attribute parameter</span></span> | <span data-ttu-id="f9eb4-955">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-955">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f9eb4-956">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-956">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f9eb4-957">Acceso de escritura</span><span class="sxs-lookup"><span data-stu-id="f9eb4-957">Write access</span></span> |

## <a name="mcf544xx-processor"></a><span data-ttu-id="f9eb4-958">Procesador MCF544xx</span><span class="sxs-lookup"><span data-stu-id="f9eb4-958">MCF544xx processor</span></span>

### <a name="mcf544xx-using-ghs"></a><span data-ttu-id="f9eb4-959">MCF544xx con GHS</span><span class="sxs-lookup"><span data-stu-id="f9eb4-959">MCF544xx using GHS</span></span>

#### <a name="module-preamble-for-mcf544xx-using-ghs"></a><span data-ttu-id="f9eb4-960">Preámbulo de módulo para MCF544xx con GHS</span><span class="sxs-lookup"><span data-stu-id="f9eb4-960">Module preamble for MCF544xx using GHS</span></span>

```c
    SECT    .preamble, x

    /* Define public symbols.  */
    XDEF __txm_module_preamble

__txm_module_preamble:
    DC.L    0x4D4F4455                                  /* Module ID                                */
    DC.L    0x5                                         /* Module Major Version                     */
    DC.L    0x3                                         /* Module Minor Version                     */
    DC.L    32                                          /* Module Preamble Size in 32-bit words     */
    DC.L    0x12345678                                  /* Module ID (application defined)          */
    DC.L    0x03000003                                  /* Module Properties where:                 */
                                                        /* Bits 31-24: Compiler ID                  */
                                                        /*           3 -> GHS                       */
                                                        /* Bits 23-2: Reserved                      */
                                                        /* Bit 1:  0 -> No MMU protection           */
                                                        /*         1 -> MMU protection (must have   */
                                                        /*              user mode selected)         */
                                                        /* Bit 0:  0 -> Supervisor mode execution   */
                                                        /*         1 -> User mode execution         */
    DC.L    _txm_module_thread_shell_entry              /* Module Shell Entry Point                 */
    DC.L    demo_module_start                           /* Module Start Thread Entry Point          */
    DC.L    0                                           /* Module Stop Thread Entry Point           */
    DC.L    1                                           /* Module Start/Stop Thread Priority        */
    DC.L    2048                                        /* Module Start/Stop Thread Stack Size      */
    DC.L    _txm_module_callback_request_thread_entry   /* Module Callback Thread Entry             */
    DC.L    1                                           /* Module Callback Thread Priority          */
    DC.L    2048                                        /* Module Callback Thread Stack Size        */
    DC.L    module_code_size                            /* Module Code Size                         */
    DC.L    module_data_size                            /* Module Data Size                         */
    DC.L    0                                           /* Reserved 0                               */
    DC.L    0                                           /* Reserved 1                               */
    DC.L    0                                           /* Reserved 2                               */
    DC.L    0                                           /* Reserved 3                               */
    DC.L    0                                           /* Reserved 4                               */
    DC.L    0                                           /* Reserved 5                               */
    DC.L    0                                           /* Reserved 6                               */
    DC.L    0                                           /* Reserved 7                               */
    DC.L    0                                           /* Reserved 8                               */
    DC.L    0                                           /* Reserved 9                               */
    DC.L    0                                           /* Reserved 10                              */
    DC.L    0                                           /* Reserved 11                              */
    DC.L    0                                           /* Reserved 12                              */
    DC.L    0                                           /* Reserved 13                              */
    DC.L    0                                           /* Reserved 14                              */
    DC.L    0                                           /* Reserved 15                              */

    END
```

#### <a name="module-properties-for-mcf544xx-using-ghs"></a><span data-ttu-id="f9eb4-961">Propiedades de módulo para MCF544xx con GHS</span><span class="sxs-lookup"><span data-stu-id="f9eb4-961">Module properties for MCF544xx using GHS</span></span>

| <span data-ttu-id="f9eb4-962">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-962">Bit</span></span> | <span data-ttu-id="f9eb4-963">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-963">Value</span></span> | <span data-ttu-id="f9eb4-964">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-964">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-965">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-965">0</span></span> | <span data-ttu-id="f9eb4-966">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-966">0</span></span><br /><span data-ttu-id="f9eb4-967">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-967">1</span></span> | <span data-ttu-id="f9eb4-968">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-968">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-969">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-969">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-970">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-970">1</span></span> | <span data-ttu-id="f9eb4-971">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-971">0</span></span><br /><span data-ttu-id="f9eb4-972">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-972">1</span></span> | <span data-ttu-id="f9eb4-973">Sin protección de MMU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-973">No MMU protection</span></span><br /><span data-ttu-id="f9eb4-974">Protección de MMU (debe estar seleccionado el modo de usuario)</span><span class="sxs-lookup"><span data-stu-id="f9eb4-974">MMU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f9eb4-975">2</span><span class="sxs-lookup"><span data-stu-id="f9eb4-975">2</span></span> | <span data-ttu-id="f9eb4-976">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-976">0</span></span><br /><span data-ttu-id="f9eb4-977">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-977">1</span></span> | <span data-ttu-id="f9eb4-978">Deshabilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-978">Disable shared/external memory access</span></span><br /><span data-ttu-id="f9eb4-979">Habilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-979">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f9eb4-980">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-980">[23-3]</span></span> | <span data-ttu-id="f9eb4-981">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-981">0</span></span> | <span data-ttu-id="f9eb4-982">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-982">Reserved</span></span>
| <span data-ttu-id="f9eb4-983">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-983">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-984">0x03</span><span class="sxs-lookup"><span data-stu-id="f9eb4-984">0x03</span></span> | <span data-ttu-id="f9eb4-985">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-985">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-986">GHS</span><span class="sxs-lookup"><span data-stu-id="f9eb4-986">GHS</span></span> |

#### <a name="module-linker-for-mcf544xx-using-ghs"></a><span data-ttu-id="f9eb4-987">Enlazador de módulos para MCF544xx con GHS</span><span class="sxs-lookup"><span data-stu-id="f9eb4-987">Module linker for MCF544xx using GHS</span></span>

```c
DEFAULTS {

    heap_reserve =  256
    stack_reserve = 256
}

//
// Program layout for PIC and PID built programs.
//

-sec
{
//
// The data segment
//
    .pidbase                0x00000000 :
    .sdabase                           :
    .sbss                   NOCLEAR    :
    .sdata                             :
    .data                   NOLOAD     :
    .bss                    NOCLEAR    :
    .heap                   ALIGN(16) PAD( heap_reserve +
        // Add space for call-graph profiling if used:
        (isdefined(__ghs_indgcount)?(2000+(sizeof(.text)/2)):0) +
        // Add estimated space for call-count profiling if used:
        (isdefined(__ghs_indmcount)?10000:0) )
                                             :
    .stack      ALIGN(16) PAD(stack_reserve) :

    module_data_size = sizeof(.pidbase) + sizeof(.sdabase) + sizeof(.sbss) + sizeof(.sdata) + sizeof(.data) + sizeof(.bss) + sizeof(.heap) + sizeof(.stack);

//
// The code segment
//

    .picbase                0x00000000 :
    .preamble                          :
    .text                              :
    .syscall                           :
    .fixaddr                           :
    .fixtype                           :
    .rodata                            :
    .ROM.data               ROM(.data) :
    .secinfo                           :

    module_code_size =  endaddr(.secinfo);
}
```

#### <a name="building-modules-for-mcf544xx-using-ghs"></a><span data-ttu-id="f9eb4-988">Compilación de módulos para MCF544xx con GHS</span><span class="sxs-lookup"><span data-stu-id="f9eb4-988">Building Modules for MCF544xx using GHS</span></span>

<span data-ttu-id="f9eb4-989">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-989">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-990">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de demostración y el proyecto de administrador de módulos de demostración.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-990">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-mcf544xx-using-ghs"></a><span data-ttu-id="f9eb4-991">Definición de extensión de subproceso para MCF544xx con GHS</span><span class="sxs-lookup"><span data-stu-id="f9eb4-991">Thread extension definition for MCF544xx using GHS</span></span>

```c
#define TX_THREAD_EXTENSION_2   int     Errno;                                  \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_mmu_protection;        \
                                VOID *  tx_thread_module_dispatch_return;       \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-mcf544xx-using-ghs"></a><span data-ttu-id="f9eb4-992">Compilación de administrador de módulos para MCF544xx con GHS</span><span class="sxs-lookup"><span data-stu-id="f9eb4-992">Building Module Manager for MCF544xx using GHS</span></span>

<span data-ttu-id="f9eb4-993">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-993">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-994">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de demostración y el proyecto de administrador de módulos de demostración.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-994">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-mcf544xx-using-ghs"></a><span data-ttu-id="f9eb4-995">Atributos de API de habilitación de memoria externa para MCF544xx con GHS</span><span class="sxs-lookup"><span data-stu-id="f9eb4-995">Attributes for external memory enable API for MCF544xx using GHS</span></span>

<span data-ttu-id="f9eb4-996">Esta característica no está habilitada en MCF544xx.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-996">This feature not enabled on MCF544xx.</span></span>

## <a name="rx63-processor"></a><span data-ttu-id="f9eb4-997">Procesador RX63</span><span class="sxs-lookup"><span data-stu-id="f9eb4-997">RX63 processor</span></span>

### <a name="rx63-using-iar"></a><span data-ttu-id="f9eb4-998">RX63 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-998">RX63 using IAR</span></span>

#### <a name="module-preamble-for-rx63-using-iar"></a><span data-ttu-id="f9eb4-999">Preámbulo de módulo para RX63 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-999">Module preamble for RX63 using IAR</span></span>

```c
    /* Alignment of 4 (16-byte) */
    SECTION .text:CODE (4)

    /* Define public symbols.  */
    PUBLIC __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    EXTERN _demo_module_start

    /* Define common external references.  */
    EXTERN  __txm_module_thread_shell_entry
    EXTERN  __txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        // Module ID
    DC32      0x5                                               // Module Major Version
    DC32      0x6                                               // Module Minor Version
    DC32      32                                                // Module Preamble Size in 32-bit words
    DC32      0x12345678                                        // Module ID (application defined)
    DC32      0x00000007                                        // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    DC32      __txm_module_thread_shell_entry - $               // Module Shell Entry Point
    DC32      _demo_module_start - $                            // Module Start Thread Entry Point
    DC32      0                                                 // Module Stop Thread Entry Point
    DC32      1                                                 // Module Start/Stop Thread Priority
    DC32      1024                                              // Module Start/Stop Thread Stack Size
    DC32      __txm_module_callback_request_thread_entry - $    // Module Callback Thread Entry
    DC32      1                                                 // Module Callback Thread Priority
    DC32      1024                                              // Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      // Module Code Size
    DC32      RWPI$$Length                                      // Module Data Size
    DC32      0                                                 // Reserved 0
    DC32      0                                                 // Reserved 1
    DC32      0                                                 // Reserved 2
    DC32      0                                                 // Reserved 3
    DC32      0                                                 // Reserved 4
    DC32      0                                                 // Reserved 5
    DC32      0                                                 // Reserved 6
    DC32      0                                                 // Reserved 7
    DC32      0                                                 // Reserved 8  
    DC32      0                                                 // Reserved 9
    DC32      0                                                 // Reserved 10
    DC32      0                                                 // Reserved 11
    DC32      0                                                 // Reserved 12
    DC32      0                                                 // Reserved 13
    DC32      0                                                 // Reserved 14
    DC32      0                                                 // Reserved 15

    END
```

#### <a name="module-properties-for-rx63-using-iar"></a><span data-ttu-id="f9eb4-1000">Propiedades de módulo para RX63 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1000">Module properties for RX63 using IAR</span></span>

| <span data-ttu-id="f9eb4-1001">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1001">Bit</span></span> | <span data-ttu-id="f9eb4-1002">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1002">Value</span></span> | <span data-ttu-id="f9eb4-1003">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1003">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-1004">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1004">0</span></span> | <span data-ttu-id="f9eb4-1005">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1005">0</span></span><br /><span data-ttu-id="f9eb4-1006">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1006">1</span></span> | <span data-ttu-id="f9eb4-1007">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1007">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-1008">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1008">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-1009">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1009">1</span></span> | <span data-ttu-id="f9eb4-1010">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1010">0</span></span><br /><span data-ttu-id="f9eb4-1011">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1011">1</span></span> | <span data-ttu-id="f9eb4-1012">Sin protección de MPU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1012">No MPU protection</span></span><br /><span data-ttu-id="f9eb4-1013">Protección de MPU (debe estar seleccionado el modo de usuario)</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1013">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f9eb4-1014">2</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1014">2</span></span> | <span data-ttu-id="f9eb4-1015">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1015">0</span></span><br /><span data-ttu-id="f9eb4-1016">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1016">1</span></span> | <span data-ttu-id="f9eb4-1017">Deshabilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1017">Disable shared/external memory access</span></span><br /><span data-ttu-id="f9eb4-1018">Habilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1018">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f9eb4-1019">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1019">[23-3]</span></span> | <span data-ttu-id="f9eb4-1020">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1020">0</span></span> | <span data-ttu-id="f9eb4-1021">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1021">Reserved</span></span>
| <span data-ttu-id="f9eb4-1022">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1022">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-1023">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1023">0x00</span></span><br /><span data-ttu-id="f9eb4-1024">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1024">0x02</span></span> | <span data-ttu-id="f9eb4-1025">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1025">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-1026">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1026">IAR</span></span><br /><span data-ttu-id="f9eb4-1027">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1027">GNU</span></span> |

#### <a name="module-linker-for-rx63-using-iar"></a><span data-ttu-id="f9eb4-1028">Enlazador de módulos para RX63 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1028">Module linker for RX63 using IAR</span></span>

```c
//-----------------------------------------------------------------------------
// ILINK command file template for the Renesas RX microcontroller R5F563NB
//-----------------------------------------------------------------------------
define exported symbol __link_file_version_4 = 1;

define memory mem with size = 4G;

// ID Code Protection
define exported symbol __ID_BYTES_1_4   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_5_8   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_9_12  = 0xFFFFFFFF;
define exported symbol __ID_BYTES_13_16 = 0xFFFFFFFF;

// Endian Select Register (MDE)
// Choose between Little endian=0xFFFFFFFF or Big endian=0xFFFFFFF8
define exported symbol __MDES           = 0xFFFFFFFF;

// Option Function Select Register 0 (OFS0)
define exported symbol __OFS0           = 0xFFFFFFFF;

// Option Function Select Register 1 (OFS1)
define exported symbol __OFS1           = 0xFFFFFFFF;

//define region ROM_region16 = mem:[from 0xFFFF8000 to 0xFFFFFFFF];
define region RAM_region16 = mem:[from 0x00010000 to 0x00017FFF];
//define region ROM_region24 = mem:[from 0xFFF00000 to 0xFFFFFFFF];
//define region RAM_region24 = mem:[from 0x00000004 to 0x0001FFFF];
define region ROM_region32 = mem:[from 0xFFF10400 to 0xFFFFFFFF];
//define region RAM_region32 = mem:[from 0x00000004 to 0x0001FFFF];
//define region DATA_FLASH_region = mem:[from 0x00100000 to 0x00107FFF];

initialize by copy { rw, ro section D, ro section D_1, ro section D_2 };
do not initialize  { section .*.noinit };

define block HEAP     with alignment = 4, size = _HEAP_SIZE { };
//define block USTACK   with alignment = 4, size = _USTACK_SIZE { };
//define block ISTACK   with alignment = 4, size = _ISTACK_SIZE { };

//define block STACKS with fixed order { block ISTACK,
//                                       block USTACK };

//place at address mem:0xFFFFFF80 { ro section .nmivec };
//"ROM16":place in ROM_region16        { ro section .code16*,
//                                       ro section .data16* };
//"RAM16":place in RAM_region16        { rw section .data16*,
//                                       rw section __DLIB_PERTHREAD };
//"ROM24":place in ROM_region24        { ro section .code24*,
//                                       ro section .data24* };
//"RAM24":place in RAM_region24        { rw section .data24* };
//"ROM32":place in ROM_region32        { ro };
//"RAM32":place in RAM_region32        { rw,
//                                       ro section D,
//                                       ro section D_1,
//                                       ro section D_2,
//                                       block HEAP,
//                                       block STACKS,
//                                       last section FREEMEM };

//"DATAFLASH":place in DATA_FLASH_region
//                                     { ro section .dataflash* };

define movable block ROPI with alignment = 4, fixed order, static base CB
{
  ro object txm_module_preamble_rx63n.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base SB
{
  rw section .sbdata*,
  rw section .sbrel*,
  rw section __DLIB_PERTHREAD,
  block HEAP
};

place in ROM_region32   { block ROPI };
place in RAM_region16   { block RWPI };
```

#### <a name="building-modules-for-rx63-using-iar"></a><span data-ttu-id="f9eb4-1029">Compilación de módulos para RX63 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1029">Building Modules for RX63 using IAR</span></span>

<span data-ttu-id="f9eb4-1030">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1030">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-1031">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de demostración y el proyecto de administrador de módulos de demostración.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1031">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-rxrx635n-using-iar"></a><span data-ttu-id="f9eb4-1032">Definición de extensión de subproceso para RXRX635N con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1032">Thread extension definition for RXRX635N using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;       \
                                VOID    *tx_thread_module_entry_info_ptr;     \
                                ULONG   tx_thread_module_current_user_mode;   \
                                ULONG   tx_thread_module_user_mode;           \
                                VOID    *tx_thread_module_kernel_stack_start; \
                                VOID    *tx_thread_module_kernel_stack_end;   \
                                ULONG   tx_thread_module_kernel_stack_size;   \
                                VOID    *tx_thread_module_stack_ptr;          \
                                VOID    *tx_thread_module_stack_start;        \
                                VOID    *tx_thread_module_stack_end;          \
                                ULONG   tx_thread_module_stack_size;          \
                                VOID    *tx_thread_module_reserved;           \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-rx63-using-iar"></a><span data-ttu-id="f9eb4-1033">Compilación de administrador de módulos para RX63 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1033">Building Module Manager for RX63 using IAR</span></span>

<span data-ttu-id="f9eb4-1034">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1034">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-1035">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de demostración y el proyecto de administrador de módulos de demostración.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1035">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-rx63-using-iar"></a><span data-ttu-id="f9eb4-1036">Atributos de API de habilitación de memoria externa para RX63 con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1036">Attributes for external memory enable API for RX63 using IAR</span></span>

| <span data-ttu-id="f9eb4-1037">Parámetro del atributo</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1037">Attribute Parameter</span></span> | <span data-ttu-id="f9eb4-1038">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1038">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f9eb4-1039">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1039">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span></span> | <span data-ttu-id="f9eb4-1040">Ejecutar código</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1040">Execute code</span></span> |
| <span data-ttu-id="f9eb4-1041">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1041">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f9eb4-1042">Acceso de escritura</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1042">Write access</span></span> |
| <span data-ttu-id="f9eb4-1043">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1043">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span></span> | <span data-ttu-id="f9eb4-1044">acceso de lectura</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1044">Read access</span></span> |

## <a name="rx65n-processor"></a><span data-ttu-id="f9eb4-1045">Procesador RX65N</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1045">RX65N processor</span></span>

### <a name="rx65n-using-iar"></a><span data-ttu-id="f9eb4-1046">RX65N con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1046">RX65N using IAR</span></span>

#### <a name="module-preamble-for-rx65n-using-iar"></a><span data-ttu-id="f9eb4-1047">Preámbulo de módulo para RX65N con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1047">Module preamble for RX65N using IAR</span></span>

```c
    /* Alignment of 4 (16-byte) */
    SECTION .text:CODE (4)

    /* Define public symbols.  */
    PUBLIC __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    EXTERN _demo_module_start

    /* Define common external references.  */
    EXTERN  __txm_module_thread_shell_entry
    EXTERN  __txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        // Module ID
    DC32      0x5                                               // Module Major Version
    DC32      0x6                                               // Module Minor Version
    DC32      32                                                // Module Preamble Size in 32-bit words
    DC32      0x12345678                                        // Module ID (application defined)
    DC32      0x00000007                                        // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    DC32      __txm_module_thread_shell_entry - $               // Module Shell Entry Point
    DC32      _demo_module_start - $                            // Module Start Thread Entry Point
    DC32      0                                                 // Module Stop Thread Entry Point
    DC32      1                                                 // Module Start/Stop Thread Priority
    DC32      1024                                              // Module Start/Stop Thread Stack Size
    DC32      __txm_module_callback_request_thread_entry - $    // Module Callback Thread Entry
    DC32      1                                                 // Module Callback Thread Priority
    DC32      1024                                              // Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      // Module Code Size
    DC32      RWPI$$Length                                      // Module Data Size
    DC32      0                                                 // Reserved 0
    DC32      0                                                 // Reserved 1
    DC32      0                                                 // Reserved 2
    DC32      0                                                 // Reserved 3
    DC32      0                                                 // Reserved 4
    DC32      0                                                 // Reserved 5
    DC32      0                                                 // Reserved 6
    DC32      0                                                 // Reserved 7
    DC32      0                                                 // Reserved 8  
    DC32      0                                                 // Reserved 9
    DC32      0                                                 // Reserved 10
    DC32      0                                                 // Reserved 11
    DC32      0                                                 // Reserved 12
    DC32      0                                                 // Reserved 13
    DC32      0                                                 // Reserved 14
    DC32      0                                                 // Reserved 15

    END
```

#### <a name="module-properties-for-rx65n-using-iar"></a><span data-ttu-id="f9eb4-1048">Propiedades de módulo para RX65N con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1048">Module properties for RX65N using IAR</span></span>

| <span data-ttu-id="f9eb4-1049">bit</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1049">Bit</span></span> | <span data-ttu-id="f9eb4-1050">Value</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1050">Value</span></span> | <span data-ttu-id="f9eb4-1051">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1051">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f9eb4-1052">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1052">0</span></span> | <span data-ttu-id="f9eb4-1053">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1053">0</span></span><br /><span data-ttu-id="f9eb4-1054">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1054">1</span></span> | <span data-ttu-id="f9eb4-1055">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1055">Privileged mode execution</span></span><br /><span data-ttu-id="f9eb4-1056">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1056">User mode execution</span></span> |
| <span data-ttu-id="f9eb4-1057">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1057">1</span></span> | <span data-ttu-id="f9eb4-1058">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1058">0</span></span><br /><span data-ttu-id="f9eb4-1059">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1059">1</span></span> | <span data-ttu-id="f9eb4-1060">Sin protección de MPU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1060">No MPU protection</span></span><br /><span data-ttu-id="f9eb4-1061">Protección de MPU (debe estar seleccionado el modo de usuario)</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1061">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f9eb4-1062">2</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1062">2</span></span> | <span data-ttu-id="f9eb4-1063">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1063">0</span></span><br /><span data-ttu-id="f9eb4-1064">1</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1064">1</span></span> | <span data-ttu-id="f9eb4-1065">Deshabilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1065">Disable shared/external memory access</span></span><br /><span data-ttu-id="f9eb4-1066">Habilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1066">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f9eb4-1067">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1067">[23-3]</span></span> | <span data-ttu-id="f9eb4-1068">0</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1068">0</span></span> | <span data-ttu-id="f9eb4-1069">Reservado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1069">Reserved</span></span>
| <span data-ttu-id="f9eb4-1070">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1070">[31-24]</span></span> | <br /><span data-ttu-id="f9eb4-1071">0x00</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1071">0x00</span></span><br /><span data-ttu-id="f9eb4-1072">0x02</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1072">0x02</span></span> | <span data-ttu-id="f9eb4-1073">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1073">**Compiler ID**</span></span><br /><span data-ttu-id="f9eb4-1074">IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1074">IAR</span></span><br /><span data-ttu-id="f9eb4-1075">GNU</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1075">GNU</span></span> |

#### <a name="module-linker-for-rx65n-using-iar"></a><span data-ttu-id="f9eb4-1076">Enlazador de módulos para RX65N con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1076">Module linker for RX65N using IAR</span></span>

```c
//-----------------------------------------------------------------------------
// ILINK command file template for the Renesas RX microcontroller R5F565N
//-----------------------------------------------------------------------------
define exported symbol __link_file_version_4 = 1;

define memory mem with size = 4G;

// ID Code Protection
define exported symbol __ID_BYTES_1_4   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_5_8   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_9_12  = 0xFFFFFFFF;
define exported symbol __ID_BYTES_13_16 = 0xFFFFFFFF;

// Endian Select Register (MDE)
// Choose between Little endian=0xFFFFFFFF or Big endian=0xFFFFFFF8
define exported symbol __MDES           = 0xFFFFFFFF;

// Option Function Select Register 0 (OFS0)
define exported symbol __OFS0           = 0xFFFFFFFF;

// Option Function Select Register 1 (OFS1)
define exported symbol __OFS1           = 0xFFFFFFFF;

//define region ROM_region16 = mem:[from 0xFFFF8000 to 0xFFFFFFFF];
define region RAM_region16 = mem:[from 0x00010000 to 0x00017FFF];
//define region ROM_region24 = mem:[from 0xFFF00000 to 0xFFFFFFFF];
//define region RAM_region24 = mem:[from 0x00000004 to 0x0001FFFF];
define region ROM_region32 = mem:[from 0xFFF10400 to 0xFFFFFFFF];
//define region RAM_region32 = mem:[from 0x00000004 to 0x0001FFFF];
//define region DATA_FLASH_region = mem:[from 0x00100000 to 0x00107FFF];

initialize by copy { rw, ro section D, ro section D_1, ro section D_2 };
do not initialize  { section .*.noinit };

define block HEAP     with alignment = 4, size = _HEAP_SIZE { };
//define block USTACK   with alignment = 4, size = _USTACK_SIZE { };
//define block ISTACK   with alignment = 4, size = _ISTACK_SIZE { };

//define block STACKS with fixed order { block ISTACK,
//                                       block USTACK };

//place at address mem:0xFFFFFF80 { ro section .nmivec };
//"ROM16":place in ROM_region16        { ro section .code16*,
//                                       ro section .data16* };
//"RAM16":place in RAM_region16        { rw section .data16*,
//                                       rw section __DLIB_PERTHREAD };
//"ROM24":place in ROM_region24        { ro section .code24*,
//                                       ro section .data24* };
//"RAM24":place in RAM_region24        { rw section .data24* };
//"ROM32":place in ROM_region32        { ro };
//"RAM32":place in RAM_region32        { rw,
//                                       ro section D,
//                                       ro section D_1,
//                                       ro section D_2,
//                                       block HEAP,
//                                       block STACKS,
//                                       last section FREEMEM };

//"DATAFLASH":place in DATA_FLASH_region
//                                     { ro section .dataflash* };

define movable block ROPI with alignment = 4, fixed order, static base CB
{
  ro object txm_module_preamble_rx65n.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base SB
{
  rw section .sbdata*,
  rw section .sbrel*,
  rw section __DLIB_PERTHREAD,
  block HEAP
};

place in ROM_region32   { block ROPI };
place in RAM_region16   { block RWPI };
```

#### <a name="building-modules-for-rx65n-using-iar"></a><span data-ttu-id="f9eb4-1077">Compilación de módulos para RX65N con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1077">Building Modules for RX65N using IAR</span></span>

<span data-ttu-id="f9eb4-1078">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1078">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-1079">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de demostración y el proyecto de administrador de módulos de demostración.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1079">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-rx65n-using-iar"></a><span data-ttu-id="f9eb4-1080">Definición de extensión de subproceso para RX65N con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1080">Thread extension definition for RX65N using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-rx65n-using-iar"></a><span data-ttu-id="f9eb4-1081">Compilación de administrador de módulos para RX65N con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1081">Building Module Manager for RX65N using IAR</span></span>

<span data-ttu-id="f9eb4-1082">Se proporciona un área de trabajo de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1082">An example workspace is provided.</span></span> <span data-ttu-id="f9eb4-1083">Compile la biblioteca de ThreadX, la biblioteca de ThreadX Modules, el proyecto de módulo de demostración y el proyecto de administrador de módulos de demostración.</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1083">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-rx65n-using-iar"></a><span data-ttu-id="f9eb4-1084">Atributos de API de habilitación de memoria externa para RX65N con IAR</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1084">Attributes for external memory enable API for RX65N using IAR</span></span>

| <span data-ttu-id="f9eb4-1085">Parámetro del atributo</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1085">Attribute Parameter</span></span> | <span data-ttu-id="f9eb4-1086">Significado</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1086">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f9eb4-1087">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1087">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span></span> | <span data-ttu-id="f9eb4-1088">Ejecutar código</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1088">Execute code</span></span> |
| <span data-ttu-id="f9eb4-1089">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1089">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f9eb4-1090">Acceso de escritura</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1090">Write access</span></span> |
| <span data-ttu-id="f9eb4-1091">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1091">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span></span> | <span data-ttu-id="f9eb4-1092">acceso de lectura</span><span class="sxs-lookup"><span data-stu-id="f9eb4-1092">Read access</span></span> |
