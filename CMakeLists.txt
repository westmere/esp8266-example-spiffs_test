# set(CMAKE_TOOLCHAIN_FILE "${CMAKE_CURRENT_LIST_DIR}/esp8266-cmake/cmake/ESP8266Toolchain.cmake")
project(esp8266-spiffs_test)

include(ExternalProject)
cmake_minimum_required(VERSION 3.5)

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/build)

ExternalProject_Add(spiffs_test
                    #--Download step--------------
                    #--Configure step-------------
                    #--Update/Patch step----------
                    SOURCE_DIR ${CMAKE_CURRENT_LIST_DIR}/esp8266-cmake/examples/spiffs_test
                    CMAKE_ARGS -DTOOLCHAIN_PREFIX=${CMAKE_CURRENT_LIST_DIR}/xtensa-lx106-elf
                    CMAKE_ARGS -DESP8266_SDK_VARIANT=RTOS
                    CMAKE_ARGS -DESP8266_SDK_VERSION=1.5.0
                    CMAKE_ARGS -DESP8266_SDK_BASE=${CMAKE_CURRENT_LIST_DIR}/ESP8266_RTOS_SDK
#                     CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=${CMAKE_BINARY_DIR}
                    #--Build step-----------------
                    BINARY_DIR ${EXECUTABLE_OUTPUT_PATH}
                    #--Install step---------------
#                     INSTALL_DIR ${CMAKE_BINARY_DIR}
                   INSTALL_COMMAND ${CMAKE_COMMAND} -E echo "Skipping install step."
                    #--Test step------------------
                    #--Output logging-------------
                    #--Custom targets-------------
#                     STEP_TARGETS firmware
#                     EXCLUDE_FROM_ALL TRUE
                    )

set_property(DIRECTORY APPEND PROPERTY ADDITIONAL_MAKE_CLEAN_FILES
    "${EXECUTABLE_OUTPUT_PATH}"
)
