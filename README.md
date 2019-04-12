int photosensor = A0; 

int analogvalue;  
char light[30];


void setup() {

	Serial.begin();


	Particle.variable("analogvalue", analogvalue);

	Particle.variable("light", light);

	Particle.subscribe("hook-response/light", myHandler, MY_DEVICES);
}
void myHandler(const char *event, const char *data) {

}

void loop() {

	
	analogvalue = analogRead(photosensor);
	
	sprintf(light,"%d", analogvalue);


	Particle.publish("light", light, PRIVATE);


	delay(3000);
}
