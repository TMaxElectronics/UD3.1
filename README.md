# UD3 Series of Dual Resonant Solid State Tesla Coil Drivers

The UD3.X series of DRSSTC drivers are the official successor to the immensly popular UD2.X series originally developed by Steve Ward quite some time ago, which have achieved impressive adoption in the community over the years.
Now the upgrade to those has arrived, bringing tesla coils up do modern standards. It includes many incredibly useful features like:

 - live telemetry
 - easy adjustment of parameters like leadtime in text form (no trim-inductor fiddleing required ;) )
 - builtin interrupter with midi and SID capability
 - remote control of bus charging and discharging, no seperate system controller board needed
 - easy hardware expandibility with programmable (!) analog circuitry and many expansion headers on the board
   - could be used to implement for example a pfc without a seperate required controller
   
# Hardware
Based on one of Infineons PSOC chips (microcontroller + cpld + programmable analog). Builtin support for measureing thermocouples, bus voltage and input current.
Only one CT input required for both OCD (pulse skipping) and ZCD.

A serial interface implementing a transfer protocol is used for communication with the control pc. You will need external one external optical transmitter and one receiver to use it. Alternatively it can be connected directly to a fiber network using the [Fibernet Network card](https://github.com/TMaxElectronics/UD3_Fibernet) project.

Included in this Repo are a PDF schematic and also (soon...) a 3d step model of the PCB, which should be compatible with pretty much any CAD software you want to use.

# Software
Based on freeRTOS and written in C. Source code can be found [here](https://github.com/Netzpfuscher/UD3). <= **This repo also contains the Wiki with some info on how to get started**

# Upgrade log
### UD3 / UD3b
- Initial release, all credit to Steve Ward and Netzpfuscher for the work done to make it happen.

### UD3.1 (currently in development!)
- LED outputs are now open drain, allowing use of 24V indicators
- Voltage sense amplifiers moved to single 5V rail
- Updated gate drive structure to allow more wide range of N&P Fet combo packages
- Added protection resistors to Relay and LED pins, added protections resistors in series with mosfet gates
- Added buck regulator for VDrive, adjustable between 10V-24V
- Added more indicator LEDs for debug purposes
- Added supply voltages to more expansion headers, external gate header can now directly support 24V gate driver modules
