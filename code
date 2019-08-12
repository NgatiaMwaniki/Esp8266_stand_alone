#include <ESP8266WiFi.h>
#include <WiFiClient.h> 
#include <ESP8266WebServer.h>
#include <ESP8266HTTPClient.h>


/* Set these to your desired credentials. */
const char *ssid = "**********";  //ENTER YOUR WIFI SETTINGS 
const char *password = "********";
int data1, data2, data3, data4, data5, ok;
unsigned char buff[10], i;
String buffer1, buffer2,buffer3;

//Web/Server address to read/write from 
const char *host = "*********";   // website or IP address of server 

//=======================================================================
//                    Power on setup
//=======================================================================

void setup() {
  
  delay(1000);
  Serial.begin(9600);
  Serial.print("Starting up!");
  WiFi.mode(WIFI_OFF);        //Prevents reconnection issue (taking too long to connect)
  delay(1000);
  WiFi.mode(WIFI_STA);        //This line hides the viewing of ESP as wifi hotspot
  
  WiFi.begin(ssid, password);     //Connect to your WiFi router
  Serial.println("");

  Serial.print("Connecting");
  // Wait for connection
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }

  //If connection successful show IP address in serial monitor
  Serial.println("");
  Serial.print("Connected to ");
  Serial.println(ssid);
  Serial.print("IP address: ");
  Serial.println(WiFi.localIP());  //IP address assigned to your ESP
}

//=======================================================================
//                    Main Program Loop
//=======================================================================
void loop() {
  HTTPClient http;    //Declare object of class HTTPClient
//String postData; 
  String ADCData, station, w_temp, postData;
//  int adcvalue=analogRead(A0);  //Read Analog value of LDR
//  ADCData = String(adcvalue);   //String to interger conversion
//  station = "A";

  //Post Data
 if (Serial.available() > 0)
  {
    delay(100);
     while (Serial.available() > 0)
        {
          buffer1 = Serial.readString();
            
          
          if (buffer1[0] == '*')
          {
            if (buffer1[7] == '#')
            {
              Serial.println(buffer1);
              data1 = ((buffer1[1] - 0x30) * 10 + (buffer1[2] - 0x30));
              data2 = ((buffer1[3] - 0x30) * 10 + (buffer1[4] - 0x30));
              data3 = ((buffer1[5] - 0x30) * 10 + (buffer1[6] - 0x30));
            }
          }
        }
    }

    ADCData= data1;
    station= data2;
    w_temp= data3;

    
  postData = "status=" + ADCData + "&station=" + station + "&w_temp=" + w_temp ;

  
  http.begin("http://***********");              //Specify request destination
  http.addHeader("Content-Type", "application/x-www-form-urlencoded");    //Specify content-type header

  int httpCode = http.POST(postData);   //Send the request
  String payload = http.getString();    //Get the response payload

  Serial.println(httpCode);   //Print HTTP return code
  Serial.println(payload);    //Print request response payload

  http.end();  //Close connection
  
  delay(1000); 
