# **Descripción del problema**

## **Nombre del proyecto**

**Sistema de turnos y atención al cliente**


Una sucursal de servicios necesita un sistema que ayude a organizar la atención de
clientes de manera más rápida y ordenada. Actualmente, los clientes llegan y esperan
ser atendidos, pero no existe un control claro del orden de llegada ni del tiempo
aproximado de espera, lo que puede causar desorganización, retrasos y dificultades
para administrar los turnos correctamente.


Para resolver este problema se desarrollará un sistema de turnos basado en una cola
FIFO (First In, First Out), donde el primer cliente en entrar será el primero en ser
atendido. El sistema permitirá registrar clientes, administrar la fila de espera, calcular
tiempos aproximados de atención y generar un reporte al finalizar el día.


Este sistema está dirigido principalmente a empleados y administradores de atención
al cliente que necesitan llevar un mejor control de las personas que esperan un
trámite. También beneficiará a los clientes, ya que podrán conocer el estado de la fila y
el tiempo aproximado que tendrán que esperar.

# **Entradas del sistema**


El sistema recibirá la siguiente información:


  - Nombre del cliente.

  - Tipo de trámite.

  - Opciones seleccionadas dentro del menú.


Los tipos de trámite disponibles serán:


|Trámite|Tiempo estimado|
|---|---|
|SIMPLE|5 minutos|
|MEDIO|15 minutos|


# **Salidas del sistema**

El sistema mostrará:


  - Confirmación cuando un cliente sea registrado.

  - Estado actual de la fila.

  - Cliente que está siendo atendido.

  - Tiempo estimado de espera.

  - Mensajes de error cuando exista información inválida.

  - Reporte final del día.


El reporte final incluirá:


  - Total de clientes atendidos.

  - Tiempo total de atención.

  - Historial de clientes atendidos.

  - Trámite más solicitado.

  - Cantidad total de clientes registrados.

# **Funcionamiento del sistema**


Cuando un cliente llegue, el sistema solicitará su nombre y el tipo de trámite que desea
realizar. Después de validar los datos, se calculará automáticamente el tiempo
estimado según el trámite seleccionado y se creará un turno que será agregado al final
de la fila.


Cada cliente será atendido respetando el orden de llegada. Cuando se atienda un
turno, este se eliminará de la fila y se guardará en el historial de clientes atendidos.


El sistema también permitirá mostrar la fila actual de clientes en espera y visualizar el
turno que está siendo atendido en ese momento.


Además, se calculará el tiempo de espera tomando en cuenta cuántos clientes están
delante en la fila y el tiempo estimado de cada trámite.


Al finalizar el día, el sistema analizará todos los trámites registrados para determinar
cuál fue el más solicitado y generará un reporte con toda la información de las
atenciones realizadas.

# **Funciones principales**

## **crearTurno()**


Esta función se encargará de crear un nuevo turno para un cliente utilizando:


  - nombre,

  - trámite,

  - estado,

  - tiempo estimado.

## **validarCliente()**


Esta función verificará que el nombre ingresado sea válido y que no esté vacío.

## **validarTramite()**


Esta función comprobará que el trámite ingresado exista dentro de las opciones
disponibles.

## **agregarAFila()**


Esta función agregará el turno del cliente al final de la cola respetando el orden FIFO.


## **atenderSiguiente()**

Esta función atenderá al primer cliente registrado en la fila y actualizará el historial de
atención.

## **calcularEsperaTotal()**


Esta función calculará el tiempo total de espera considerando todos los clientes
pendientes.

## **determinarTiempoTramite()**


Esta función asignará automáticamente el tiempo estimado dependiendo del trámite
seleccionado.

## **mostrarFila()**


Esta función mostrará todos los clientes que se encuentran actualmente en espera.

## **mostrarTurnoActual()**


Esta función mostrará el cliente que está siendo atendido en ese momento.

## **determinarTramiteMasSolicitado()**


Esta función analizará los trámites registrados y mostrará cuál fue el más solicitado
durante el día.


## **generarReporteDia()**

Esta función generará un reporte final con estadísticas e información general del
sistema.

# **Escenarios que debe contemplar el** **sistema**


El sistema deberá funcionar correctamente en situaciones como:


  - intentar atender cuando la fila está vacía,

  - registrar un cliente con nombre vacío,

  - registrar un trámite inválido,

  - calcular tiempos de espera con varios clientes en fila,

  - generar un reporte final con diferentes tipos de trámite.

# **Estructuras de datos utilizadas**

## **Cola FIFO**


Se utilizará para almacenar los clientes en espera respetando el orden de llegada.

## **Lista**


Se usará para guardar el historial de clientes atendidos.

## **Diccionarios**


Permitirán almacenar la información de cada turno:


  - nombre,

  - trámite,

  - estado,

  - tiempo estimado.


También servirán para contar cuántas veces se solicita cada trámite.

## **Enumeraciones**


Representarán los tipos de trámite disponibles:


  - SIMPLE,

  - MEDIO,

  - COMPLEJO.

# **Objetivo del proyecto**


El objetivo de este proyecto es desarrollar un sistema organizado y modular que
permita administrar turnos de atención al cliente utilizando estructuras de datos
adecuadas, validaciones y funciones separadas para cada tarea del sistema.