#What is DCC++ BaseStation#

**DCC++ BASE STATION** is a **C++** program written by **Gregg E. Berman** for the Arduino Uno and Arduino Mega
using the [Arduino IDE](https://www.arduino.cc/en/Main/Software) 1.6.6 or higher.

It allows a standard [Arduino Uno](https://www.arduino.cc/en/Main/ArduinoBoardUno) or [Arduino Mega](https://www.arduino.cc/en/Main/ArduinoBoardMega2560) with an [Arduino motor shield](https://www.arduino.cc/en/Main/ArduinoMotorShieldR3) (as well as others)
to be used as a fully-functioning digital command and control (DCC) base station
for controlling model train layouts that conform to current National Model
Railroad Association ([NMRA](http://www.nmra.org)) DCC standards.

The newest version of DCC++ BASE STATION supports:

  * 2-byte and 4-byte locomotive addressing
  * Simultaneous control of multiple locomotives
  * 128-step speed throttling
  * Cab functions F0-F28
  * Activate/de-activate accessory functions using 512 addresses, each with 4 sub-addresses
      - includes optional functionailty to monitor and store of the direction of any connected turnouts
  * Programming on the Main Operations Track
      - write configuration variable bytes
      - set/clear specific configuration variable bits
  * Programming on the Programming Track
      - write configuration variable bytes
      - set/clear specific configuration variable bits
      - read configuration variable bytes

DCC++ BASE STATION is controlled with simple text commands received via
the Arduino's serial interface, or one of the other supported interfaces. Users can type these commands directly into the Arduino IDE Serial Monitor, or can send such commands from another device or computer program.

When compiled for the [Arduino Mega](https://www.arduino.cc/en/Main/ArduinoBoardMega2560), an [Arduino Ethernet Shield](https://www.arduino.cc/en/Main/ArduinoEthernetShield) can be used for network communications instead of using serial communications.

[DCC++ Controller](https://github.com/DccPlusPlus/Controller), available separately under a similar open-source license, is a Java program written using the Processing library and Processing IDE that provides a complete and configurable graphic interface to control model train layouts via the [DCC++ Base Station](https://github.com/DccPlusPlus/BaseStation).

With the exception of a standard 15V power supply that can be purchased in
any electronics store, no additional hardware is required.

Neither [DCC++ Base Station](https://github.com/DccPlusPlus/BaseStation) nor [DCC++ Controller](https://github.com/DccPlusPlus/Controller) use any known proprietary or commercial hardware, software, interfaces, specifications, or methods related to the control of model trains using [NMRA DCC Standards](http://www.nmra.org/index-nmra-standards-and-recommended-practices). Both programs are original, developed by **Gregg E. Berman**, and are not derived from any known commercial, free, or open-source model railroad control packages by any other parties.

However, [DCC++ Base Station](https://github.com/DccPlusPlus/BaseStation) and [DCC++ Controller](https://github.com/DccPlusPlus/Controller) do heavily rely on the IDEs and embedded libraries associated with [Arduino IDE](https://www.arduino.cc/en/Main/Software) and [Processing IDE](https://processing.org/download/).  Tremendous thanks to those responsible for these terrific open-source initiatives that enable programs like [DCC++](https://sites.google.com/site/dccppsite/) to be developed and distributed in the same fashion.
