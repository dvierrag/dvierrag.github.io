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

[PCB Board]<img width="1302" height="914" alt="image" src="https://github.com/user-attachments/assets/1635725e-87ba-4b8b-8c1a-bffb353760a6" />
>


![dead bug circuit](<img width="637" height="416" alt="{3E89A480-116B-4404-A64E-40A77FE4E3C4}" src="https://github.com/user-attachments/assets/8403d2b1-0b24-4b2d-b45f-678afe495a7f" />
){style width:"350" height:"300;"}
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
| **Option 1: M1N10FB11G  |<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/008c1915-1472-4211-b8f0-aabcb350dd6a" />| [M1N10FB11G ](https://www.digikey.com/en/products/detail/nmb-technologies-corporation/M1N10FB11G/2417078?gclsrc=aw.ds&gad_source=1&gad_campaignid=20243136172&gclid=Cj0KCQjw9czHBhCyARIsAFZlN8Ra9mbT1tIFcV5t-kcWw9YWB8xrca6-W-SrpTi-4TWKs_f_DMkQr_IaAn3xEALw_wcB) | $3.19 | Matches 12 V rail; simple H-bridge drive; compact | Verify **stall current** vs driver/supply; add EMI suppression |
| **Option 2: 12 V Gearmotor w/ Encoder |<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/cee27eba-58a6-4a45-8b22-06e35fe4e6c9" />| [Gearmotor + encoder](https://www.digikey.com/en/products/detail/dfrobot/FIT0186/6588528?gclsrc=aw.ds&gad_source=1&gad_campaignid=20243136172&gclid=Cj0KCQjw9czHBhCyARIsAFZlN8SwwRbIKz446RdhLvExD7Jq3hJFp_r5DxhS5wGWdU_l_QlIk-23MLoaAk6REALw_wcB) | $16.50 | Higher torque; built-in position feedback | More wiring; encoder logic-level compatibility; larger package |
| **Option 3: 12 V Generic DC Motor (no gearbox) |<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/e0264dbf-f6b2-42f6-9406-00820b16750d" />| [Generic 12 V DC motor](https://www.digikey.com/en/products/detail/olimex-ltd/MG-12V-12RPM/22157942?gclsrc=aw.ds&gad_source=1&gad_campaignid=20243136172&gclid=Cj0KCQjw9czHBhCyARIsAFZlN8T4poKcN0nC5ODQuPEy_bPangy6zy0kYFOLvjY0nSOWQ0ljkTPVw4EaAopSEALw_wcB) | $5.86 | Inexpensive; easy to source | Lower torque; speed varies with load; no feedback |

**Final Choice:** M1N10FB11G  
**Rationale:** Fits the 12 V system and mechanical space; provides adequate speed/torque for baseline demo; simplest electrical interface with the chosen H-bridge.



Voltage Regulator Selection (5 V Logic Rail)

| Solution | Photo | Link | Unit Cost | Pros | Cons |
| --- | --- | --- | --- | --- | --- |
| **Option 1: 12 V → 5 V Buck Module (≥2 A)** | ![photo](../static/buck_12to5.jpg) | [Buck module](#) | $TBD | High efficiency; low heat; compact; plenty of headroom | Switching noise—add LC filter near MCU |
| **Option 2: LM7805 Linear Regulator** | ![photo](../static/lm7805.jpg) | [LM7805](#) | $TBD | Simple; low ripple | Inefficient from 12→5 V; possible thermal issues |
| **Option 3: Use Curiosity Nano USB 5 V** | ![photo](../static/usb_5v.jpg) | [Board ref](#) | $0 | No extra hardware | Limited current; possible ground loop with 12 V motor rail |

**Final Choice:** 12 V → 5 V Buck Converter (≥2 A)  
**Rationale:** Supplies MCU + logic with margin while avoiding heat of a linear regulator when stepping down from 12 V.


Power Source Selection (External)

| Solution | Photo | Link | Unit Cost | Pros | Cons |
| --- | --- | --- | --- | --- | --- |
| **Option 1: 12 V, 2–3 A Regulated Wall Adapter** | ![photo](../static/12v_wall_adapter.jpg) | [12 V wall adapter](#) | $TBD | Simple; safe; readily available; meets stall + margin | Tethered; not portable |
| **Option 2: 3S Li-ion Pack + BMS** | ![photo](../static/3s_liion.jpg) | [3S Li-ion + BMS](#) | $TBD | Portable demo; realistic product scenario | Requires charger/BMS; safety considerations |
| **Option 3: Bench Power Supply** | ![photo](../static/bench_psu.jpg) | [Bench PSU](#) | $TBD | Adjustable; current limit for bring-up | Not a final product power source |

**Final Choice:** 12 V, ≥2 A Wall Adapter  
**Rationale:** Covers motor stall current with 25% system margin and keeps the lab setup simple and safe.







## Results

1. Numbered Point 1
1. Numbered Point 2
1. Numbered Point 3

## Conclusions and Future Work

## External Links

[example link to idealab](https://idealab.asu.edu)


## Results

1. Numbered Point 1
1. Numbered Point 2
1. Numbered Point 3

## Conclusions and Future Work

## External Links

[example link to idealab](https://idealab.asu.edu)


## References


