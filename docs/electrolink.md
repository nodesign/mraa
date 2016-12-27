Using Electrolink board with mraa      {#electrolink}
=============================

Mraa can use a Electrolink board as a subplatform. This means one can access the
native IO as well as the IO on a electrolink compatible board

### Supported Electrolink boards ###

- Genuino/Arduino 101 running either CustomFirmata or StandardFirmata
- Other Arduino boards will likely work but are as of yet unsuported

### Using the subplatform API ###

Using the subplatform API is relatively simple, simply add '512', the platform
offset to any IO calls. I2c 0 becomes I2c 512+0 etc... The API works from UPM
or mraa in any of the bindings as long as you compiled mraa with -DFIRMATA=ON.
Currently -DFIRMATA is not compatible with USBPLAT. Multiple subplatforms are
not yet supported

### Sending custom MQTT messages ###

You can use the electrolink API to send custom MQTT messages.

### CurieImu Plugin ###

Using Customisable firmata we're able to use the onboard IMU to get data. This
uses the public SYSEX firmata API from mraa and there is a UPM module that
exposes this capability in a simple way. To use it your board needs to use
CustomFirmata with the CurieIMU plugin

### Limitations ###

Only one instance of mraa (one process linking to mraa) can communicate to an
firmata subplatform. This is a limitation due to only having one application
using the Uart at once. In order to get around this a daemon type methodology
has to be used. Technically you can mirror the TTY port from firmata but this
is likely going to cause issues
