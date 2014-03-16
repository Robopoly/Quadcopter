# Quadcopter shield

## Introduction
This shield has firstly been designed by Robopoly for Aeropoly. It is now available at Robopoly.
It is compatible with the PRismino, and thus compatible with a Leonardo and most Arduino boards.
It is basically a copy of the nanowii board, except that it is now set as a shield for a Leonardo, rather than a standalone board.
Therefore, you can use the multiwii code, but you will have to make your own configuration.
You can find the Altium and gerber files, as well as the datasheets on this repo.

## Components
The shield is mainly a break-out board. There are only 3 chips on the board:
| chip | purpose | link |
|-------| ------- | -----|
|MPU-9150|Accelerometer, gyroscope, magnetometer | http://www.invensense.com/mems/gyro/nineaxis.html |
|TLV70033DDCR | 3V regulator | http://www.ti.com/product/tlv70033 |
|PCA9306DP1-G| I2C level translator| http://www.nxp.com/products/interface_and_connectivity/i2c/i2c_voltage_level_translators/PCA9306DP1.html|

## Power
You can power the controller through the shield by connecting an 5V BEC to ESC1 pin.
The 3.3V available with the micromatch or double pins are not the ones from the arduino. Meaning you won't fry your controller if you use too much current.
I recommend not to draw current from the 3.3V regulator of the controller, because that one powers the MPU-9150.

## Used pins
### ESC connections
Be careful, only ESC 1 has the ground and 5V pins connected. This is made to avoid ground loops.
| ESC | pin |
|-----|-----|
|ESC1 | x   |
|ESC2 | x   |
|ESC3 |     |
|ESC4 |     |

### Transmitter connections
Be careful, only THR has the ground and 5V pins connected. This is made to avoid ground loops. If your transmitter does not have a common ground for its channels, you will want to bridge the whole ground line.
| Command | pin |
|---------|-----|
| THR     |     |
|---------|-----|
| ROLL    |     |
|---------|-----|
| YAW     |     |
|---------|-----|
| PITCH   |     |
|---------|-----|
| AUX     |     |

## Thanks
I'd like to thank the various people that have helped developping this board. Mainly the directors of Robopoly, and xxxx, the creator of the Nanowii board.

