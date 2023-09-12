# Конфигурационный файлы Klipper для Anycubic i3 Mega
Прикладываю свои рабочие файлы конфигурации Klipper для своего принтера.

А также скрины Cura с G-Code начала и окончания печати:
# Settings->Printer->Manage printers->Machine Settings
Start G-CODE:
G21 ;metric values
G90 ;absolute positioning
M82 ;set extruder to absolute mode
M107 ;start with the fan off
G28 X0 Y0 ;move X/Y to min endstops
G28 Z0 ;move Z to min endstops
G1 Z15.0 F{speed_travel} ;move the platform down 15mm
G92 E0 ;zero the extruded length
G1 F200 E3 ;extrude 3mm of feed stock
G92 E0 ;zero the extruded length again
G1 F{speed_travel}
G0 Y20 F{speed_travel}
M117 Printing...

End G-CODE:
TURN_OFF_HEATERS
M107
G91 ;relative positioning
G1 E-1 F300 ;retract the filament a bit before lifting the nozzle, to release some of the pressure
G0 X5 Y5 Z0.2 F5000
G0 Z2 F1500
G90
PARK
M84
M300 P300 S4000
M117 Finished.

# В конфигах реализованы макросы стандартных комманд:
- M600 (замена филамента)
- M300 (работа со встроенным BEEP-ером)
- Парковка после окончания печати

Файлы на стороне Klipper лежат в папке ~/printer_data/config
В моём случае в качестве платформы был использован **Orange Pi One** с установленной на нём Armbian 23.8.1 bookworm
