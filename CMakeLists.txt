# Generated Cmake Pico project file

cmake_minimum_required(VERSION 3.13)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# Initialise pico_sdk from installed location
# (note this can come from environment, CMake cache etc)
set(PICO_SDK_PATH $ENV{PICO_SDK_PATH})

# Pull in Raspberry Pi Pico SDK (must be before project)
include($ENV{PICO_SDK_PATH}/external/pico_sdk_import.cmake)
include($ENV{PICO_SDK_PATH}/tools/CMakeLists.txt)

project(PicoGFX C CXX ASM)

# Initialise the Raspberry Pi Pico SDK
pico_sdk_init()

# Add executable. Default name is the project name, version 0.1.0

add_executable(${PROJECT_NAME} main.cpp)
target_sources(${PROJECT_NAME} PUBLIC
        ${CMAKE_SOURCE_DIR}/Adafruit_GFX/Adafruit_GFX.cpp
        ${CMAKE_SOURCE_DIR}/Adafruit_GFX/Adafruit_GFX.h
        ${CMAKE_SOURCE_DIR}/Adafruit_GFX/glcdfont.c
        ${CMAKE_SOURCE_DIR}/SSD1306/Adafruit_SSD1306.cpp
        ${CMAKE_SOURCE_DIR}/SSD1306/Adafruit_SSD1306.h
        ${CMAKE_SOURCE_DIR}/SSD1306/splash.h
        )

pico_set_program_name(${PROJECT_NAME} "PicoGFX")
pico_set_program_version(${PROJECT_NAME} "0.1.0")

# disable UART stdio output, enable USB stdio output
pico_enable_stdio_uart(${PROJECT_NAME} 0)
pico_enable_stdio_usb(${PROJECT_NAME} 1)

# Add the standard library to the build
target_link_libraries(${PROJECT_NAME} pico_stdlib)

# Add any user requested libraries
target_link_libraries(${PROJECT_NAME}
        hardware_spi
        hardware_i2c
        hardware_dma
        hardware_pio
        hardware_interp
        hardware_timer
        hardware_watchdog
        hardware_clocks
        )

pico_add_extra_outputs(${PROJECT_NAME})

