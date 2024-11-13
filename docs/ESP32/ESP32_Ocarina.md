# ESP32 Ocarina

## 1. Projects

<span style="color: rgb(65, 104, 211);">**Before learning, please the kit has been assembled!**</span>

### 1.1 Capacitive Touch Module

![KS6013](img/KS6013.png)

There is a touch area on the capacitive touch sensor, which can be used as a replacement of traditional buttons, as shown below:

![1101](img/1101.png)

<span style="color: rgb(2, 167, 240);">**We can regard the sensor as a button. Touching the area means pressing the button.**</span>

After powering on, it takes about 0.5 seconds for stabilization. During this period, please do not touch this area, because all functions are disabled at this time and self-calibration is always carried out. The calibration period is about 4 seconds.

#### Schematic Diagram

![1102](img/1102.png)

TTP223N-BA6 is a touch pad detector IC that comes with a touch area. The touch detection IC, with various dimensions, can replace the traditional buttons. Its output mode is related to pins TOG and AHLB.

| TOG  | AHLB | Optional Function of Pin Q           |
| ---- | ---- | ------------------------------------ |
| 0    | 0    | Direct mode, available at high level |
| 0    | 1    | Direct mode, available at low level  |
| 1    | 0    | Trigger mode, power-on state is 0    |
| 1    | 1    | Trigger mode, power-on state is 1    |

From the Schematic Diagram, the pin TOG and AHLB are suspended, so the output of this module is direct mode which is available at high level.

When we touch the area on the module (equivalent to pressing the button), the signal S outputs high and the on-board red LED lights up. We can determine whether the capacitive touch module is working by reading the power level of S terminal.


------

#### Parameters

- Operating voltage: DC 3.3 / 5V
- Maximum power: 0.3 W
- Operating temperature: -10°C ~ +50°C
- Output signal: digital signal
- Dimensions: 32 x 24 x 7.3 mm
- Positioning hole: diameter of 4.8 mm
- Interface: 3 pin spacing 2.54 mm

---

#### Wiring Diagram 1

<span style="color: rgb(2, 167, 240);">**NOTE:**</span>

| Expansion board pin color | Wire color          | Module terminal |
| ------------------------- | ------------------- | :-------------: |
| ![e-b](img/e-b.png)       | ![p-b](img/p-b.png) | ![g](img/g.png) |
| ![e-r](img/e-r.png)       | ![p-r](img/p-r.png) | ![v](img/v.png) |
| ![e-y](img/e-y.png)       | ![p-y](img/p-y.png) | ![s](img/s.png) |

![1103](img/1103.png)

------
#### Test Code 1

Open KidsBlock and connect the board to your computer. Click **File --> Load from your computer**.

![code1](img/code1.png)

Open code **1.1_1 Capacitive Touch Module.sb3**.

Click ![code2](img/code2.png) to connect to port, and then ![code3](img/code3.png) the Test Code.



- Initialization: Set pin mode; initialize serial port and RGB.

  Set pin IO14 to input mode.

  ![1104](img/1104.png)

  ![1105](img/1105.png)

  

  Set baud rate to 115200.

  ![1106](img/1106.png)

  

  Initialize RGB.

  ![1107](img/1107.png)

  

- Loop: Determine whether the area is touched. Touch the area (press the button) to output high 1.

  Build code blocks as follows:

  ![1108](img/1108.png)

  ![1109](img/1109.png)

  

  Build code blocks as follows, and set a condition: pin IO14 outputs value 1.

  ![1110](img/1110.png)

  ![1111](img/1111.png)
  
  
  
- Pressed: ESP32 Easy Coding Board shows a big heart.

  Build code blocks as follows, and adjust the brightness and color of the heart. Click the little square to light up the corresponding RGB.

  ![1112](img/1112.png)

  

- Not pressed: ESP32 Easy Coding Board shows a small heart.

  Click the code block to choose **Duplicate**.

  ![1113](img/1113.png)

  As follows:

  ![1114](img/1114.png)

  Modify the heart icon.

  ![1115](img/1115.png)

  

- Complete Test Code

  ![1116](img/1116.png)

------

#### Test Result 1

Press the button, and ESP32 Easy Coding Board shows a large heart.

