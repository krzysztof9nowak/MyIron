# MyIron

### Goal
To have a soldering station.

### Design requirments

- components can be easily and cheaply sourced in 2022
- support C210 and C245 tips with JBC connector
- 130W @ 24V
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
- high side current measurment 
$$I = \cfrac{130W}{24V} \approx 5.4A$$
, so assuming $I_{max}=10A$ 
$$R_{sense} = 10m \Omega$$
$$U_{sense} = 100mV$$ 
$$U_{ADC}=5V$$
$$G = 50$$
INA180-A2 (absolute max $26V$, accuracy 1%, CMRR min 84dB, typ 100dB, 210kHz bandwidth, 5V supply)

Calculating CMRR for an opamp circuit:
$\cfrac{A_{diff}}{A_{cm}} \approx \cfrac{1 + G}{2 \Delta}$
, where $\Delta$ is tolerance of resistors. Unviable with 1% resistors...

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
