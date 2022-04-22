# MyIron

### Goal
To have a soldering station.

### Design requirments

- components can be easily and cheaply sourced in 2022
- support C210 and C245 tips with JBC connector
- >= 130W @ 24V
- display of current temperature, set temperature and power bar
- PID control without overshoots
- easy changing of temperature + 2 presets
- detection of handle in the stand => autocooldown
- safety timer 15min ?
- single PCB
- protection against MOSFET short circuit failure (relatively common failure)
- EMC
- quiet

### Design decisions
- MCU
	- ESP32 - 3USD, seems overkill, but okay
	- STM32 - unavailable or extremly pricy
	- AVR - also pricy
- current measurment
	- high side
	- low side
	- custom current op-amp (INA180)
	- basic rail-to-rail op-amp
- PWM switching
	- low side - imposible, due to the required grounding of the tip
	- high side
	- N type FET with bootstraping 
	- P type FET
- handle connector
	- front
	- back
- enclousure
	- plywood (laser cut or handmade)
	- extruded aluminium
	- 3D printed
- power supply connector