![1118](img/1118.png)

Release the button, and ESP32 Easy Coding Board displays a small heart.

![1117](img/1117.png)

---

#### Wiring Diagram 2

<span style="color: rgb(2, 167, 240);">**NOTE:**</span>

| Expansion board pin color | Wire color          | Module terminal |
| ------------------------- | ------------------- | :-------------: |
| ![e-b](img/e-b.png)       | ![p-b](img/p-b.png) | ![g](img/g.png) |
| ![e-r](img/e-r.png)       | ![p-r](img/p-r.png) | ![v](img/v.png) |
| ![e-y](img/e-y.png)       | ![p-y](img/p-y.png) | ![s](img/s.png) |

![1119](img/1119.png)

---

#### Test Code 2

Open KidsBlock and connect the board to your computer. Click **File --> Load from your computer**.

![code1](img/code1.png)

Open code **1.1_2 4 keys.sb3**.

Click ![code2](img/code2.png) to connect to port, and then ![code3](img/code3.png) the Test Code.



- Initialization: Set pin mode; initialize serial port and RGB.

  Set pin to input mode.

  ![1120](img/1120.png)

  

  Set baud rate to 115200.
  
  ![1121](img/1121.png)
  
  
  
  Initialize RGB.
  
  ![1122](img/1122.png)
  
  
  
  Create four variables: sw1, sw2, sw3, sw4, used to record the number of times of pressing button.
  
  ![1123](img/1123.png)
  
  
  
- Press the button for the first time, and the dot matrix shows 1. Press the button again to clear the dot matrix. 

  Eliminate the button jitters.

  ![1124](img/1124.png)

  

  Each time press the button, and the variable sw1 adds one. Meanwhile, zero out other three variables.

  ![1125](img/1125.png)

  

  When the remainder of "variable sw1 divided by 2" equals 1 (this means sw1 is odd), the dot matrix shows number 1.

  ![1126](img/1126.png)

  ![1127](img/1127.png)

  ![1128](img/1128.png)

  

  When the remainder of "variable sw1 divided by 2" is not 1 (this means sw1 is even), the dot matrix goes off.

  ![1129](img/1129.png)

  

- Similarly, set sw2:

  ![1130](img/1130.png)

  

- sw3:

  ![1131](img/1131.png)

  

- sw4:

  ![1132](img/1132.png)

  

- Complete Test Code:

  ![1133](img/1133.png)



---

#### Test Result 2

Press the button and the dot matrix shows corresponding numbers. Press the button again and the dot matrix is cleared.

------

### 1.2 Sound Sensor

![KS6027](img/KS6027.png)

The sound sensor can be regarded as a microphone, which consists of a sensitive capacitive microphone for detecting sound and an amplification circuit.

The sound sensor captures ambient sound due to sound propagation and vibration. When sound travels near the sensor, the sound wave causes the sensor to vibrate. A device inside the sensor converts these vibrations into electrical signals, which are sent to other devices for further processing or analysis.

#### Schematic Diagram

![1201](img/1201.png)

The sound sensor is composed of a high-sensitivity microphone and the LM386 audio power amplifier chip. The former detects the ambient sounds, and the latter amplifies detected sounds.

Rotate the potentiometer on the sensor to adjust the magnification of the amplification. Rotate it clockwise to the end, and the magnification is the largest.

------

#### Wiring Diagram

<span style="color: rgb(2, 167, 240);">**NOTE:**</span>

| Expansion board pin color | Wire color          | Module terminal |
| ------------------------- | ------------------- | :-------------: |
| ![e-b](img/e-b.png)       | ![p-b](img/p-b.png) | ![g](img/g.png) |
| ![e-r](img/e-r.png)       | ![p-r](img/p-r.png) | ![v](img/v.png) |
| ![e-y](img/e-y.png)       | ![p-y](img/p-y.png) | ![s](img/s.png) |

![1202](img/1202.png)

------

#### Parameters

- Operating voltage: DC 3.3 / 5V 
- Current: 15 mA
- Maximum power: 0.075 W
- Operating temperature: -10°C ~ +50°C
- Dimensions: 32 x 24 x 11 mm
- Positioning hole: diameter of 4.8 mm
- Interface: 3 pin spacing 2.54 mm

