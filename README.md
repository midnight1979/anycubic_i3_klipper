# Конфигурационный файлы Klipper для Anycubic i3 Mega
Прикладываю свои рабочие файлы конфигурации Klipper для своего принтера.

А также скрины Cura с G-Code начала и окончания печати:<br>
Заходим в **Settings->Printer->Manage printers->Machine Settings**<br>
**Start G-CODE:<br>**
G21 ;metric values<br>
G90 ;absolute positioning<br>
M82 ;set extruder to absolute mode<br>
M107 ;start with the fan off<br>
G28 X0 Y0 ;move X/Y to min endstops<br>
G28 Z0 ;move Z to min endstops<br>
G1 Z15.0 F{speed_travel} ;move the platform down 15mm<br>
G92 E0 ;zero the extruded length<br>
G1 F200 E3 ;extrude 3mm of feed stock<br>
G92 E0 ;zero the extruded length again<br>
G1 F{speed_travel}<br>
G0 Y20 F{speed_travel}<br>
M117 Printing...<br>

**End G-CODE:<br>**
TURN_OFF_HEATERS<br>
M107<br>
G91 ;relative positioning<br>
G1 E-1 F300 ;retract the filament a bit before lifting the nozzle, to release some of the pressure<br>
G0 X5 Y5 Z0.2 F5000<br>
G0 Z2 F1500<br>
G90<br>
PARK<br>
M84<br>
M300 P300 S4000<br>
M117 Finished.<br>

# В конфигах реализованы макросы стандартных комманд:
- M600 (замена филамента)
- M300 (работа со встроенным BEEP-ером)
- Парковка после окончания печати

Файлы на стороне Klipper лежат в папке **~/printer_data/config<br>**
В моём случае в качестве платформы был использован **Orange Pi One** с установленной на нём Armbian 23.8.1 bookworm
