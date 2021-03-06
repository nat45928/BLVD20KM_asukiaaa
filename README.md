# BLVD20KM_asukiaaa

A library for Arduino to control BLVD20KM which is a brushless motor controller of Oriental Motor.

# Usage

## BLVD20KM configuration

### SW 2

To use BLVD20KM in 115200bps via RS485 modbus, set switch 2 like this

No | State | Role
-- | ----- | ---
1  | OFF   | Baudrate
2  | OFF   | Baudrate
3  | ON    | Baudrate
4  | OFF   | Not used
5  | ON    | Use Modbus Protocol
6  | OFF   | Not used
7  | ON if the BLVD02KM is end of RS485 chain | End point register
8  | OFF   | Address upper bit

Baudrate configuration

No1 | No2 | No3 | Baudrate
--- | --- | --- | --------
OFF | OFF | OFF | 9600
ON  | OFF | OFF | 19200
OFF | ON  | OFF | 38400
ON  | ON  | OFF | 57600
OFF | OFF | ON  | 115200

### SW 3

Switch 3 means address of motor driver.
If you use multiple motor, set different address for each motors.

## Connection

### LAN cable pinout of BLVD20KM

No | Role
---|-----
1  | NC
2  | GND
3  | TR+
4  | NC
5  | NC
6  | TR-
7  | NC
8  | NC

### Arduino <-> Uart to RS485S Transceiver <-> BLVD20KM

Arduino | Uart to RS485 | BLVD20KM
--------|--------|------
None    | A      | TR+ (LAN 3)
None    | B      | TR- (LAN 6)
TX1     | DI     | None
RX1     | RO     | None
D3      | RE     | None
D2      | DE     | None
VCC     | 5V     | None
GND     | GND    | GND (LAN 2)

I checked connection with using [SparkFun Transceiver Breakout - RS-485](https://www.sparkfun.com/products/10124).

## Software

See [example project](./examples) and [header file](./src/BLVD02KM_asukiaaa.h).

# License

MIT

# References

- BLVD20KM manual list [ja](https://www.orientalmotor.co.jp/download/manual_search.action?productName=BLVD20KM&searchPattern=1&gengoId=1) [en](https://www.orientalmotor.co.jp/download/manual_search.action?productName=BLVD20KM&searchPattern=1&gengoId=2&x=22&y=17)
- [BLVD20KM](https://www.orientalmotor.co.jp/products/detail.action?hinmei=BLVD20KM)
- [ArduinoでRS-485に対応する](https://www.denshi.club/cookbook/wire/rs-4852-arduinors-485.html)
- [CRC16を計算する](http://www.soramimi.jp/crc16/)
