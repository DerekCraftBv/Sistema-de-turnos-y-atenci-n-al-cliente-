# Diagramas de flujo

## Función validarCliente()

```mermaid

flowchart TD

A[Inicio] --> B[Recibir nombre]

B --> C{¿Nombre vacío?}

C -- Sí --> D[Retornar FALSO]

C -- No --> E[Retornar VERDADERO]

D --> F[Fin]
E --> F

```

## Función validarTramite()

```mermaid
flowchart TD

A[Inicio] --> B[Recibir tipoTramite]

B --> C{¿Es SIMPLE, MEDIO o COMPLEJO?}

C -- Sí --> D[Retornar VERDADERO]

C -- No --> E[Retornar FALSO]

D --> F[Fin]
E --> F

```

## Función determinarTiempoTramite()

```mermaid
flowchart TD

A[Inicio] --> B[Recibir tipoTramite]

B --> C{¿Tipo SIMPLE?}

C -- Sí --> D[Retornar 5]

C -- No --> E{¿Tipo MEDIO?}

E -- Sí --> F[Retornar 15]

E -- No --> G[Retornar 30]

D --> H[Fin]
F --> H
G --> H
```

## Función crearTurno()
```mermaid
flowchart TD

A[Inicio] --> B[Recibir nombre y tipoTramite]

B --> C[Validar cliente]

C --> D{¿Cliente válido?}

D -- No --> E[Mostrar error nombre vacío]

E --> F[Retornar NULO]

D -- Sí --> G[Validar trámite]

G --> H{¿Trámite válido?}

H -- No --> I[Mostrar error trámite inválido]

I --> F

H -- Sí --> J[Crear diccionario turno]

J --> K[Guardar nombre]

K --> L[Guardar tipoTramite]

L --> M[Guardar estado EN ESPERA]

M --> N[Determinar tiempo estimado]

N --> O[Guardar tiempo estimado]

O --> P[Retornar turno]

P --> Q[Fin]

F --> Q
```

## Función agregarAFila()
```mermaid
flowchart TD

A[Inicio] --> B[Recibir turno]

B --> C[Encolar turno]

C --> D[Obtener tipoTramite]

D --> E[Actualizar conteoTramites]

E --> F[Mostrar cliente agregado]

F --> G[Fin]
```

## Función atenderSiguiente()
```mermaid
flowchart TD

A[Inicio] --> B{¿Fila vacía?}

B -- Sí --> C[Mostrar no hay clientes]

C --> D[Fin]

B -- No --> E[Desencolar turno]

E --> F[Guardar en turnoActual]

F --> G[Cambiar estado a ATENDIDO]

G --> H[Agregar a historial]

H --> I[Mostrar cliente atendido]

I --> D
```



## Función calcularEsperaTotal()
```mermaid
flowchart TD

A[Inicio] --> B[Inicializar tiempoTotal en 0]

B --> C[Recorrer filaTurnos]

C --> D[Sumar tiempoEstimado]

D --> E{¿Quedan turnos?}

E -- Sí --> C

E -- No --> F[Retornar tiempoTotal]

F --> G[Fin]
```

## Función mostrarFila() 
```mermaid
flowchart TD

A[Inicio] --> B{¿Fila vacía?}

B -- Sí --> C[Mostrar fila vacía]

C --> D[Fin]

B -- No --> E[Mostrar FILA ACTUAL]

E --> F[Recorrer filaTurnos]

F --> G[Mostrar nombre]

G --> H[Mostrar trámite]

H --> I[Mostrar estado]

I --> J[Mostrar tiempo estimado]

J --> K{¿Quedan turnos?}

K -- Sí --> F

K -- No --> D
```

## Función mostrarTurnoActual()
```mermaid
flowchart TD

A[Inicio] --> B{¿turnoActual es NULO?}

B -- Sí --> C[Mostrar no hay turno]

C --> D[Fin]

B -- No --> E[Mostrar TURNO ACTUAL]

E --> F[Mostrar nombre]

F --> G[Mostrar trámite]

G --> D
```

## Función determinarTramiteMasSolicitado()
```mermaid
flowchart TD

A[Inicio] --> B[Inicializar mayor en 0]

B --> C[Inicializar tramiteMasSolicitado]

C --> D[Recorrer conteoTramites]

D --> E{¿Conteo mayor que mayor?}

E -- Sí --> F[Actualizar mayor]

F --> G[Actualizar tramiteMasSolicitado]

G --> H{¿Quedan trámites?}

E -- No --> H

H -- Sí --> D

H -- No --> I[Retornar tramiteMasSolicitado]

I --> J[Fin]

```

## Función generarReporteDia()
```mermaid
flowchart TD

A[Inicio] --> B[Obtener totalClientes]

B --> C[Inicializar tiempoTotal en 0]

C --> D[Recorrer historialAtendidos]

D --> E[Sumar tiempoEstimado]

E --> F{¿Quedan turnos?}

F -- Sí --> D

F -- No --> G[Determinar trámite más solicitado]

G --> H[Mostrar REPORTE DEL DÍA]

H --> I[Mostrar clientes atendidos]

I --> J[Mostrar tiempo total]

J --> K[Mostrar trámite más solicitado]

K --> L[Fin]
```