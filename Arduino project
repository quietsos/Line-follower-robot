// Md Shohanuzzaman //
// Information and Communication Technology //
// Islamic University Bangladesh //

// Line follower robot //

int motorRightA = 4;              //motor A1 pin
int motorRightB = 5;              //motor A2 pin
int motorLeftA = 6;               //motor A3 pin
int motorLeftB = 7;               //motor A4 pin
int Sample = 0,Speed=128;

int rightSensor = A0;             //right side IR sensor
int leftSensor = A1;              //left side IR sensor

void setup()
{

  pinMode(motorRightA,OUTPUT);   //pin mode for all pin
  pinMode(motorRightB,OUTPUT);
  pinMode(motorLeftA,OUTPUT);
  pinMode(motorLeftB,OUTPUT);
 
  pinMode(rightSensor,INPUT);
  pinMode(leftSensor,INPUT);

  Serial.begin(9600);
  

}

void loop()
{
    int right = analogRead(rightSensor);  //read analog value for right sensor
    int left = analogRead(leftSensor);    //read analog value for left sensor

    Serial.print(right);
    Serial.print(" | ");
    Serial.println(left);

    if( right <= 300 && left <= 300)
    {
      analogWrite(motorRightA,0);   // motor A clockwise
      analogWrite(motorRightB,Speed);
      analogWrite(motorLeftA,Speed);   // motor B clockwise
      analogWrite(motorLeftB,0);
      delayMicroseconds(500);
      ++Sample;
      if (Sample == 100){
        Sample = 0;
        Speed += 5;
        if (Speed>128)
            Speed = 128;
      }
    }

   else if( right <= 300 && !left <= 300)
     {
      Speed=70;
      analogWrite(motorRightA,LOW);   // motor A clockwise
      analogWrite(motorRightB,150); 
      analogWrite(motorLeftA,LOW);    // motor B anti-clockwise
      analogWrite(motorLeftB,150); 
     }

    else if( !right <= 300 && left <= 300)
     {
       Speed=70;
      analogWrite(motorRightA,150);  // motor A anti-clockwise
      analogWrite(motorRightB,LOW);
      analogWrite(motorLeftA,150);   // motor B clockwise
      analogWrite(motorLeftB,LOW);
     }

    else if( !right <=300 && !left <= 300)
    {
      analogWrite(motorRightA,LOW);   // motor A stop
      analogWrite(motorRightB,LOW);
      analogWrite(motorLeftA,LOW);    // motor B stop
      analogWrite(motorLeftB,LOW);
    }
}
