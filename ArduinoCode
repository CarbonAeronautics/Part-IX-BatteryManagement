float Voltage, Current, BatteryRemaining, BatteryAtStart; 
float CurrentConsumed=0;
float BatteryDefault=1300;
void battery_voltage(void) {
  Voltage=(float)analogRead(15)/62;
  Current=(float)analogRead(21)*0.089;
}
void setup() {
  digitalWrite(5, HIGH);
  battery_voltage();
  if (Voltage > 8.3) { digitalWrite(5, LOW);
      BatteryAtStart=BatteryDefault; } 
  else if (Voltage < 7.5) {
      BatteryAtStart=30/100*BatteryDefault ;} 
  else { digitalWrite(5, LOW);
      BatteryAtStart=(82*Voltage-580)/100* BatteryDefault; }  
}
void loop() {
  battery_voltage();
  CurrentConsumed=Current*1000*0.004/3600+ CurrentConsumed;
  BatteryRemaining=(BatteryAtStart- CurrentConsumed)/BatteryDefault*100;
  if (BatteryRemaining<=30) digitalWrite(5, HIGH); 
  else digitalWrite(5, LOW);
}
