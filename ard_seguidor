/*

Pinagem motores:
pino 3 = (Motor 1 avante)
pino 2 = (Motor 1 reverso)
pino 6 = (Motor 2 avante)
pino 7 = (Motor 2 reverso)

Pinagem sensores:
pino A0 = (Sensor 0)
pino A1 = (Sensor 1)
pino A2 = (Sensor 2)
pino A3 = (Sensor 3)
pino A4 = (Sensor 4)

pino 10 = HM (Habilita Motor 1)
pino 5 = HM (Habilita Motor 2)

*/

//============== NOMEAR PINOS ===============
//=========== INCLUIR BIBLIOTECAS ===========
//=========== VARIÁVEIS E TABELAS ===========
int e2, e1, c, d2, d1; 
//================ SUB-ROTINAS ==============
//================= FUNÇÕES =================
void leitura(){
  e2 = map(analogRead(A4), 0, 1023, 0, 500);
  e1 = map(analogRead(A3), 0, 1023, 0, 500);
  c = map(analogRead(A2), 0, 1023, 0, 500);
  d1 = map(analogRead(A1), 0, 1023, 0, 500);
  d2 = map(analogRead(A0), 0, 1023, 0, 500);
}

int frente(int vel){
  digitalWrite(3, HIGH);
  digitalWrite(2, LOW);
  digitalWrite(6, HIGH);
  digitalWrite(7, LOW);
  Serial.println("Frente");
  analogWrite(5, vel);
  analogWrite(10, vel);
}

void parar(){
  digitalWrite(3, LOW);
  digitalWrite(6, LOW);
  digitalWrite(2, HIGH);
  digitalWrite(7, HIGH);
  analogWrite(5, 0);
  analogWrite(10, 0);
  Serial.println("Parar");
}

int esquerda(int vel){
	digitalWrite(3, HIGH);
    digitalWrite(6, HIGH);
    digitalWrite(2, LOW);
    digitalWrite(7, LOW);
	analogWrite(5, vel);
    analogWrite(10, 0);
  	Serial.println("Esquerda");
}

int direita(int vel){
	digitalWrite(3, HIGH);
    digitalWrite(6, HIGH);
    digitalWrite(2, LOW);
    digitalWrite(7, LOW);
	analogWrite(10, vel);
    analogWrite(5, 0);
  Serial.println("Direita");
}

//================== SETUP ==================
void setup() {  
  pinMode(9, OUTPUT);
  pinMode(7, OUTPUT);
  pinMode(6, OUTPUT);
  pinMode(5, OUTPUT);
  pinMode(10, OUTPUT);
  pinMode(3, OUTPUT);
  pinMode(2, OUTPUT);
  pinMode(A0, INPUT);
  pinMode(A1, INPUT);
  pinMode(A2, INPUT);
  pinMode(A3, INPUT);
  pinMode(A4, INPUT);

//---------- CONDIÇÕES INICIAIS ----------
  digitalWrite(3, LOW);
  digitalWrite(2, LOW);
  digitalWrite(6, LOW);
  digitalWrite(7, LOW);
  Serial.begin(10);
}//fecha void setup()


//============== LOOP INFINITO ===============
void loop() {
  
  //lê os sensores
  leitura();
  
  //frente
  if(e2<250 && d2<250 && e1<497 && e1>250 && d1<497 && d1>250 && c>=497){    
    frente(200);
  }
  //virar a esquerda
  else if(e2<497 && e2>250 && e1>=497 && d1<=250 && d2<=168){
    esquerda(200);
  }
  //virar a direita
  else if(d2<497 && d2>250 && d1>=497 && e1<=250 && e2<=168){
    direita(200);
  }   
  //parar
  else/*(d2>=497 && e2>=497 && e1>=497 && d1>=497 && c>=497)*/{    
    parar();
  }
  
  Serial.println("esquerdo 2:");
  Serial.println(e2);
  Serial.println("esquerdo 1:");
  Serial.println(e1);
  Serial.println("centrao:");
  Serial.println(c);
  Serial.println("direito 1:");
  Serial.println(d1);
  Serial.println("direito 2:");
  Serial.println(d2);


}//fecha void loop()