---

#### Test Code 

Open KidsBlock and connect the board to your computer. Click **File --> Load from your computer**.

![code1](img/code1.png)

Open code **1.2 Sound Sensor.sb3**.

Click ![code2](img/code2.png) to connect to port, and then ![code3](img/code3.png) the Test Code.



- Initialization: set pin mode and initialize serial port.

  ![1203](img/1203.png)

  

- Print the read analog values on the serial monitor.

  Build code blocks as follows:

  ![1204](img/1204.png)

  Modify the content into *value_voice：* and choose no-wrap printing.

  ![1205](img/1205.png)

  Build code blocks as follows to print the analog value input by pin IO32 on the serial monitor.

  ![1206](img/1206.png)

  ![1207](img/1207.png)

  

- Delay 0.1s after each time the value is read.

  ![1208](img/1208.png)

  

- Complete Test Code

  ![1209](img/1209.png)
  
  

#### Test Result 

<span style="color: rgb(2550, 10, 50);">NOTE: Before uploading code, please set baud rate first. Or else, garbled words may be shown on the monitor.</span>

Click ![Baud1](img/Baud1.png) to set Buadrate to 115200.

![Baud2](img/Baud2.png)

After uploading the code, speak to the MIC. You will see the serial monitor displays the analog values of the sounds converted by the sensor.

![1210](img/1210.png)

------

### 1.3 Passive Buzzer Module

![KS6011](img/KS6011.png)

Buzzer is an integrated structure of electronic sound device, which is powered by DC voltage. In application, it is widely used in computers, printers, copiers, alarms, electronic toys, automotive electronic equipment, telephones and timers. 

Buzzers can be divided into active ones(built-in drive circuits) and passive ones(external drive) according to that whether they includes an excitation source.

Active buzzers contain oscillation source inside, which can sound at a fixed frequency once be triggered. They are convenient in program control and features high sound pressure.

Passive ones, however, do not include oscillating sources. If we directly power a passive buzzer via DC voltage, it will emit no sound. According to needs, we generally drive through square waves, whose frequency determines the sound tones.

-------------------

#### Schematic Diagram

![1301](img/1301.png)

Passive buzzer works on the basis of electromagnetic induction, and it is composed of an electromagnetic coil and a vibration sheet. When an electric current passes through the coil, the resulting magnetic field attracts the sheet to vibrate, thus producing sounds. 

The passive buzzer requires an external circuit is required to provide AC signals to emit sound, as they do not integrates oscillating circuits. By controlling the frequency of the AC signals, the tone of the sound can also be changed.

![1303](img/1303.png)

The foundation of music, as we all know, is note. We can compose a variety of melodies and rhythms with different notes. Of all the notes, the most basic are seven: C, D, E, F, G, A, B.

We can compose a variety of melodies and rhythms with these notes.



In the code, there are blocks of notes with three pitches. You can directly drag them to use.

![1307](img/1307.png)

---

#### Wiring Diagram 

<span style="color: rgb(2, 167, 240);">**NOTE:**</span>

| Expansion board pin color | Wire color          | Module terminal |
| ------------------------- | ------------------- | :-------------: |
| ![e-b](img/e-b.png)       | ![p-b](img/p-b.png) | ![g](img/g.png) |
| ![e-r](img/e-r.png)       | ![p-r](img/p-r.png) | ![v](img/v.png) |
| ![e-y](img/e-y.png)       | ![p-y](img/p-y.png) | ![s](img/s.png) |

![1302](img/1302.png)

---

#### Parameters

- Operating voltage: DC 3.3 / 5V 
- Operating temperature: -10°C ~ +50°C
- Dimensions: 32 x 24 x 11.5 mm
- Positioning hole: diameter of 4.8 mm
- Interface: 3 pin spacing 2.54 mm

---

#### Test Code 

Open KidsBlock and connect the board to your computer. Click **File --> Load from your computer**.

![code1](img/code1.png)

Open code **1.3 Passive Buzzer.sb3**.

Click ![code2](img/code2.png) to connect to port, and then ![code3](img/code3.png) the Test Code.



