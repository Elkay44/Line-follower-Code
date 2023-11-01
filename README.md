# Line-follower-Code

#define OUT_PIN_13 13

int Left_p = 2;
int Left_n = 3;
int Right_p = 4;
int Right_n = 5;

void setup() {
  // Set the pinMode for motor control pins
  pinMode(Left_p, OUTPUT);
  pinMode(Left_n, OUTPUT);
  pinMode(Right_p, OUTPUT);
  pinMode(Right_n, OUTPUT);

  // Set the pinMode for analog input pins
  for (int i = A0; i <= A4; i++) {
    pinMode(i, INPUT);
  }
}

void loop() {
  int ex_right = analogRead(A0);
  int right = analogRead(A1);
  int centre = analogRead(A2);
  int left = analogRead(A3);
  int ex_left = analogRead(A4);

  // If both extreme left and extreme right sensors are below 700
  if (ex_left < 700 && ex_right < 700) {
    digitalWrite(Left_p, HIGH);
    digitalWrite(Left_n, LOW);
    digitalWrite(Right_p, HIGH);
    digitalWrite(Right_n, LOW);
  }
  
  // If only the extreme left sensor is above 700
  if (ex_left > 700 && ex_right < 700) {
    digitalWrite(Left_p, HIGH);
    digitalWrite(Left_n, LOW);
    digitalWrite(Right_p, LOW);
    digitalWrite(Right_n, LOW);
  }
  
  // If only the extreme right sensor is above 700
  if (ex_left < 700 && ex_right > 700) {
    digitalWrite(Left_p, LOW);
    digitalWrite(Left_n, LOW);
    digitalWrite(Right_p, HIGH);
    digitalWrite(Right_n, LOW);
  }
}
