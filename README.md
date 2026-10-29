# Rain Root

## Bill of Materials

| Item | Image | Description | Project Usage | Quantity | Product Link |
| ------ | ------- | ------------- | --------------- | ---------- | -------------- |
| Arduino Mega | <img src="assets/arduino-mega.png" width="80"> | Microcontroller board with many analog and digital I/O pins. | Main controller of the system. Reads the soil moisture sensors and switches the pumps through the relay module when moisture falls below the threshold. | 1 | |
| Protoboard 20x30cm | <img src="assets/protoboard.png" width="80"> | Large perforated prototyping board for soldered circuits. | Base for the permanent circuit: mounts the pinheaders and connects the Arduino, sensor lines, relay module, and power distribution. | 1 | |
| Male Pinheaders | <img src="assets/male-pinheaders.png" width="80"> | Single-row male connector strips. | Soldered on the protoboard to provide plug-in connection points for the Arduino and sensor/relay wiring. | 10 | |
| Female Pinheaders | <img src="assets/female-pinheaders.png" width="80"> | Single-row female socket strips. | Soldered on the protoboard as sockets so the Arduino and modules can be plugged in and removed without soldering. | 10 | |
| Analog Capacitive Soil Moisture Sensor | <img src="assets/soil-moisture-sensor.png" width="80"> | Corrosion-resistant sensor that outputs an analog voltage proportional to soil moisture. | One sensor per pot, wired to the Arduino analog inputs to measure each plant's soil moisture. | 4 | |
| 16 Channel Relay Module | <img src="assets/relay-module-16ch.png" width="80"> | Board of 16 relays that switch high-current loads from low-power logic signals. | Controlled by the Arduino to turn each peristaltic pump on and off; spare channels are available for expansion. | 1 | |
| LiPo Battery 18650 | <img src="assets/battery-18650.png" width="80"> | Rechargeable 18650 cells for energy storage. | Battery bank (9 cells) that stores solar energy and powers the Arduino, relay module, and pumps, including when there is no sunlight. | 9 | |
| Solar Panel 100W | <img src="assets/solar-panel-100w.png" width="80"> | Photovoltaic panel that converts sunlight into electricity. | Primary power source; charges the battery bank through the charge controller. | 1 | |
| PWM Solar Charge Controller | <img src="assets/pwm-charge-controller.png" width="80"> | Regulates solar panel output to charge a battery safely using PWM. | Placed between the solar panel and battery bank to prevent overcharging and protect the batteries. | 1 | |
| XL4015 Buck Converter | <img src="assets/xl4015-buck-converter.png" width="80"> | Adjustable DC-DC step-down converter (up to 5A). | Steps the battery voltage down to the regulated voltage required by the Arduino, relay module, and pumps. | 1 | |
| Peristaltic Pump | <img src="assets/peristaltic-pump.png" width="80"> | Pump that moves liquid by compressing a flexible tube; self-priming and accurate. | One pump per pot, switched by the relay module to deliver measured water from the tank to the plant. | 4 | |
| Silicone Tubing | <img src="assets/silicone-tubing.png" width="80"> | Flexible, food-safe tubing. | Fitted to each peristaltic pump to carry water from the tank to the pot's drip outlet. | 4 | |
| Silicone Wire 22AWG | <img src="assets/silicone-wire-22awg.png" width="80"> | Thin, highly flexible heat-resistant wire. | Low-current signal wiring: sensor connections and Arduino-to-relay control lines. | 1 | |
| Silicone Wire 20AWG | <img src="assets/silicone-wire-20awg.png" width="80"> | Slightly thicker, flexible heat-resistant wire. | Power wiring: battery, buck converter, relay module, and pump connections. | 1 | |
| Waterproof ABS Enclosure | <img src="assets/abs-enclosure.png" width="80"> | Sealed plastic housing that protects electronics from water and dust. | Houses the Arduino, protoboard, relay module, and power electronics, protecting them from rain and moisture outdoors. | 1 | |
| Soldering Wire | <img src="assets/soldering-wire.png" width="80"> | Tin alloy solder used to join electrical connections. | Used to solder the pinheaders and wire connections on the protoboard. | 1 | |
| Soldering Iron | <img src="assets/soldering-iron.png" width="80"> | Heated tool for melting solder. | Used during assembly to solder the circuit on the protoboard and the wire joints. | 1 | |

