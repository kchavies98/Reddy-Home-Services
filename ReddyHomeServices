int living_room_switch = 4;
int living_room_light = 3;
int entry_light = A1;
int kitchen_light = 7;
int kitchen_switch = 6;
int bedroom_light = 5;
int bedroom_switch = 8;
int hallway_light = A4;
int hallway_switch = 2;
int buzz_switch = A0;
int buzz_sound = A2;



boolean buttonOn = false;
boolean living_room_on = false;
boolean entry_on = false;
boolean kitchen_on = false;
boolean bedroom_on = false;
boolean hallway_on = false;
boolean bathroom_on = false;
int sensorState = 0;
int buttonState = 0;
int previousEntry = 0;
int previousLivingRoom = 0;
int previousKitchen = 0;
int previousBedroom = 0;
int previousHallway = 0;
int previousBathroom = 0;
long stime = 0;
long debounce = 1000;

void setup() {
  Serial.begin(9600);

  //code for doorbell
  pinMode(buzz_switch, INPUT);
  pinMode(buzz_sound, OUTPUT);

  //code for living room light
  pinMode(living_room_switch, INPUT);
  pinMode(living_room_light, OUTPUT);

  //code for kitchen light
  pinMode(kitchen_switch, INPUT);
  pinMode(kitchen_light, OUTPUT);

  //code for entry light
  pinMode(entry_light, OUTPUT);

  //code for bedroom light
  pinMode(bedroom_switch, INPUT);
  pinMode(bedroom_light, OUTPUT);

  //code for hallway light
  pinMode(hallway_switch, INPUT);
  pinMode(hallway_light, OUTPUT);
}

void loop()
{
  // entry light ------ walking through "front door"
  // if entry sensor is off/not triggered
  int buttonState = digitalRead(buzz_switch);
  if (buttonState == HIGH)
  {
    digitalWrite(buzz_sound, HIGH);
  }
  else
  {
    digitalWrite(buzz_sound, LOW);
  }

  if (buttonState == HIGH && previousEntry == LOW && millis() - stime > debounce)
  {
    if (entry_on)
    {
      digitalWrite(entry_light, LOW);
      entry_on = false;
    }
    else
    {
      digitalWrite(entry_light, HIGH);
      entry_on = true;
    }
  }

  previousEntry = buttonState; //previous status for entry sensor is HIGH if light turned on/ LOW if light did not turn on

  // living room light ---- walking from entry to living room
  // if living room sensor is off/not triggered

  sensorState = digitalRead(living_room_switch);
  if (sensorState == HIGH && previousLivingRoom == LOW && millis() - stime > debounce)
  {
    if (living_room_on)
    {
      digitalWrite(living_room_light, LOW);
      living_room_on = false;
      digitalWrite(entry_light, HIGH);
    }
    else
    {
      digitalWrite(living_room_light, HIGH);
      living_room_on = true;
      digitalWrite(entry_light, LOW);
    }
  }

  previousLivingRoom = sensorState;

  sensorState = digitalRead(kitchen_switch);
  if (sensorState == HIGH && previousKitchen == LOW && millis() - stime > debounce)
  {
    if (kitchen_on)
    {
      digitalWrite(kitchen_light, LOW);
      kitchen_on = false;
      digitalWrite(living_room_light, HIGH);
    }
    else
    {
      digitalWrite(kitchen_light, HIGH);
      kitchen_on = true;
      digitalWrite(living_room_light, LOW);
    }
  }

  previousKitchen = sensorState; // previous status for LIVING ROOM sensor is HIGH if light turned on/ LOW if light did not turn on

  sensorState = digitalRead(bedroom_switch);
  if (sensorState == HIGH && previousKitchen == LOW && millis() - stime > debounce)
  {
    if (bedroom_on)
    {
      digitalWrite(bedroom_light, LOW);
      bedroom_on = false;
      digitalWrite(kitchen_light, HIGH);
    }
    else
    {
      digitalWrite(bedroom_light, HIGH);
      bedroom_on = true;
      digitalWrite(kitchen_light, LOW);
    }
  }

  previousBedroom = sensorState; // previous status for LIVING ROOM sensor is HIGH if light turned on/ LOW if light did not turn on


  sensorState = digitalRead(hallway_switch);
  if (sensorState == HIGH && previousBedroom == LOW && millis() - stime > debounce)
  {
    if (hallway_on)
    {
      digitalWrite(hallway_light, LOW);
      hallway_on = false;
      digitalWrite(bedroom_light, HIGH);
    }
    else
    {
      digitalWrite(hallway_light, HIGH);
      hallway_on = true;
      digitalWrite(bedroom_light, LOW);
    }
  }

  previousHallway = sensorState; // previous status for LIVING ROOM sensor is HIGH if light turned on/ LOW if light did not turn on

}
