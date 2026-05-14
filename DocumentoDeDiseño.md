# Documento de Diseño

## Nombre del proyecto
**Sistema de turnos y atención al cliente**

---

# 1. Introducción

El proyecto consiste en desarrollar un sistema de turnos para organizar la atención de clientes dentro de una sucursal de servicios. El sistema permitirá registrar clientes, administrar una fila de espera y generar reportes utilizando programación modular y estructuras de datos adecuadas.

El objetivo principal es mejorar la organización de atención al cliente respetando el orden de llegada y facilitando el control de los turnos.

---

# 2. Objetivo del sistema

El sistema fue diseñado para:

- Registrar clientes.
- Validar información ingresada.
- Administrar una fila FIFO.
- Calcular tiempos de espera.
- Mostrar información de atención.
- Generar reportes finales.

---

# 3. Justificación de las estructuras de datos

Para el desarrollo del sistema se seleccionaron distintas estructuras de datos según las necesidades de cada proceso.

---

## Cola FIFO

La estructura principal del sistema es una cola FIFO (First In, First Out).

Se eligió esta estructura porque representa correctamente el comportamiento real de una fila de atención, donde el primer cliente en llegar debe ser el primero en ser atendido.

La cola permite:

- agregar clientes al final de la fila,
- atender clientes desde el inicio,
- mantener el orden de llegada automáticamente.

En el sistema, la cola se utiliza mediante la variable:

```text
filaTurnos
```

Operaciones utilizadas:
- ENCOLAR
- DESENCOLAR
- ESTA_VACIA

---

## Lista

Se utilizó una lista para almacenar el historial de clientes atendidos.

Esta estructura permite guardar todos los turnos finalizados de forma ordenada para posteriormente generar estadísticas y reportes.

La lista facilita:
- recorrer clientes atendidos,
- calcular tiempos totales,
- consultar información histórica.

En el sistema se utiliza mediante:

```text
historialAtendidos
```

---

## Diccionario

Se utilizaron diccionarios para almacenar información relacionada con cada turno y también para llevar el conteo de trámites.

Cada turno contiene varios datos asociados:
- nombre,
- trámite,
- estado,
- tiempo estimado.

El diccionario permite acceder fácilmente a cada dato mediante una clave.

---

## Enumeración

Se utilizó una enumeración llamada:

```text
TipoTramite
```

La enumeración ayuda a representar los tipos de trámite disponibles junto con su tiempo estimado.

Esto mejora:
- la organización del sistema,
- la legibilidad del código,
- el control de valores válidos.

Valores utilizados:

```text
SIMPLE = 5
MEDIO = 15
COMPLEJO = 30
```

---

# 4. Justificación de los módulos

El sistema fue dividido en módulos o funciones para facilitar su comprensión, mantenimiento y reutilización.

Cada función cumple una responsabilidad específica dentro del sistema.

---

## validarCliente()

Se encarga de verificar que el nombre ingresado no esté vacío.

Separar esta validación permite reutilizarla en distintas partes del sistema y evita repetir código.

---

## validarTramite()

Verifica que el trámite ingresado sea válido.

Este módulo ayuda a controlar errores y garantiza que solamente existan trámites permitidos.

---

## determinarTiempoTramite()

Calcula el tiempo estimado según el tipo de trámite.

Separar esta lógica permite modificar tiempos fácilmente sin afectar otras partes del sistema.

---

## crearTurno()

Se encarga de crear la estructura completa del turno.

Este módulo centraliza toda la información necesaria para registrar un cliente.

---

## agregarAFila()

Agrega el turno al final de la cola y actualiza el conteo de trámites.

Separar esta función facilita el control de la fila de espera.

---

## atenderSiguiente()

Gestiona el proceso de atención del siguiente cliente disponible.

También actualiza el historial y el estado del turno.

---

## calcularEsperaTotal()

Calcula el tiempo total de espera sumando los tiempos estimados de todos los clientes pendientes.

Esto ayuda a proporcionar información útil a los usuarios.

---

## mostrarFila()

Permite visualizar todos los clientes pendientes en la cola.

Este módulo facilita el monitoreo del estado actual del sistema.

---

## mostrarTurnoActual()

Muestra el cliente que está siendo atendido en ese momento.

Ayuda a mantener visible la información de atención actual.

---

## determinarTramiteMasSolicitado()

Analiza los datos registrados y determina cuál trámite fue solicitado más veces.

Este módulo permite generar estadísticas útiles para la sucursal.

---

## generarReporteDia()

Genera un resumen completo de las actividades realizadas durante el día.

Incluye:
- clientes atendidos,
- tiempo total,
- trámite más solicitado.

---

# 5. Diseño general del sistema

El sistema sigue una estructura modular donde cada función cumple una tarea específica.

El flujo general es:

1. Registrar cliente.
2. Validar datos.
3. Crear turno.
4. Agregar turno a la cola.
5. Mostrar fila.
6. Atender clientes.
7. Actualizar historial.
8. Generar reporte final.

---

# 6. Beneficios del diseño

El diseño modular y el uso de estructuras de datos adecuadas permiten:

- mayor organización,
- facilidad de mantenimiento,
- reutilización de código,
- mejor control de errores,
- claridad en la lógica del sistema,
- facilidad para futuras mejoras.

---