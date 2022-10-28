# IASE-test-station
project of test stiation for SIMATIC S7-1200 system

## Design assumptions
* I want it to be portable,
* I want it to have built-in power supply,
* SIMATIC components;
   - CPU unit,
   - Digital IN/OUT,
   - Analog input,
   - RS-485 module,
   - Switch,
 * I want it to have bunch of switches and indicators - digital IO simulator,
 * I want it to have analog setter and analogue output measurements,

## Construction

<p align="center">
  <img width="750" src="https://user-images.githubusercontent.com/96399051/188468933-159279c5-fdba-47a7-a779-aaad8ff547c1.png">
  <img width="750" src="https://user-images.githubusercontent.com/96399051/188469810-0b7bd558-cb68-4da9-8d04-355bc24022c9.png">
</p>

As You can see, it is designed out of v-slots, there is place for PLC stuff as well for input setters and indicators. To show value of analog output I am planning to use simple meter shown below. It is one channel device and I am planning to use two analogue outputs - thus I am going to use two of them.

<p align="center">
  <img width="500" src="https://user-images.githubusercontent.com/96399051/198616406-75c70bc1-68a4-4a60-9313-be03373df0de.png">
</p>

## Analog setters

To set analogue values firstly I was planning to use some 4-20 output devices, but becouse we have 6 analogue inputs (and not all of them support current input) I decided to change approach and use 6 potentiometers to set voltage with range 0-10V. Becouse I wanted to see current voltage settings I decided to make small pcb with ability to show some data at screen.

### Main idea
is simple...
* I tahe 24VDC input and convert it down to 10VDC,
* 10VDC goes on potentiometers and from them it goes into:
   - output pins -> to PLC,
   - through voltage divider into analogue pins of arduino,
 * VIA I2C bus I show measurements on LCD 4x20
 
 ### Renders of design
<p align="center">
  <img width="1000" src="https://user-images.githubusercontent.com/96399051/188713483-224d0726-58c3-4380-adff-6425d9f5ef8a.png">
  <img width="1000" src="https://user-images.githubusercontent.com/96399051/188729027-83cc91f9-2014-4440-a9f4-2719aa549fe8.png">
</p>

### PCB view
<p align="center">
  <img width="700" src="https://user-images.githubusercontent.com/96399051/188469192-b07b9a15-e60d-4e0c-8963-60a718f3446a.png">
</p>

## Some simple code
basicly it is analogRead(inputPIN); and then pushing it on LCD, and thats all XD
