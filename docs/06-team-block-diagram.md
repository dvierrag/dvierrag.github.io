---
title:  Block Diagram
---

## Introduction

The PCB board functions as a motor controller system that operates a DC motor through a PIC18F57Q43 Curiosity Nano microcontroller. The H-Bridge component FAN8100N receives motor control signals from the microcontroller to operate the M1N10FB11G motor. The microcontroller operates the motor through digital signals sent from pins RA1 and RD0 and RD1.

The board features an input connector which enables future sensor integration and digital and analog signal reception. The PCB serves as a basic solution for embedded system developers to evaluate and manage motor operations through its straightforward design.

## Research Question

* Bullet Point 1
* Bullet Point 2
* Bullet Point 3

## Images

[PCB Board]


<img width="572" height="416" alt="image" src="https://github.com/user-attachments/assets/fb557ad8-a2e5-4c17-b2f1-60cf27dbe371" />





<img width="2190" height="1512" alt="image" src="https://github.com/user-attachments/assets/9efacbe0-696a-4893-9e0a-123cc0fbeea4" />
**Figure 2:** Early PCB working design


![showcase](ImageShowcase.png)


### H-Bridge (Motor Driver)

| Solution | Photo | Link | Unit Cost | Pros | Cons |
|----------|--------|--------|-----------|-------|-------|
| Option 1: FAN8100N |<img width="640" height="640" alt="image" src="https://github.com/user-attachments/assets/31aeebd0-2281-4b88-b4e4-ec15abd9f2c3" /> |[FAN8100N Datasheet](https://www.digikey.com/en/products/detail/rochester-electronics-llc/FAN8100N/11558200?gclsrc=aw.ds&gad_source=1&gad_campaignid=120565755&gclid=Cj0KCQjw9czHBhCyARIsAFZlN8Td83C8Z8gdR38_rkx56qkHiMYeCuAWATtnKyPa6cvx9s9slA38YgAaArcOEALw_wcB)| $0.96 | Compact, logic-level, built-in protection | Must verify continuous current |
| Option 2: DRV8871 | <img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/51f718df-287c-4fcd-a85c-5954088572bb" />|[DRV8871](https://www.digikey.com/en/products/detail/texas-instruments/DRV8871DDARQ1/8347710?gclsrc=aw.ds&gad_source=1&gad_campaignid=20228387720&gclid=Cj0KCQjw9czHBhCyARIsAFZlN8S4qVNAMozf3Hh7ttzLuEbMeZ7Pt4pGIJsJqOqV7SmrHC9xeCaIfPQaAqlREALw_wcB)| $3.82 | Current limiting & thermal protection | Slightly more wiring |
| Option 3: L298N |<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/faf007a0-ed43-4912-9659-ddd56f807420" />| [L298N Module](https://www.digikey.com/en/products/detail/stmicroelectronics/L298N/585918?gclsrc=aw.ds&gad_source=1&gad_campaignid=20228387720&gclid=Cj0KCQjw9czHBhCyARIsAFZlN8Rs2xNGjbljsz_1EYiK-wMWGtYjNDDEZssP93XHzGJ4src6zgRIz-saAvbiEALw_wcB) | $11.78 | Easy to use, widely available | Inefficient, large voltage drop |

**Final Choice:** *FAN8100N*  
**Rationale:** Chosen for its protection features, size, and compatibility with 12 V system and PIC GPIO.


DC Motor Selection

| Solution | Photo | Link | Unit Cost | Pros | Cons |
| --- | --- | --- | --- | --- | --- |
| Option 1: M1N10FB11G  |<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/008c1915-1472-4211-b8f0-aabcb350dd6a" />| [M1N10FB11G ](https://www.digikey.com/en/products/detail/nmb-technologies-corporation/M1N10FB11G/2417078?gclsrc=aw.ds&gad_source=1&gad_campaignid=20243136172&gclid=Cj0KCQjw9czHBhCyARIsAFZlN8Ra9mbT1tIFcV5t-kcWw9YWB8xrca6-W-SrpTi-4TWKs_f_DMkQr_IaAn3xEALw_wcB) | $3.19 |Works on 12 V, simple wiring, compact |  Check stall current, add noise cap |
| Option 2: 12 V Gearmotor w/ Encoder |<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/cee27eba-58a6-4a45-8b22-06e35fe4e6c9" />| [Gearmotor + encoder](https://www.digikey.com/en/products/detail/dfrobot/FIT0186/6588528?gclsrc=aw.ds&gad_source=1&gad_campaignid=20243136172&gclid=Cj0KCQjw9czHBhCyARIsAFZlN8SwwRbIKz446RdhLvExD7Jq3hJFp_r5DxhS5wGWdU_l_QlIk-23MLoaAk6REALw_wcB) | $16.50 |  More torque, has feedback| Bigger size, more wires |
| Option 3: 12 V Generic DC Motor (no gearbox) |<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/e0264dbf-f6b2-42f6-9406-00820b16750d" />| [Generic 12 V DC motor](https://www.digikey.com/en/products/detail/olimex-ltd/MG-12V-12RPM/22157942?gclsrc=aw.ds&gad_source=1&gad_campaignid=20243136172&gclid=Cj0KCQjw9czHBhCyARIsAFZlN8T4poKcN0nC5ODQuPEy_bPangy6zy0kYFOLvjY0nSOWQ0ljkTPVw4EaAopSEALw_wcB) | $5.86 | Cheap, easy to find |  Torque varies, no feedback |

**Final Choice:** M1N10FB11G  
**Rationale:** Fits the 12 V system and mechanical space; provides adequate speed/torque for baseline demo; simplest electrical interface with the chosen H-bridge.



Voltage Regulator Selection (5 V Logic Rail)

| Solution | Photo | Link | Unit Cost | Pros | Cons |
| --- | --- | --- | --- | --- | --- |
| Option 1: 12 V → 5 V Buck Module (≥2 A) |<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/cefafcca-4e0f-42ec-9975-3cc8fbb94c14" />| [Buck module](https://www.digikey.com/en/products/detail/envistia-mall/F23J5V3A4S/26420424) | $5.89 |Handles high current, small size, stays cool|  Switching noise, needs filter cap |
| Option 2: LM7805 Linear Regulator |<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/88700506-9973-49a7-8e36-2de037592745" />| [LM7805](https://www.digikey.com/en/products/detail/texas-instruments/UA78M05CKCS/521616?gclsrc=aw.ds&gad_source=1&gad_campaignid=20228387720&gclid=Cj0KCQjw9czHBhCyARIsAFZlN8SMmcF35ESDpeZq5G1PZZSyAO0Rm_lPFeMZ5EiNADKQGwQLSUrgsgEaArRVEALw_wcB) | $4.20| Simple wiring, low noise |  Wastes heat, not good for 12→5 V drops |
| Option 3: Use Curiosity Nano USB 5 V |<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/cad168e0-ce7b-41ef-9352-1284d2da1bb1" />| [Board ref](https://www.digikey.com/en/products/detail/microchip-technology/EV53Z50A/16889562?gclsrc=aw.ds&gad_source=1&gad_campaignid=20243136172&gclid=Cj0KCQjw9czHBhCyARIsAFZlN8QsSYwf7xxqaQhg8AugncSBybDSFBbLQ3fk_YeqYXxtskF4rt-LRHwaAnpUEALw_wcB) | $0 |  No extra parts, easy to use |  Low current limit, not good for motor systems |

**Final Choice:** 12 V → 5 V Buck Converter (≥2 A)  
**Rationale:** Supplies MCU + logic with margin while avoiding heat of a linear regulator when stepping down from 12 V.


Power Source Selection (External)

| Solution | Photo | Link | Unit Cost | Pros | Cons |
| --- | --- | --- | --- | --- | --- |
| Option 1: 12 V, 2–3 A Regulated Wall Adapter |<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/5851fdef-140f-4222-bd2b-039c803c37e8" />| [12 V wall adapter](https://www.digikey.com/en/products/detail/triad-magnetics/WSU120-0700-R/3094980?gclsrc=aw.ds&gad_source=1&gad_campaignid=20232005509&gclid=Cj0KCQjw9czHBhCyARIsAFZlN8TFVvj7PSoSBD8DLiF1ic46F7QcSOPegxfym53Tw6c9u2Tg71CVW9YaAqR-EALw_wcB) | $7.35 | Simple; safe, readily available, meets stall + margin |  Tethered, not portable |
| Option 2: 3S Li-ion Pack + BMS |<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/1a0730f2-8d90-4031-8653-78b35962fdd8" />| [3S Li-ion + BMS](https://www.digikey.com/en/products/detail/dantona-industries/L37A52-2-1-3WA3/13692679?gclsrc=aw.ds&gad_source=1&gad_campaignid=20243136172&gclid=Cj0KCQjw9czHBhCyARIsAFZlN8SXKbI0gilJBMLqTbNlkLfi3v3ZwIE8SngqtwPa-J6yf74CLZ_FIFgaAqNpEALw_wcB) | $17.87 | Portable, real-world use| Requires charger/BMS, safety considerations 
| Option 3: Bench Power Supply |<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/5ac56556-54f3-4997-9971-5f9326fa019a" /> | [Bench PSU](https://www.digikey.com/en/products/detail/phoenix-contact/1394764/21848912?gclsrc=aw.ds&gad_source=1&gad_campaignid=20232005509&gclid=Cj0KCQjw9czHBhCyARIsAFZlN8SDCR366KwBJntPq899KcohlzfRSOIit_A_IDm5aIcjnehgYqWUwAgaAlmnEALw_wcB) | $18.19| Adjustable, current limit | Not a final product power source |

**Final Choice:** 12 V, ≥2 A Wall Adapter  
**Rationale:** Covers motor stall current with 25% system margin and keeps the lab setup simple and safe.


### Power Budget

This budget lists worst-case current for each device, groups them by rail, and adds a 25% safety margin.

#### Section A – Loads (worst case)

| Device / Subsystem | Voltage (V) | Max Current Each (mA) | Qty | Total (mA) |
| --- | ---:| ---:| ---:| ---:|
| PIC18F57Q43 Curiosity Nano | 5 | 50 | 1 | 50 |
| H-Bridge logic (FAN8100N) | 5 | 20 | 1 | 20 |
| Peripherals / LEDs / misc. | 5 | 25 | 1 | 25 |
| **DC Motor (stall)** | **12** | **2000** | **1** | **2000** |
| **Totals** | — | — | — | **2095** |

#### Section B – Rails with +25% margin

| Rail | Voltage | Sum of Loads (mA) | +25% Margin (mA) | **Required Capacity** |
| --- | ---:| ---:| ---:| ---:|
| **Logic_5V** | 5 | 95 | **119** | **≥120 mA @ 5 V** |
| **Motor_12V** | 12 | 2000 | **2500** | **≥2.5 A @ 12 V** |

> Note: The 5 V rail is generated from 12 V via a buck converter. At ~85% efficiency, 120 mA @ 5 V ≈ **0.6 W**, which draws about **0.06 A** from the 12 V source—small compared to the motor rail.

#### Section C – Regulator (5 V)

- **Choice:** 12 V → 5 V **buck (step-down) converter**, ≥**2 A** output, ~85–90% eff.  
- **Why:** Plenty of headroom for MCU + logic and runs cool compared to a linear regulator.  
- **Note:** Place 0.1 µF + 10 µF near MCU VCC, keep motor and logic grounds star-routed.

#### Section D – External Power Source

- **Choice:** **12 V, 3 A** regulated wall adapter.  
- **Why:** Meets **2.5 A** (stall + margin) on the motor rail plus a small extra draw for the 5 V buck. 3 A gives comfortable headroom.

#### Section E – Battery (optional)

- If using a 3S Li-ion pack, compute life with **worst-case average** current. For continuous stall, life is very short; use measured average instead.
  
### Results
The major electrical components for the motor control system were selected, compared, and justified based on compatibility, cost, and performance. The final design uses a 12 V brushed DC motor, an H-Bridge for direction control, and a 12 V → 5 V buck converter for logic power. A power budget was also completed using the motor’s stall current and a 25% safety margin to ensure the system can be powered safely and reliably. These selections support the goal of driving the motor forward and reverse using the PIC microcontroller.

### Conclusions and Future Work
The current design provides a solid foundation for motor control using the selected parts. The next step will be improving how the motor is controlled by adding PWM for smoother and adjustable speed, along with safety features such as current limits or automatic shutoff. Over time, the system can be expanded with more advanced features to improve motion control and flexibility.

### External Links
- [PIC18F57Q43 Curiosity Nano Product Page](https://www.microchip.com/en-us/development-tool/dm164150)
- [H-Bridge Information](https://www.ti.com/)
- [Buck Converter Information](https://www.digikey.com/)

### References
- Datasheets and product pages for the DC motor, H-Bridge, and buck converter
- PIC18F57Q43 Curiosity Nano documentation
- Power budget reference material from class


