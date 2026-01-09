Hardware
- Exhaust fan with activated carbon and hepa
- The Shmilter under centre of bed, activated carbon and two fans
- two fans, one under each outer edge of the bed, controlled as a chamber heater
- chamber thermistor coming out of the cable chain at the back for controlling the outer bed fans


Orca settings

Printer
Machine Start
; Start macro: Heat bed and nozzle simultaneously
M104 S150                                           ; Preheat nozzle to 150°C (non-blocking)
M140 S[bed_temperature_initial_layer_single]        ; Set bed target temperature (non-blocking)
M190 S[bed_temperature_initial_layer_single]        ; Wait for bed to reach target temperature
M109 S150                                           ; Wait for nozzle to reach 150°C
PRINT_START EXTRUDER=[nozzle_temperature_initial_layer] BED=[bed_temperature_initial_layer_single] CHAMBER_TEMP=[chamber_temperature]

Machine End
PRINT_END


Filament
Activate Air Filtration On

ABS
- During print 10%
- After print 70%

PLA
- During print 80% (for cooling)
- After print 70%


Workflow

Orca passes chamber temperature to Klipper, then the chamber heats with the sequence before printing.
To manually heat the chamber for presoak it is treated as a heater, so set bed to 100C and chamber to 60C.
The exhaust fan is controlled by the print job, and runs for 10mins after the print to reduce fumes. It auto cancels the timer if a new print is started.