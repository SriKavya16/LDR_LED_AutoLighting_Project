# 🌙 Light-Activated LED System using LDR and Arduino

This is a beginner-friendly embedded systems project built with **Arduino Uno**, an **LDR (Light Dependent Resistor)**, and an **LED**.  
The system automatically turns the LED **ON in the dark** and **OFF in light**, simulating a basic **automatic streetlight**.

---

## 🔧 Components Used

- Arduino Uno R3
- LDR (Photoresistor)
- 10kΩ resistor (for voltage divider with LDR)
- 220Ω resistor (for LED current limiting)
- LED
- Breadboard and jumper wires
- Tinkercad Circuits (free simulation platform)

---

## 🔌 Circuit Connections

### 📷 Voltage Divider with LDR:
| LDR Pin | Connection |
|---------|------------|
| One leg | 5V         |
| Other leg | Analog pin A0 **and** one end of 10kΩ resistor |
| Other end of 10kΩ resistor | GND |

### 💡 LED Output Circuit:
| Component | Connection |
|----------|------------|
| **Pin 9 (Arduino)** → **220Ω resistor** → **Long leg (Anode) of LED** |
| **Short leg (Cathode) of LED** → **GND** |

> 📎 The resistor protects the LED by limiting the current.

---

## 💻 Arduino Code

```cpp
int ldrPin = A0;       // Light sensor pin
int ledPin = 9;        // LED output pin
int threshold = 500;   // Light threshold value

void setup() {
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int lightLevel = analogRead(ldrPin);
  Serial.print("Light level: ");
  Serial.println(lightLevel);

  if (lightLevel < threshold) {
    digitalWrite(ledPin, HIGH);  // It's dark, turn ON LED
  } else {
    digitalWrite(ledPin, LOW);   // It's bright, turn OFF LED
  }

  delay(1000); // 1 second delay
}
