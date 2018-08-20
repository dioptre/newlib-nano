# Newlib-nano
Copyright ©🄯 2018 Keith Packard
Copyright ©🄯 2018 Andrew Grosser

This is a fork of newlib which integrates the stdio code from gcc-avr
to make it much smaller for tiny embedded systems. There's debian
packaging which builds for arm-none-eabi targets.


# Building

## For Arm target on debian & ubuntu host
* ```apt install gcc-arm-none-eabi meson autoconf2.64``` and anything else
* ```meson newlib --cross-file=newlib/cross-arm-none-eabi.txt && ninja```
