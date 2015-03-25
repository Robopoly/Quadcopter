# Quadcopter shield

## Introduction
This shield has firstly been designed by Robopoly for Aeropoly. It is now available at Robopoly.
It is cmade for the [PRismino][prismino], and thus compatible with a Leonardo and most Arduino boards.
It is basically a copy of the nanowii board, except that it is now set as a shield for a Leonardo, rather than a standalone board. The pins are exactly the same.
Therefore, you can use the [Multiwii][multiwii] code, but you will have to make your own configuration.
You can find the Altium and gerber files, as well as the datasheets on this repo.

## Components

NOT VALID FOR NEW VERSION. CHECK DOC PDF
The shield is mainly a break-out board. There are only 3 chips on the board:
The MPU-9150 has the same register map as it's brother the MPU-6050 which is used in a Nanowii board. Therefore you can use it as a MPU-6050 if you don't want the magnetometer.
NOT VALID FOR NEW VERSION. CHECK DOC PDF
| chip         | purpose                                | link                         |
|--------------|----------------------------------------|------------------------------|
| MPU-9150     | Accelerometer, gyroscope, magnetometer | [MPU-9150][MPU-9150]         |
| TLV70033DDCR | 3V regulator                           | [TLV70033DDCR][TLV70033DDCR] |
| PCA9306DP1-G | I2C level translator                   | [PCA9306DP1-G][PCA9306DP1-G] |
NOT VALID FOR NEW VERSION. CHECK DOC PDF
| identifier   |   value   |
|--------------|-----------|
| R1 -> R5     | 10kOhm    |
| C1,2,5,6,7   | 0.1uF     |
|     C4       |  10nF     |
|     C3       |   2.2nF   |
NOT VALID FOR NEW VERSION. CHECK DOC PDF

## Power
You can power the controller through the shield by connecting an 5V BEC to ESC1 pin.
The 3.3V available with the micromatch or double pins are not the ones from the Arduino. Meaning you won't fry your controller if you use too much current.
However, you should stick well within the limits as it powers the MPU-9150 and the I2C level shifter.

## Used pins
### Jumper
Either J0 or J1 has to be bridged. If you bridge both, you'll short your power. Never bridge both. These are used to set the address of the MPU-9150.

### ESC connections
Be careful, only ESC 1 has the ground and 5V pins connected. This is made to avoid ground loops.
The data pin is at the outer side of the board (closest to the pins). The ground pin is the square one.

| ESC  | pin   |
|------|-------|
| ESC1 |   9   |
| ESC2 |  10   |
| ESC3 |   5   |
| ESC4 |   6   |

### Transmitter connections
Be careful, only THR has the ground and 5V pins connected. This is made to avoid ground loops. If your transmitter does not have a common ground for its channels, you will have to bridge the whole ground line, or mod your receiver.
The data pin is at the outer side of the board (closest to the edge). The ground pin is the square one.

| Command | pin  |
|---------|------|
| THR     |   7  |
| ROLL    | MOSI |
| YAW     | SCK  |
| PITCH   | MISO |
| AUX1    |  8   |

## Various
### MPU-9150
Be careful that the axis for the magnetometer are not the same as for the accelerometer and the gyroscope. The ones on the board are those of the accelerometer.

## Thanks
I'd like to thank the various people that have helped developping this board and namely Felix (aka ronco on multiwii forum), the creator of the Nanowii board.

[MPU-9150]: http://www.invensense.com/mems/gyro/nineaxis.html "MPU-9150"
[TLV70033DDCR]: http://www.ti.com/product/tlv70033 "TLV70033DDCR"
[atmega32u4]: http://www.atmel.ch/Images/doc7766.pdf "ATmega16U4/32U4 datasheet"
[PCA9306DP1-G]: http://www.nxp.com/products/interface_and_connectivity/i2c/i2c_voltage_level_translators/PCA9306DP1.html "PCA9306DP1-G"
[prismino]: https://github.com/Robopoly/PRismino "PRismino"
[multiwii]: http://www.multiwii.com/software "Multiwii"