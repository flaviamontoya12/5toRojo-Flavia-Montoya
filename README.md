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