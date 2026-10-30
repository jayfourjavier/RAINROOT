# Rain Root

## Description

Rain Root is a rainwater harvesting system with moisture-based drip irrigation. It collects rainwater in a tank for irrigating plants based on their moisture needs. An Arduino Mega reads the soil moisture sensors and activates peristaltic pumps when the soil moisture drops below a set threshold.

Each pot has its own moisture sensor and pump, allowing for precise watering based on the needs of each individual plant. The system is powered by a solar panel and a 3S3P 18650 Li-ion battery pack.

## Bill of Materials

| Item | Image | Description | Project Usage | Quantity | Product Link |
| ------ | ------- | ------------- | --------------- | ---------- | -------------- |
| Arduino Mega | <img src="assets/arduino-mega.png" width="400" height="400"> | Microcontroller board with many analog and digital I/O pins. | Main controller of the system. Reads the soil moisture sensors and switches the pumps through the relay module when moisture falls below the threshold. | 1 | [Buy here](https://s.shopee.ph/BUyGO9Zsj) |
| Protoboard 20x30cm | <img src="assets/protoboard.png" width="400" height="400"> | Large perforated prototyping board for soldered circuits. | Base for the permanent circuit: mounts the pinheaders and connects the Arduino, sensor lines, relay module, and power distribution. | 1 | [Buy here](https://s.shopee.ph/30p9dglv0M) |
| Male Pinheaders | <img src="assets/male-pinheaders.png" width="400" height="400"> | Single-row male connector strips. | Soldered on the protoboard to provide plug-in connection points for the Arduino and sensor/relay wiring. | 10 | [Buy here](https://s.shopee.ph/9fM3aDSnnm) |
| Female Pinheaders | <img src="assets/female-pinheaders.png" width="400" height="400"> | Single-row female socket strips. | Soldered on the protoboard as sockets so the Arduino and modules can be plugged in and removed without soldering. | 10 | [Buy here](https://s.shopee.ph/9fM3aDSnnm) |
| Analog Capacitive Soil Moisture Sensor | <img src="assets/soil-moisture-sensor.png" width="400" height="400"> | Corrosion-resistant sensor that outputs an analog voltage proportional to soil moisture. | One sensor per pot, wired to the Arduino analog inputs to measure each plant's soil moisture. | 4 | [Buy here](https://s.shopee.ph/AKbkNXKoe8) |
| 16 Channel Relay Module | <img src="assets/relay-module-16ch.png" width="400" height="400"> | Board of 16 relays that switch high-current loads from low-power logic signals. | Controlled by the Arduino to turn each peristaltic pump on and off; spare channels are available for expansion. | 1 | [Buy here](https://s.shopee.ph/4VdxQsOQWw) |
| 18650 Battery Cells | <img src="assets/battery-18650.png" width="400" height="400"> | Rechargeable 18650 Li-ion cells for energy storage. | Battery bank (9 cells, 3S3P) that stores solar energy and powers the Arduino, relay module, and pumps, including when there is no sunlight. | 9 | [Buy here](https://s.shopee.ph/8VA6CHpZXr) |
| 3S 20A BMS | <img src="assets/bms-3s-20a.png" width="400" height="400"> | Battery management system for 3-series Li-ion packs with cell balancing and overcharge, over-discharge, and short-circuit protection. | Connected between the 18650 cells and the charge controller to balance the 3 series groups and protect the pack. | 1 | [Buy here](https://s.shopee.ph/3g4qRRxtNY) |
| Solar Panel 100W (980mm x 530mm x 30mm) | <img src="assets/solar-panel-100w.png" width="400" height="400"> | Photovoltaic panel that converts sunlight into electricity. | Primary power source; charges the battery bank through the charge controller. | 1 | [Buy here](https://s.shopee.ph/1BNVSxuGnu) |
| Galvanized Iron Tubular Steel (20mm x 20mm) | <img src="assets/galvanized-iron-tubular-steel.png" width="400" height="400"> | Square tubular steel for the support frame. | Used to construct the Rain Root frame. | As required | |
| Orange Sanitary PVC Pipe (3" 3 meters) | <img src="assets/pvc-pipe-3-inch.png" width="400" height="400"> | Orange 3-inch sanitary PVC pipe. | Forms the gutter that collects rainwater from the solar panel and directs it toward the tank. | 1 | |
| 90-degree PVC Elbow (3-inch) | <img src="assets/pvc-elbow-90-3-inch.png" width="400" height="400"> | 90-degree elbow fitting for 3-inch PVC pipe. | Directs rainwater from the gutter toward the tank. | 3 | |
| PVC End Cap (3-inch) | <img src="assets/pvc-end-cap-3-inch.png" width="400" height="400"> | End cap for 3-inch PVC pipe. | Closes the end of the rainwater gutter. | 1 | |
| PWM Solar Charge Controller | <img src="assets/pwm-charge-controller.png" width="400" height="400"> | Regulates solar panel output to charge a battery safely using PWM. | Placed between the solar panel and battery bank to prevent overcharging and protect the batteries. | 1 | [Buy here](https://s.shopee.ph/1BNVT2gUjz) |
| XL4015 Buck Converter | <img src="assets/xl4015-buck-converter.png" width="400" height="400"> | Adjustable DC-DC step-down converter (up to 5A). | Steps the battery voltage down to regulated 5V for the Arduino, sensors, and relay-module logic. The pumps receive battery power through the relay contacts. | 1 | [Buy here](https://s.shopee.ph/7AeicFrMbw) |
| Peristaltic Pump | <img src="assets/peristaltic-pump.png" width="400" height="400"> | Pump that moves liquid by compressing a flexible tube; self-priming and accurate. | One pump per pot, switched by the relay module to deliver measured water from the tank to the plant. | 4 | [Buy here](https://s.shopee.ph/4VdxRtbxPP) |
| Silicone Tubing | <img src="assets/silicone-tubing.png" width="400" height="400"> | Flexible, food-safe tubing. | Fitted to each peristaltic pump to carry water from the tank to the pot's drip outlet. | 4 | |
| Water Tank (50L 570mm x 300mm x 300mm) | <img src="assets/water-tank.png" width="400" height="400"> | Water storage tank for the irrigation system. | Stores rainwater collected for watering the plants. | 1 | [Buy here](https://s.shopee.ph/5q9L7JRwen) |
| Silicone Wire 22AWG | <img src="assets/silicone-wire-22awg.png" width="400" height="400"> | Thin, highly flexible heat-resistant wire. | Low-current signal wiring: sensor connections and Arduino-to-relay control lines. | 1 | [Buy here](https://s.shopee.ph/6AmBQVoPqb) |
| Silicone Wire 20AWG | <img src="assets/silicone-wire-20awg.png" width="400" height="400"> | Slightly thicker, flexible heat-resistant wire. | Power wiring: battery, buck converter, relay module, and pump connections. | 1 | [Buy here](https://s.shopee.ph/6AmBQVoPqb) |
| Waterproof ABS Enclosure (240mm x 160mm x 92mm) | <img src="assets/abs-enclosure.png" width="400" height="400"> | Sealed plastic housing that protects electronics from water and dust. | Two enclosures are mounted beneath the solar panel: one houses the electronics and battery, and the other houses the water pumps. | 2 | [Buy here](https://s.shopee.ph/LoOU0t4h9) |
| Soldering Wire | <img src="assets/soldering-wire.png" width="400" height="400"> | Tin alloy solder used to join electrical connections. | Used to solder the pinheaders and wire connections on the protoboard. | 1 | [Buy here](https://s.shopee.ph/9fM3bE0flr) |
| Soldering Iron | <img src="assets/soldering-iron.png" width="400" height="400"> | Heated tool for melting solder. | Used during assembly to solder the circuit on the protoboard and the wire joints. | 1 | [Buy here](https://s.shopee.ph/9KjDCjx3mV) |

## 3D Model

![Isometric 3D model of the Rain Root frame, solar panel, gutter, tank, and pots](assets/3d/ISO1.png)

The 100W solar panel is mounted at a 30-degree incline and also serves as the rainwater collector. Its dimensions are 980mm x 530mm x 30mm, as listed in the Bill of Materials. Rainwater runs into an orange 3-inch sanitary PVC pipe gutter and is directed to the tank using three 90-degree elbows; one end cap closes the gutter.

The frame is made from 20mm x 20mm galvanized iron tubular steel. Two waterproof enclosures sit beneath the solar panel and are accessible from the back of the frame. One enclosure houses the electronics and battery, and the other houses the water pumps. The peristaltic pumps draw water from the tank and deliver it to the pots through silicone hose.

### Model Views

| East | North | South |
| --- | --- | --- |
| <img src="assets/3d/EAST.png" width="300" alt="East view"> | <img src="assets/3d/NORTH.png" width="300" alt="North view"> | <img src="assets/3d/SOUTH.png" width="300" alt="South view"> |

| Top | West |
| --- | --- |
| <img src="assets/3d/TOP.png" width="300" alt="Top view"> | <img src="assets/3d/WEST.png" width="300" alt="West view"> |

## Flowchart

### Control Logic

```mermaid
flowchart TD
    START([Start]) --> INIT[Initialize pins and set moisture threshold]
    INIT --> RESET[Set pot number i = 1]
    RESET --> READ[/Read soil moisture sensor i on A0-A3/]
    READ --> DEC{Soil moisture below threshold?}
    DEC -- Yes --> ON[Turn ON relay i to start pump i]
    ON --> WAIT[Wait for watering duration]
    WAIT --> OFF[Turn OFF relay i to stop pump i]
    DEC -- No --> OFF
    OFF --> MORE{More pots? i less than 4}
    MORE -- Yes --> NEXT[Increment i]
    NEXT --> READ
    MORE -- No --> DELAY[Wait for next sampling interval]
    DELAY --> RESET
```

### Energy and Water Flow

```mermaid
flowchart LR
    RAIN([Rainfall]) --> COLLECT[Collect rainwater]
    COLLECT --> TANK[(Water tank)]
    TANK --> PUMPS[Peristaltic pumps x4]
    PUMPS --> TUBE[Silicone tubing and drip outlets]
    TUBE --> PLANTS([Plants in pots])

    SUN([Sunlight]) --> SP[Solar panel 100W]
    SP --> CC[PWM charge controller]
    CC <--> BMS[3S 20A BMS]
    BMS <--> BAT[(18650 battery cells 3S3P)]
    CC --> LOAD[Controller load output]
    LOAD --> BUCK[XL4015 buck converter 5V]
    BUCK --> MEGA[Arduino Mega]
    BUCK --> RLY[16 channel relay module]
    LOAD --> RLY
    SENS[/Soil moisture sensors x4/] --> MEGA
    MEGA --> RLY
    RLY --> PUMPS
```

## Circuit Diagram

![Rain Root circuit diagram](assets/circuit-diagram.svg)

### Pin Connections

| From | Terminal / Pin | To | Terminal / Pin |
| ---- | -------------- | -- | -------------- |
| Solar Panel | + / - | PWM Charge Controller | PV+ / PV- |
| Battery Cells (3S3P) | + / 2 / 1 / - | BMS | B+ / B2 / B1 / B- |
| BMS | P+ / P- | PWM Charge Controller | BAT+ / BAT- |
| PWM Charge Controller | LOAD+ / LOAD- | XL4015 Buck Converter | IN+ / IN- |
| XL4015 Buck Converter (5V) | OUT+ | Arduino Mega | 5V |
| XL4015 Buck Converter | OUT- | Arduino Mega | GND |
| XL4015 Buck Converter (5V) | OUT+ / OUT- | Relay Module | VCC / GND |
| Arduino Mega | 5V / GND | Soil Moisture Sensors 1-4 | VCC / GND |
| Soil Moisture Sensor 1 | AOUT | Arduino Mega | A0 |
| Soil Moisture Sensor 2 | AOUT | Arduino Mega | A1 |
| Soil Moisture Sensor 3 | AOUT | Arduino Mega | A2 |
| Soil Moisture Sensor 4 | AOUT | Arduino Mega | A3 |
| Arduino Mega | D3 | Relay Module | IN1 |
| Arduino Mega | D4 | Relay Module | IN2 |
| Arduino Mega | D5 | Relay Module | IN3 |
| Arduino Mega | D6 | Relay Module | IN4 |
| PWM Charge Controller | LOAD+ | Relay Module | COM1 to COM4 |
| Relay Module | NO1 / NO2 / NO3 / NO4 | Pump 1 / 2 / 3 / 4 | + |
| Pump 1 / 2 / 3 / 4 | - | PWM Charge Controller | LOAD- |

Notes:

- The 9 cells are assumed to be wired 3S3P (about 11.1V), and the pumps are assumed to be 12V. Adjust if your pack or pumps differ.
- The BMS must be a 3S type. Connect the cell balance leads (B-, B1, B2, B+) in order and verify cell voltages before connecting the BMS output; the charge controller connects only to the BMS P+ / P- output.
- Set the XL4015 output to 5V with a multimeter before connecting the Arduino and relay module.
- Many relay modules are active LOW, so the relay turns on when its input pin is driven LOW.
- All grounds (battery, buck converter, Arduino, relay module, sensors) must be common.

## Q&A

### Why use an Arduino Mega?

The Arduino Mega provides up to 16 analog inputs for the soil-moisture sensors.

### Why use a 16-channel relay module?

It provides one relay channel for each of up to 16 peristaltic pumps.

### Why use a 3S battery pack for 12V pumps?

A 3S battery pack provides a voltage suited to the 12V pumps.

### Why use a PWM solar charge controller instead of MPPT?

The PWM solar charge controller is less efficient than MPPT, but costs less and suits this low-power application.

### Why use one sensor and one pump per pot?

Each pot has its own sensor and pump so it can be monitored and watered individually.

### Why use silicone-insulated wire?

Silicone wire is flexible and beginner-friendly to solder.

### Why use a relay module?

The relay module lets the Arduino switch the pumps on and off.

### Why use an XL4015 buck converter?

The XL4015 steps the battery voltage down to 5V for the Arduino and control circuit.

### How do I set up the XL4015?

Apply input power, adjust the trim pots, and observe the display until it reads 5V and 5A.
