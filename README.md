# esp8266-example-mqtt-demo

git clone --recursive https://github.com/westmere/esp8266-example-mqtt-demo.git

mkdir build

cd build

cmake -DCMAKE_EXPORT_COMPILE_COMMANDS=ON -DTOOLCHAIN_PREFIX=$PWD/../xtensa-lx106-elf -DESP8266_SDK_VARIANT="RTOS" -DESP8266_SDK_VERSION="1.5.0" -DESPTOOL=${PWD}/../esptool/esptool.py -DESP8266_SDK_BASE=${PWD}/../ESP8266_RTOS_SDK -DCMAKE_BUILD_TYPE=Release -G "Eclipse CDT4 - Unix Makefiles" -DCMAKE_ECLIPSE_VERSION=4.6 ../esp8266-cmake/examples/mqtt_demo

make

make firmware 

./esptool.sh /dev/ttyUSB0