## Description

Rain Root rainwater harvesting system with moisture based drip irrigation system. The system is designed to collect rainwater and store it in a tank, which can then be used to irrigate plants based on their moisture needs. The system uses an Arduino Mega to control the irrigation process, with soil moisture sensors to monitor the moisture levels of the soil. When the soil moisture drops below a certain threshold, the system activates peristaltic pumps to deliver water to the plants.

Each pot has its own moisture sensor and pump, allowing for precise watering based on the needs of each individual plant. The system is powered by a solar panel and a LiPo battery, making it energy-efficient and environmentally friendly.

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
    CC --> BAT[(18650 battery bank)]
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

```mermaid
flowchart LR
    subgraph SOLAR["Solar Charging"]
        SP["Solar Panel 100W"]
        CC["PWM Charge Controller"]
        BAT["Battery Bank<br/>9x 18650, 3S3P, about 11.1V"]
        BUCK["XL4015 Buck Converter<br/>set to 5V"]
    end

    subgraph MEGA["Arduino Mega"]
        V5["5V"]
        GND["GND"]
        A0["A0"]
        A1["A1"]
        A2["A2"]
        A3["A3"]
        D3["D3"]
        D4["D4"]
        D5["D5"]
        D6["D6"]
    end

    subgraph SENSORS["Capacitive Soil Moisture Sensors"]
        S1["Sensor 1"]
        S2["Sensor 2"]
        S3["Sensor 3"]
        S4["Sensor 4"]
    end

    subgraph RELAY["16 Channel Relay Module"]
        RVCC["VCC"]
        RGND["GND"]
        IN1["IN1"]
        IN2["IN2"]
        IN3["IN3"]
        IN4["IN4"]
        K1["CH1 COM / NO"]
        K2["CH2 COM / NO"]
        K3["CH3 COM / NO"]
        K4["CH4 COM / NO"]
    end

    subgraph PUMPS["Peristaltic Pumps"]
        P1["Pump 1"]
        P2["Pump 2"]
        P3["Pump 3"]
        P4["Pump 4"]
    end

    %% Solar charging
    SP -- "+ to PV+" --> CC
    SP -- "- to PV-" --> CC
    CC -- "BAT+ to Battery +" --> BAT
    CC -- "BAT- to Battery -" --> BAT

    %% Regulated 5V supply
    CC -- "LOAD+ to IN+" --> BUCK
    CC -- "LOAD- to IN-" --> BUCK
    BUCK -- "OUT+ to 5V" --> V5
    BUCK -- "OUT- to GND" --> GND
    BUCK -- "OUT+ to VCC" --> RVCC
    BUCK -- "OUT- to GND" --> RGND

    %% Sensors
    V5 -- "VCC" --> S1 & S2 & S3 & S4
    GND -- "GND" --> S1 & S2 & S3 & S4
    S1 -- "AOUT" --> A0
    S2 -- "AOUT" --> A1
    S3 -- "AOUT" --> A2
    S4 -- "AOUT" --> A3

    %% Relay control signals
    D3 -- "signal" --> IN1
    D4 -- "signal" --> IN2
    D5 -- "signal" --> IN3
    D6 -- "signal" --> IN4

    %% Pump power switched by relays
    CC -- "LOAD+ to COM1-COM4" --> K1 & K2 & K3 & K4
    K1 -- "NO1 to +" --> P1
    K2 -- "NO2 to +" --> P2
    K3 -- "NO3 to +" --> P3
    K4 -- "NO4 to +" --> P4
    P1 & P2 & P3 & P4 -- "- to LOAD-" --> CC
```

### Pin Connections

| From | Terminal / Pin | To | Terminal / Pin |
| ---- | -------------- | -- | -------------- |
| Solar Panel | + / - | PWM Charge Controller | PV+ / PV- |
| Battery Bank | + / - | PWM Charge Controller | BAT+ / BAT- |
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
- Set the XL4015 output to 5V with a multimeter before connecting the Arduino and relay module.
- Many relay modules are active LOW, so the relay turns on when its input pin is driven LOW.
- All grounds (battery, buck converter, Arduino, relay module, sensors) must be common.
