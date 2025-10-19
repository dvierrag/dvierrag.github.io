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
| Option 1: FAN8100N |(<img width="640" height="640" alt="image" src="https://github.com/user-attachments/assets/31aeebd0-2281-4b88-b4e4-ec15abd9f2c3" /> |[FAN8100N Datasheet](https://www.unikeyic.com/?campaignid=22783272917&adgroupid=183048181420&feeditemid&targetid=kwd-296668624245&device=c&creative=763224061586&keyword=electronic%20components%20online%20market&gclid=Cj0KCQjw9czHBhCyARIsAFZlN8R8Vcb45DylHHPIODkKHT1TnOQzkQvjbgJ_wIkDguQowdL8BwksVncaArG3EALw_wcB&gad_source=1&gad_campaignid=22783272917)| $X.XX | Compact, logic-level, built-in protection | Must verify continuous current |
| Option 2: DRV8871 | ![photo](../static/drv8871.jpg) | [DRV8871 Datasheet](https://www.ti.com/) | $0.96 | Current limiting & thermal protection | Slightly more wiring |
| Option 3: L298N | ![photo](../static/l298.jpg) | [L298N Module](https://www.robotshop.com/) | $X.XX | Easy to use, widely available | Inefficient, large voltage drop |

**Final Choice:** *FAN8100N*  
**Rationale:** Chosen for its protection features, size, and compatibility with 12 V system and PIC GPIO.



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


