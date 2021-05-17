

# How to use STM32_F4VE development board from Arduino IDE

The board:

[https://stm32-base.org/boards/STM32F407VET6-STM32-F4VE-V2.0](https://stm32-base.org/boards/STM32F407VET6-STM32-F4VE-V2.0)

The USB port does not work, so I programmed it with an FTDI Serial to USB board.

Set the FTDI to 5V and connect it to the STM board.

STM	FTDI

GND	GND

5V	VCC

RX	TX

TX	RX

Install STM32CubeProgrammer

In Arduino IDE add STM32:

[https://github.com/stm32duino/wiki/wiki/Getting-Started](https://github.com/stm32duino/wiki/wiki/Getting-Started)

Arduino IDE tools menu: \
Board: Generic STM32F4 series

Board part number: Generic  F407VETx (Probably not important)

U(S)ART support: Enabled (Generic serial)

Upload method: STM32CubeProgrammer (Serial)

Because there is no such a board (STM32_F4VE), the ports are not set up well.

Use the blink example, but change BUILTIN_LED to PA6 or PA7 (There are two leds on this board + the power LED).

There are two jumpers on the board, BT0 and BT1 (BOOT0 and BOOT1)
Before upload the code, set BT0 to 3.3V and press Reset button
Before running the code, set BT0 to GND and press Reset button
Boot1 remains in GND in both cases.


```
void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(PA6, OUTPUT);
  pinMode(PA7 part , OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(PA6, HIGH);   // turn the LED on (HIGH is the voltage level)
  digitalWrite(PA7, LOW);   // turn the LED on (HIGH is the voltage level)
  delay(1000);                       // wait for a second
  digitalWrite(PA7, HIGH);   // turn the LED on (HIGH is the voltage level)
  digitalWrite(PA6, LOW);   // turn the LED on (HIGH is the voltage level)
  delay(1000);                       // wait for a second
}
```