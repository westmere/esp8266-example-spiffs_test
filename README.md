git clone --recursive https://github.com/westmere/esp8266-example-spiffs_test.git

rm -rf build
mkdir -p build
cd build
cmake -DCMAKE_EXPORT_COMPILE_COMMANDS=ON -DCMAKE_BUILD_TYPE=Release -G "Eclipse CDT4 - Unix Makefiles" -DCMAKE_ECLIPSE_VERSION=4.6 ../esp8266-example-spiffs_test

make all

cd build

./esptool.sh /dev/ttyUSB0
