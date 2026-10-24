# 5toRojo-Flavia-Montoya
Repositorio pensamiento computacional 
Primera clase: creación de repositorio 

tercera clase: actividad de distancias 
representamos un mapa con circulos y lineas usando papel, marcadores y regla. propusimos rutas 
sumando distancias entre las ciudades propuestas, aplicando nuestros conocimientos para emcontrar 
la ruta mas corta, Ademas armamos un circuito con 6 LED en paralelo y 2 Led de distintos colores 
Actividades adjuntas:
https://www.tinkercad.com/things/7oEBFdjXngn-practica-3-led?sharecode=ls7F3lmKjk6TOtskgJKShXZA7ilyjbBxP4iNFuZ4Qg8
https://link.camscanner.com/7K3LtacqZi -- trabajo teorico 



cuarta clase: actividad de tinkercad circuito 
 Nuestro problema fue con el indicador de la puerta abierta o cerrada. 

¿Cual es el problema?
A veces las personas dejan la puerta o acceso principal abierto por descuido, lo que compromete la seguridad y la privacidad de un espacio.
¿Quién se beneficiaría de la solución?
Estudiantes, trabajadores o familias que deseen mantener el control visual e inmediato sobre el estado de la puerta de su habitación, estudio u oficina.
¿Cómo ayudará tu prototipo a resolver la situación?
El circuito detecta si un interruptor/pulsador (que simula la puerta) está accionado. Si la puerta está abierta, encenderá un LED de alerta y enviará un mensaje por el Monitor Serial indicando la situación en
tiempo real.

https://www.tinkercad.com/things/kK34A5nGeKA/editel?lessonid=EFU6PEHIXGFUR1J&projectid=OGK4Q7VL20FZRV9&collectionid=undefined&title=Editing%20Components#/lesson-viewer



