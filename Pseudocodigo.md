### *Pseudocodigo*
```

ENUM TipoTramite
    SIMPLE = 5
    MEDIO = 15
    COMPLEJO = 30
FIN ENUM


VARIABLE filaTurnos = Cola()
VARIABLE historialAtendidos = Lista()
VARIABLE conteoTramites = Diccionario()
VARIABLE turnoActual = NULO

conteoTramites["SIMPLE"] = 0
conteoTramites["MEDIO"] = 0
conteoTramites["COMPLEJO"] = 0


FUNCION validarCliente(nombre)

    SI nombre == "" ENTONCES
        RETORNAR FALSO
    FIN SI

    RETORNAR VERDADERO

FIN FUNCION


FUNCION validarTramite(tipoTramite)

    SI tipoTramite == "SIMPLE" O
       tipoTramite == "MEDIO" O
       tipoTramite == "COMPLEJO" ENTONCES

        RETORNAR VERDADERO

    SINO

        RETORNAR FALSO

    FIN SI

FIN FUNCION


FUNCION determinarTiempoTramite(tipoTramite)

    SEGUN tipoTramite HACER

        CASO "SIMPLE":
            RETORNAR 5

        CASO "MEDIO":
            RETORNAR 15

        CASO "COMPLEJO":
            RETORNAR 30

    FIN SEGUN

FIN FUNCION


FUNCION crearTurno(nombre, tipoTramite)

    SI validarCliente(nombre) == FALSO ENTONCES
        MOSTRAR "Error: nombre vacío"
        RETORNAR NULO
    FIN SI

    SI validarTramite(tipoTramite) == FALSO ENTONCES
        MOSTRAR "Error: trámite inválido"
        RETORNAR NULO
    FIN SI

    VARIABLE turno = Diccionario()

    turno["nombre"] = nombre
    turno["tipoTramite"] = tipoTramite
    turno["estado"] = "EN ESPERA"

    turno["tiempoEstimado"] =
        determinarTiempoTramite(tipoTramite)

    RETORNAR turno

FIN FUNCION


FUNCION agregarAFila(turno)

    filaTurnos.ENCOLAR(turno)

    VARIABLE tipo = turno["tipoTramite"]

    conteoTramites[tipo] =
        conteoTramites[tipo] + 1

    MOSTRAR "Cliente agregado a la fila"

FIN FUNCION


FUNCION atenderSiguiente()

    SI filaTurnos.ESTA_VACIA() ENTONCES
        MOSTRAR "No hay clientes en espera"
        RETORNAR
    FIN SI

    turnoActual = filaTurnos.DESENCOLAR()

    turnoActual["estado"] = "ATENDIDO"

    historialAtendidos.AGREGAR(turnoActual)

    MOSTRAR "Atendiendo a: "
            + turnoActual["nombre"]

FIN FUNCION


FUNCION calcularEsperaTotal()

    VARIABLE tiempoTotal = 0

    PARA CADA turno EN filaTurnos HACER

        tiempoTotal =
            tiempoTotal +
            turno["tiempoEstimado"]

    FIN PARA

    RETORNAR tiempoTotal

FIN FUNCION


FUNCION mostrarFila()

    SI filaTurnos.ESTA_VACIA() ENTONCES
        MOSTRAR "La fila está vacía"
        RETORNAR
    FIN SI

    MOSTRAR "===== FILA ACTUAL ====="

    PARA CADA turno EN filaTurnos HACER

        MOSTRAR "Cliente: "
                + turno["nombre"]

        MOSTRAR "Trámite: "
                + turno["tipoTramite"]

        MOSTRAR "Estado: "
                + turno["estado"]

        MOSTRAR "Tiempo estimado: "
                + turno["tiempoEstimado"]

    FIN PARA

FIN FUNCION


FUNCION mostrarTurnoActual()

    SI turnoActual == NULO ENTONCES
        MOSTRAR "No hay turno en atención"
        RETORNAR
    FIN SI

    MOSTRAR "===== TURNO ACTUAL ====="

    MOSTRAR "Cliente: "
            + turnoActual["nombre"]

    MOSTRAR "Trámite: "
            + turnoActual["tipoTramite"]

FIN FUNCION


FUNCION determinarTramiteMasSolicitado()

    VARIABLE mayor = 0
    VARIABLE tramiteMasSolicitado = ""

    PARA CADA tipo EN conteoTramites HACER

        SI conteoTramites[tipo] > mayor ENTONCES

            mayor = conteoTramites[tipo]

            tramiteMasSolicitado = tipo

        FIN SI

    FIN PARA

    RETORNAR tramiteMasSolicitado

FIN FUNCION


FUNCION generarReporteDia()

    VARIABLE totalClientes =
        historialAtendidos.TAMANIO()

    VARIABLE tiempoTotal = 0

    PARA CADA turno EN historialAtendidos HACER

        tiempoTotal =
            tiempoTotal +
            turno["tiempoEstimado"]

    FIN PARA

    VARIABLE tramiteMasSolicitado =
        determinarTramiteMasSolicitado()

    MOSTRAR "===== REPORTE DEL DÍA ====="

    MOSTRAR "Clientes atendidos: "
            + totalClientes

    MOSTRAR "Tiempo total de atención: "
            + tiempoTotal

    MOSTRAR "Trámite más solicitado: "
            + tramiteMasSolicitado

FIN FUNCION


PROGRAMA PRINCIPAL

    VARIABLE turno1 =
        crearTurno("Ana", "SIMPLE")

    SI turno1 != NULO ENTONCES
        agregarAFila(turno1)
    FIN SI


    VARIABLE turno2 =
        crearTurno("Luis", "MEDIO")

    SI turno2 != NULO ENTONCES
        agregarAFila(turno2)
    FIN SI


    VARIABLE turno3 =
        crearTurno("Maria", "COMPLEJO")

    SI turno3 != NULO ENTONCES
        agregarAFila(turno3)
    FIN SI


    VARIABLE turno4 =
        crearTurno("", "COMPLEJO")


    VARIABLE turno5 =
        crearTurno("Carlos", "INVALIDO")


    mostrarFila()


    MOSTRAR "Tiempo total de espera: "
            + calcularEsperaTotal()


    atenderSiguiente()


    mostrarTurnoActual()


    generarReporteDia()

FIN PROGRAMA

```