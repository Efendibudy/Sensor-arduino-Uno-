# Sensor-arduino-Uno-
//sensor ultrasonik 
//Nama : Deni Efendi 
//kelas : TME D3 4C 
// Definisikan pin yang digunakan
const int trigPin = 9;
const int echoPin = 10;

// Definisikan variabel untuk menyimpan waktu
long duration;
int distance;

void setup() {
  // Inisialisasi pin
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);

  // Mulai komunikasi serial dengan kecepatan 9600 baud
  Serial.begin(9600);
}

void loop() {
  // Kirimkan pulsa ultrasonik
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  // Baca waktu pantulan gelombang ultrasonik
  duration = pulseIn(echoPin, HIGH);

  // Konversi waktu menjadi jarak dalam sentimeter
  distance = duration * 0.034 / 2;

  // Tampilkan jarak ke serial monitor
  Serial.print("Jarak: ");
  Serial.print(distance);
  Serial.println(" cm");

  // Tunggu sejenak sebelum mengukur lagi
  delay(1000);
}