// Definición de pines basados en el circuito conectado const int PIN_BOTON - 2; // Dispositivo de entrada (Pulsador / Puerta)
const int PIN_LED = 13; // Dispositivo de salida (LED indicador)
int estadoBoton = 0;
// Variable para almacenar la lectura de la
entrada
void setup () {
// Configuración de los pines
pinMode (PIN_BOTON, INPUT); // Configura el pin 2 como entrada
pinMode (PIN_LED, OUTPUT);
// Configura el pin 13 como salida
// Inicializar la comunicación serial para el monitor
Serial. begin (9600);
}
void l00p() {
// 1. Leer una entrada: Comprueba el estado actual del pulsador
estadoBoton = digitalRead(PIN_BOTON);
// 2. Procesar una condición: Evalúa si el botón está presionado o no
if (estadoBoton == HIGH) {
// 3. Generar una respuesta (Caso: Puerta abierta / Alerta activada)
digitalWrite(PIN_LED, HIGH);
// Enciende el LED
Serial.println("ALERTA: Puerta abierta detectada."); // Mensaje en monitor serial
} else {
// 3. Generar una respuesta (Caso: Puerta cerrada / Estado seguro)
digitalWrite(PIN_LED, LOW);
// Apaga el LED
Serial.println("Estado normal: Puerta cerrada.");
// Mensaje en monitor serial
}
delay(300); // Pequeña pausa de estabilidad para el sistema



se utiliza digitslread (pin_boton); para capturar pulsado el estado del pulsador conectado al pin 2.
se evelua mediante una estructura condicional if/else si la senal leida es alta (high) o baja (low).
se acciona fisicamente el LED (digitalWrite) y se imprimen mensajes de texto informativos en el monitor serial del sistema.

actividad 23/10
3 enunciados de logica 
https://link.camscanner.com/7hnZL1mp1M
pseudocodigos:
ENUNCIADO 1:
Algoritmo GestionCentroAtencion

    // Definición del tipo de dato/estructura Estudiante
    Estructura Estudiante
        id_estudiante Como Cadena
        nombre Como Cadena
        tipo_tramite Como Cadena  // "a": Consulta general, "b": Entrega documentos, "c": Solicitud constancia
        hora_llegada Como Entero
        prioridad Como Entero     // 1: Alta (Consulta general), 2: Media (Entrega), 3: Baja (Constancia)
        hora_salida Como Entero
    FinEstructura

    ColaEstudiantes = CrearColaVacia()

    // 1. LLEGADA Y REGISTRO DE ESTUDIANTES
    Proceso RegistrarEstudiante()
        Escribir "Ingrese Cédula/ID:"
        Leer estudiante.id_estudiante
        Escribir "Ingrese Nombre completo:"
        Leer estudiante.nombre
        Escribir "Ingrese Tipo de Trámite (a: Consulta, b: Entrega, c: Constancia):"
        Leer estudiante.tipo_tramite
        Escribir "Ingrese Hora de Llegada (en minutos):"
        Leer estudiante.hora_llegada

        // Asignar nivel de prioridad según el tipo de trámite
        Segun estudiante.tipo_tramite Hacer
            'a': estudiante.prioridad <- 1  // Consulta general (Más rápido/básico)
            'b': estudiante.prioridad <- 2  // Entrega de documentos
            'c': estudiante.prioridad <- 3  // Solicitud de constancia
        FinSegun

        // Insertar en la cola según prioridad y orden de llegada
        AgregarAColaPonderada(ColaEstudiantes, estudiante)
    FinProceso

    // 2. ATENCIÓN EN VENTANILLA
    Proceso AtenderSiguiente()
        Si NO EstaVacia(ColaEstudiantes) Entonces
            estudianteActual = ObtenerSiguiente(ColaEstudiantes)
            
            Escribir "Atendiendo a: ", estudianteActual.nombre, " - Trámite: ", estudianteActual.tipo_tramite
            
            // Simular procesamiento del trámite
            Escribir "Ingrese Hora de Salida:"
            Leer estudianteActual.hora_salida
            
            // 3. CIERRE Y ESTADÍSTICAS
            tiempoEspera = estudianteActual.hora_salida - estudianteActual.hora_llegada
            Escribir "Trámite finalizado. Tiempo total de atención/espera: ", tiempoEspera, " minutos."
        Sino
            Escribir "No hay estudiantes en espera en la cola."
        FinSi
    FinProceso

FinAlgoritmo

ENUNCISDO 2:
Algoritmo RutaAutobusEscolar

    // Definición de arreglos con los datos de las paradas
    Paradas Pendientes = ["P1", "P2", "P3", "P4", "P5", "P6"]
    EstudiantesPorParada = [3, 5, 2, 4, 6, 1] // Cantidad en P1, P2, P3, P4, P5, P6 respectivamente
    
    distanciaTotal = 0
    totalEstudiantesRecogidos = 0
    
    // a) Definir punto de partida
    paradaActual = "P1"
    RutaSeguida = ["P1"]
    
    // Registrar estudiantes de la parada inicial
    totalEstudiantesRecogidos = totalEstudiantesRecogidos + EstudiantesPorParada[1]
    RemoverDePendientes("P1")

    // b y c) Buscar iterativamente la parada más cercana linealmente para evitar cruces
    Mientras NO EstaVacia(ParadasPendientes) Hacer
        siguienteParada = BuscarParadaMasCercanaEficiente(paradaActual, ParadasPendientes)
        distancia = ObtenerDistancia(paradaActual, siguienteParada)
        
        distanciaTotal = distanciaTotal + distancia
        totalEstudiantesRecogidos = totalEstudiantesRecogidos + ObtenerEstudiantes(siguienteParada)
        
        paradaActual = siguienteParada
        AgregarA(RutaSeguida, paradaActual)
        RemoverDePendientes(siguienteParada)
    FinMientras

    // d) Finalizar en el colegio desde la última parada
    distanciaTotal = distanciaTotal + ObtenerDistancia(paradaActual, "Colegio")
    AgregarA(RutaSeguida, "Colegio")

    // Mostrar resultados finales
    Escribir "Ruta elegida: ", RutaSeguida
    Escribir "Total estudiantes recogidos: ", totalEstudiantesRecogidos
    Escribir "Distancia total recorrida: ", distanciaTotal, " km"

FinAlgoritmo

ENUNCIADO 3:
Algoritmo PromedioNotasEstudiante

    Definir nota1, nota2, nota3, promedio Como Real

    // 1. Validación de entradas (Rango de 0 a 100)
    Repetir
        Escribir "Ingrese la nota 1 (0 a 100):"
        Leer nota1
    Hasta Que (nota1 >= 0 Y nota1 <= 100)

    Repetir
        Escribir "Ingrese la nota 2 (0 a 100):"
        Leer nota2
    Hasta Que (nota2 >= 0 Y nota2 <= 100)

    Repetir
        Escribir "Ingrese la nota 3 (0 a 100):"
        Leer nota3
    Hasta Que (nota3 >= 0 Y nota3 <= 100)

    // 2. Corrección del cálculo del promedio
    promedio = (nota1 + nota2 + nota3) / 3

    Escribir "El promedio obtenido es: ", promedio

    // 3. Evaluación de aprobación / mejora adicional (Aprobado >= 50)
    Si promedio >= 50 Entonces
        Escribir "Aprobó"
    SiNo
        Escribir "No aprobó (Raspó) - Debe ir a recuperación"
    FinSi

FinAlgoritmo
