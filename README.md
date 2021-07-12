# controlling-6-servo-motors-
## Designing and programing to control 6 servo motors for the arms of the evaluation robot.

### The circuit design 
The circuit contains:

- Arduino UNO.
- Breadboard.
- 6 servo motors.
- 4.5V Battery.
- Wires ( red= power , black= ground , yellow and green = signal).
 
and the circuit was designed using tinkercad website as below:
#### Diagram preview:
![controlling 6 servo motors ](https://user-images.githubusercontent.com/86317095/125345408-2bbbe880-e361-11eb-9f25-06fe3ced96fd.png)

### Programming three coordinated movements of the robot arms
 The circuit was programmed using the C++ language via the Tinkercad website as shown in ino file in this repository.
 
 #### Code Explanation:
 ---
 #### Defining the servos:
 ```
 #include <Servo.h>;


Servo ServoRightArm1;
Servo ServoRightArm2;
Servo ServoRightArm3;
Servo ServoLeftArm1;
Servo ServoLeftArm2;
Servo ServoLeftArm3;
```
#### sitting up:
```
void setup()
{
 initialPosition();

  Serial.begin(9600);
  ServoRightArm1.attach(3);
  ServoRightArm2.attach(5);
  ServoRightArm3.attach(6);
  ServoLeftArm1.attach(9);
  ServoLeftArm2.attach(10);
  ServoLeftArm3.attach(11);
  
  Serial.println("enter the number of the move");
  Serial.println("(1) if you want move1");
  Serial.println("(2) if you want move2");
  Serial.println("(3) if you want move3");
  
  
}
```
#### initial position function: 
```
void initialPosition(){
  
       ServoRightArm1.write(0);
       ServoRightArm2.write(0);
       ServoRightArm3.write(0);
       ServoLeftArm1.write(0);
       ServoLeftArm2.write(0);
       ServoLeftArm3.write(0);
  
  ```
 ##### (( It depends on the number you enter in the serial monitor.))
 #### First move:
  ```void loop()
{
   if (Serial.available() > 0)
  {
    int input = Serial.read();
    
    // first move (if user entered 1)
    if (input == '1')
    {
     Serial.println('\n');
     Serial.println("Doing  Move1...");
  
      ServoRightArm1.write(0);
      ServoRightArm2.write(0);
      ServoRightArm3.write(180);
      delay(800);
      ServoRightArm1.write(60);
      delay(800);
      ServoRightArm1.write(30);
      delay(2000);
      
      initialPosition();
      Serial.println("Done");
      
    }
  
  ```
   
   #### Second move:
   
    ``` else if (input == '2')
    {
     Serial.println('\n');
     Serial.println("Doing  Move2...");
        
      ServoRightArm1.write(180);
      ServoRightArm2.write(90);
      ServoRightArm3.write(45);
      delay(2000);
      
      initialPosition();
      Serial.println("Done");
    
    }
    ```
   #### Third move: 
    
    ```
    else if (input == '3')
    {
    Serial.println('\n');
    Serial.println("Doing  Move3...");
      
      ServoRightArm1.write(0);
      ServoRightArm2.write(90);
      ServoRightArm3.write(90);
      
      ServoLeftArm1.write(0);
      ServoLeftArm2.write(90);
      ServoLeftArm3.write(90);
      
      delay(800);
      ServoRightArm2.write(0);
      delay(800);
      ServoRightArm3.write(90);
      delay(2000);
      
      initialPosition();
      Serial.println("Done");
    }
    ```
   
   
     
  ### For simulation:
 - [Press here ](https://www.tinkercad.com/things/5s1tgjjn475-controlling-6-servo-motors-)
      
