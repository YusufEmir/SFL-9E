# SFL9E
Dönem Ödevi
int trigPin = 5;
int echoPin = 4;
 //sağ
int trigPin2 = 13;
int echoPin2 = 6;
//sol
int trigPin3 = 8;
int echoPin3 = 7;
 
// motor 1
int enA = 9;//ok
int in1 = 2;
int in2 = 10;
// motor 2
int enB = 3;//ok
int in3 = 11;
int in4 = 12;
 
void setup()
{
Serial.begin (9600);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
 
  pinMode(trigPin2, OUTPUT);
  pinMode(echoPin2, INPUT);
 
  pinMode(trigPin3, OUTPUT);
  pinMode(echoPin3, INPUT);
 
  pinMode(9,OUTPUT);
  pinMode(2,OUTPUT);
  pinMode(10,OUTPUT);
  pinMode(3,OUTPUT);
 
   pinMode(11,OUTPUT);
  pinMode(12,OUTPUT);
  }
 
void loop()
 
{
//sistemin 3saniye gecikmeli başlaması için
  do {delay(3000);}
  while(0);
 
//ön------------------------------------------------------------------
 
int duration, distance;
    digitalWrite (trigPin, HIGH);
    delayMicroseconds (10);
    digitalWrite (trigPin, LOW);
    duration = pulseIn (echoPin, HIGH);
    distance = (duration/2) / 29.1;
 
    Serial.print(&quot;sag sensor:&quot;);
      Serial.print(distance);   
      Serial.print(&quot;cm&quot;);
      Serial.println();
  //sağ-------------------------------------------------------------------
 
int duration2, distance2;
    digitalWrite (trigPin2, HIGH);
    delayMicroseconds (10);
    digitalWrite (trigPin2, LOW);
    duration2 = pulseIn (echoPin2, HIGH);
    distance2 = (duration2/2) / 29.1;
 
    Serial.print(&quot;sag sensor:&quot;);
      Serial.print(distance2);   
      Serial.print(&quot;cm&quot;);
      Serial.println();
  //sol------------------------------------------------------------------
 
 int duration3, distance3;
    digitalWrite (trigPin3, HIGH);
    delayMicroseconds (10);
    digitalWrite (trigPin3, LOW);
    duration3 = pulseIn (echoPin3, HIGH);
    distance3 = (duration3/2) / 29.1;
 
    Serial.print(&quot;sag sensor:&quot;);
      Serial.print(distance3);   
      Serial.print(&quot;cm&quot;);
      Serial.println();
     //------------------------------------------------------------------
 
      // Motorlar sabit hızda aynı yöne dönüyorlar.
  // sol motor ileri
  digitalWrite(in1, HIGH);
  digitalWrite(in2, LOW);
  // Motor 1 için 0~255 arasında bir hız değeri verelim. 255 en üst sınır
  analogWrite(enA, 100);
  // sağ motor ileri
  digitalWrite(in3, HIGH);
  digitalWrite(in4, LOW);
  // Motor 2 için 0~255 arasında bir hız değeri verelim. 255 en üst sınır
  analogWrite(enB, 100);
  delay(2000);
 
  //-------------------KOŞUL BLOĞU----------------------
      if(distance&lt;10 &amp;&amp; distance &gt;4)//ön sensör
      {
        //motorlar durduruluyor
        digitalWrite(in1, LOW);
         digitalWrite(in2, LOW);  
        digitalWrite(in3, LOW);
        digitalWrite(in4, LOW);  
 
        delay(750);//bir üst fonksiyonun çalışma süresi
         
         // motorlar geriye dönüyor
         digitalWrite(in1, LOW);
         digitalWrite(in2, HIGH);  
         digitalWrite(in3, LOW);
         digitalWrite(in4, HIGH);
 
         delay(1750);//bir üst fonksiyonun çalışma süresi
 
         digitalWrite(in1, HIGH);
         digitalWrite(in2, LOW);
 
         delay(1750);//bir üst fonksiyonun çalışma süresi
 
      }
        //----------------------------------------------------
      if(distance2&lt;7 &amp;&amp; distance2 &gt;4)//sağ sensör
      {
        //sol motor
      digitalWrite(in1, HIGH);
      digitalWrite(in2, LOW);
      analogWrite(enA, 200);
 
      //sağ motor
      digitalWrite(in3, HIGH);
      digitalWrite(in4, LOW);
      analogWrite(enB, 130); // sağ motorun hızı arttırıldı
 
      delay(1500);
      }
 
      //------------------------------------------------------
      if(distance3&lt;7 &amp;&amp; distance3 &gt;4)//sol sensör
      {
 
      //sol motor
      digitalWrite(in1, HIGH);
      digitalWrite(in2, LOW);
      analogWrite(enA, 130);// sol motorun hızı arttırıldı
 
      //sağ motor
      digitalWrite(in3, HIGH);
      digitalWrite(in4, LOW);
      analogWrite(enB, 100); 
 
      delay(1500);
      }
 
      }
      //---------------------------------------------------
