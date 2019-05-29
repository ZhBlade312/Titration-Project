//Titration Project
<code>int button = 2; //sets up button to 2
int drip = 3;  //sets up dripper to 3
int tubeY = 4; //sets up pneumatic for lever to 4
int tubeXZS = 5; //sets up pneumatic for turntable to 5
int spinner = 6;  //sets up motor to 6
int x = 0; //set x to 0
void setup()
{
Serial.begin(9600); //sets up serial monitor
pinMode(button, INPUT); //sets var button to input
pinMode(drip, OUTPUT); //sets var drip to output
pinMode(tubeY, OUTPUT);//sets var tubeY to output
pinMode(tubeXZS, OUTPUT);//sets var tubeXZS to output
pinMode(spinner, OUTPUT);//sets var spinner to output
}
void loop()
{
if(digitalRead(2) == 0){ //when button is on turn on
Serial.println("on") //says its on
armDown(); //runs function
armUp(); //runs function
turntableclock(); //runs function
armDown(); //runs function
motor(5, 200); //runs function
phDrip(85.); //runs function
armUp(); //runs function
turntablecounter(); //runs function
armDown(); //runs function
}
if(digitalRead(2) == 0){//when button is on turn off
Serial.println("off") //says its off
}
}
void armUp (){
digitalWrite(tubeY, LOW); //turns off lever
Serial.println("down"); //says lever went down
delay(5000); //delays
}
void turntableclock (){
digitalWrite(tubeXZS,HIGH); //rotates turntable clockwise
Serial.println("clock"); //says it turned clockwise
delay(5000); //delays
}
void armDown (){
digitalWrite(tubeY,HIGH); //turns on lever
Serial.println("up");//says lever went on
delay(5000); //delays
}
void motor (int mate, int speed){ //creates two int for the wait delay and speed
digitalWrite(3,speed);//turns on motor
delay(mate*1000);//delays a specific amount of seconds
digitalWrite(3,0);//turns motor off
}
void phDrip(float y){ //creates an int for the number of grams needed
digitalWrite(drip,HIGH); //turns on the dripper
delay(1786*y);//drops a certain volume of water
digitalWrite(drip,LOW); //turns on the dripper
int VOG = analogRead(5); //PH CODE
float voltage = (VOG/1023.)*5; //PH CODE
float pH = 14.3-(voltage)/.25; //PH CODE
Serial.println(pH); //says the pH value
delay(1000); //delays
}
void turntablecounter (){
digitalWrite(tubeXZS,LOW); //rotates turntable counterclockwise
Serial.println("counter"); //says counter
delay(5000); //delays
}</code>
