´´´
#include <WiFi.h>
#include <WebServer.h>
// SSID & Password
const char* ssid = "Sergi plus"; // Enter your SSID here
const char* password = "937126782*"; //Enter your Password here
WebServer server(80); // Object of WebServer(HTTP port, 80 is defult)
void handle_root(void);
void setup() {
Serial.begin(115200);
Serial.println("Try Connecting to ");
Serial.println(ssid);
// Connect to your wi-fi modem
WiFi.begin(ssid, password);
// Check wi-fi is connected to wi-fi network
while (WiFi.status() != WL_CONNECTED) {
delay(1000);
Serial.print(".");
}
Serial.println("");
Serial.println("WiFi connected successfully");
Serial.print("Got IP: ");
Serial.println(WiFi.localIP()); //Show ESP32 IP on serial
server.on("/", handle_root);
server.begin();
Serial.println("HTTP server started");
delay(100);
}
void loop() {
server.handleClient();
}
// HTML & CSS contents which display on web server
String HTML = "<!DOCTYPE html>\
<html>\
<body>\
<h1>My Primera Pagina con ESP32 - Station Mode &#128522;</h1>\
</body>\
</html>";
// Handle root url (/)
void handle_root() {
server.send(200, "text/html", HTML);
}

´´´
## FUNCIONAMIENTO

Hacemos include de dos librerías, la primera #include <WiFi.h&gt; sirve para permitir que
nuestra placa se conecte a internet, y la segunda librería #include <WebServer.h&gt; es para hacer un
servidor web.
Dentro del void setup() primero imprimimos por pantalla:
Try Connecting to:
Sergi plus
conectamos el mòdem WiFi a la placa
Una vez hecho esto debemos comprobar si el WiFi está conectado a la red WiFi.
Seguidamente el programa creamos una string de nombre HTML que son los contenidos de tipo
HTML que se van a mostrar en el servidor web.

## Salida por terminal 
todo esto es lo que sale.
try connecting to Sergi plus
wifi 
got ip 

