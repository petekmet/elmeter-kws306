# elmeter-kws306
Electricity meter documentation

| Register Address (HEX) | Meaning                          | Word Length | R/W | Scale Factor | Notes                                                                 |
|-------------------------|----------------------------------|-------------|-----|--------------|----------------------------------------------------------------------|
| 0x000C                 | Communication Address & Baudrate Status Word | 1 | RW  | 1            | High byte = baudrate, low byte = communication address. Example readout `02 03 02 02 03 BD 25` → baudrate = 0x02, address = 0x03 |
| 0x000E                 | Phase A Voltage                  | 1           | R   | 100          | 220.00 V                                                             |
| 0x000F                 | Phase B Voltage                  | 1           | R   | 100          |                                                                      |
| 0x0010                 | Phase C Voltage                  | 1           | R   | 100          |                                                                      |
| 0x0011                 | Phase A Current (High+Low)       | 2           | R   | 1000         | 5.000 A. All double-word data: high word first, low word second      |
| 0x0013                 | Phase B Current (High+Low)       | 2           | R   | 1000         |                                                                      |
| 0x0015                 | Phase C Current (High+Low)       | 2           | R   | 1000         |                                                                      |
| 0x0017                 | Total Active Power               | 2           | R   | 10           | 1100.0 W                                                             |
| 0x0019                 | Phase A Active Power             | 2           | R   | 10           |                                                                      |
| 0x001B                 | Phase B Active Power             | 2           | R   | 10           |                                                                      |
| 0x001D                 | Phase C Active Power             | 2           | R   | 10           |                                                                      |
| 0x001F                 | Total Reactive Power             | 2           | R   | 10           | var                                                                  |
| 0x0021                 | Phase A Reactive Power           | 2           | R   | 10           |                                                                      |
| 0x0023                 | Phase B Reactive Power           | 2           | R   | 10           |                                                                      |
| 0x0025                 | Phase C Reactive Power           | 2           | R   | 10           |                                                                      |
| 0x0027                 | Total Apparent Power             | 2           | R   | 10           | VA                                                                   |
| 0x0029                 | Phase A Apparent Power           | 2           | R   | 10           |                                                                      |
| 0x002B                 | Phase B Apparent Power           | 2           | R   | 10           |                                                                      |
| 0x002D                 | Phase C Apparent Power           | 2           | R   | 10           |                                                                      |
| 0x002F                 | Total Power Factor               | 1           | R   | 1000         |                                                                      |
| 0x0030                 | Phase A Power Factor             | 1           | R   | 1000         |                                                                      |
| 0x0031                 | Phase B Power Factor             | 1           | R   | 1000         |                                                                      |
| 0x0032                 | Phase C Power Factor             | 1           | R   | 1000         |                                                                      |
| 0x0033                 | Frequency                        | 1           | R   | 100          | 50.00 Hz                                                             |
| 0x0034                 | Total Energy                     | 2           | R   | 100          | 1.00 kWh                                                             |
| 0x0036                 | Phase A Energy                   | 2           | R   | 100          |                                                                      |
| 0x0038                 | Phase B Energy                   | 2           | R   | 100          |                                                                      |
| 0x003A                 | Phase C Energy                   | 2           | R   | 100          |                                                                      |
| 0x003C                 | Temperature                      | 1           | R   | 1            | 25 ℃                                                                 |
| 0x003D                 | Runtime                          | 1           | R   |              | Minutes                                                              |
| 0x003E                 | Alarm Flags                      | 1           | R   |              | Bit flags: 0=Overvoltage, 1=Undervoltage, 2=Overcurrent, 3=Overpower, 4=Over Energy, 5=Overtemperature, 6=Voltage imbalance, 7=Current imbalance |
| 0x003F                 | Meter Status                     | 1           | RW  |              | 0=Output Off, 1=Output On. Only single-word write allowed            |
| 0x0040                 | Overvoltage Threshold            | 1           | RW  | 10           | 240.0 V, max=290.0. Can be read/written together                     |
| 0x0041                 | Undervoltage Threshold           | 1           | RW  | 10           | 120.0 V, max=220.0                                                   |
| 0x0042                 | Overcurrent Threshold            | 1           | RW  | 100          | 20.00 A, max=99.00                                                   |
| 0x0043                 | Overpower Threshold              | 1           | RW  | 100          | 1.00 kW, max=23.20                                                   |
| 0x0044                 | Voltage Imbalance Threshold      | 1           | RW  | 10           | 10.0 V, max=290.0                                                    |
| 0x0045                 | Current Imbalance Threshold      | 1           | RW  | 10           | 1.0 A, max=99.0                                                      |
| 0x0046                 | Countdown Timer                  | 1           | RW  | 1            | Minutes, max=59999                                                   |
| 0x0047                 | Screensaver Timeout              | 1           | RW  | 1            | Minutes, max=59                                                      |
| 0x0048                 | Overtemperature Threshold        | 1           | RW  | 1            | ℃, max=150                                                           |
| 0x0049                 | Over Energy Threshold            | 2           | RW  | 1            | kWh, max=9,999,999                                                   |
| 0x004B                 | Energy Reset                     | 1           | W   | 1            | Write `0x5AA5` to clear. Only single-word write allowed              |
| 0x004C                 | Timer Reset                      | 1           | W   | 1            | Write `0x5AA5` to clear. Only single-word write allowed              |