- Set tones.

  Build code blocks as follows, and set pins, tones and beats.

  ![1304](img/1304.png)

  Click the code block to choose **Duplicate**. Duplicate six blocks and modify their tones.

  ![1305](img/1305.png)

  

- Complete Test Code

  ![1306](img/1306.png)

---

#### Test Result 

The passive buzzer repeatedly plays the set tones.

------

### 1.4 Play The Ocarina

![1401](img/1401.png)

The Ocarina, a worldwide instrument, belongs to any nations. All countries and regions have experienced long or short pottery times documentarily, or learn from each other to reform and develop pottery flutes.

According to the number of holes, ocarinas can be divided into 4 holes, 5 holes, 6 holes, 7 holes, 8 holes, 9 holes, 10 holes, 11 holes, 12 holes, and even 17 holes or more. The most common ones are 6 and 12 holes.

![1402](img/1402.png)

**How to play the ocarina**: 

Your index and middle fingers should be on the holes of the top side. Your ring finger gently holds its bottom to prevent it from falling. Gently cover holes with your finger abdomen rather than fingertips, please do not use too much force. The rest of your fingers should go over the remaining holes.

In this project, we will build a four-hole ocarina. Let's learn how to play!

---

#### Principle

![1412](img/1412.png)

In this project, we build a simulated ocarina with touch sensors, a sound sensor and structural basswood board. 

In this structure, the sound sensor is equivalent to the mouthpiece and windway of an ocarina. Blow into the sound sensor and the output analog value will increase. 

Toneholes are replaced with capacitive touch sensors. High level will output when you touch these sensors.

The passive buzzer plays corresponding tones according to different finger models. The following diagram is the relationship between tones and finger models.

![1411](img/1411.png)

Pin numbers:

![1413](img/1413.png)

Press the certain touch sensor(s) and blow into the sound sensor, and the passive buzzer will emit sounds of corresponding tones.

------

#### Test Code

Open KidsBlock and connect the board to your computer. Click **File --> Load from your computer**.

![code1](img/code1.png)

Open code **1.4 Ocarina.sb3**.

Click ![code2](img/code2.png) to connect to port, and then ![code3](img/code3.png) the Test Code.



- Initialization: initialize the serial port and set pin mode.

  ![1403](img/1403.png)

- Print the analog value read by pin IO32 on the serial monitor. The results refresh every 0.1s.

  ![1404](img/1404.png)

- Blow into the mouthpiece (the sound sensor).

  ![1405](img/1405.png)

- At the same time, determine the finger models. And the buzzer will emit sounds of corresponding tones.

  “DO”: Press all toneholes (touch sensors).

  ![1406](img/1406.png)

  

  “RE”: Press toneholes (touch sensors) 1, 3, 4 at the same time.
  
  ![1407](img/1407.png)
  
  
  
  “Mi”: Press toneholes (touch sensors) 1, 2, 3 at the same time.
  
  ![1408](img/1408.png)
  
  
  
  Similarly, set other tones.
  
  ![1409](img/1409.png)
  
  


- Complete Test Code

  ![1410](img/1410.png)

---

#### Test Result 

Press the certain touch sensor(s) and blow into the sound sensor, and the passive buzzer will emit sounds of corresponding tones.

------

## 2. FAQ

### Q: Battery model?

A: Four AAA batteries. Please install the batteries in the correct direction rather than reverse them! For younger students, please be accompanied by your parents!

![0201](img/0201.png)

![0202](img/0202.png)

------



### Q: Errors occur when ESP32 burns code?

A: 

- Please check whether the USB port number is correct.
- Please ensure the main board model is available. 

------



### Q: Expand to external modules?

A: It can expand to external modules. For details, please follow the ESP32 pin instructions to ensure external modules can normally work.

------



## 3. Resources

Keyestudio official:

[https://www.keyestudio.com/](https://www.keyestudio.com/)

Keyestudio wiki main page:

[https://wiki.keyestudio.com/Main_Page](https://www.keyestudio.com/)

ESP32 development board details:

<http://keyestudio-ks0579.readthedocs.io/>

Arduino official:

[https://www.arduino.cc/](https://www.keyestudio.com/)

ESP32 espressif official:

[https://www.espressif.com/](https://www.keyestudio.com/)