# Hello-World
BLDC motor control Arduino Uno L298n Hall Sensors.
/*
 Motor - brushless motor control
 Created 07 Jan. 2018
 This example code is in the public domain.
 http://engineer2you.blogspot.com
 */

const byte en_A = 6;
const byte in_A = 3;
const byte en_B = 4;
const byte in_B = 5;
const byte en_C = 7;
const byte in_C = 8;

int speed_motor = 20;

void setup() {
  pinMode(en_A,OUTPUT);
  pinMode(in_A,OUTPUT);
  pinMode(en_B,OUTPUT);
  pinMode(in_B,OUTPUT);
  pinMode(en_C,OUTPUT);
  pinMode(in_C,OUTPUT);

  // start serial port at 9600 bps:
  Serial.begin(9600);
  while (!Serial) {
    ; // wait for serial port to connect. Needed for native USB port only
  }
}

void loop() {
  //increasing speed gradually by loop
  for (int i = 0; i<=(21-speed_motor)*5; i++) {
    motor_run();
  }
  
  if (speed_motor > 2) speed_motor = speed_motor - 1; //increasing speed
  Serial.println(speed_motor);  //print out speed to serial port
}
