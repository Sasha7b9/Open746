project (Test)

include_directories(../common/MDK_KEIL/CMSIS/
                    src
                    src/Hardware/HAL
                    ../common/BSP
                    ../common/stm32CubeF7/Drivers/STM32F7xx_HAL_Driver/Inc/
                    ../common/stm32CubeF7/Drivers/CMSIS/Device/ST/STM32F7xx/Include/
                    ../common/stm32CubeF7/Drivers/CMSIS/Include/
)

add_definitions(-DSTM32F746xx -DDEVICE -DVS_KEIL)

add_compile_options(/wd4100)
add_compile_options(/wd4242)
add_compile_options(/wd4244)
add_compile_options(/wd4365)
add_compile_options(/wd4459)
add_compile_options(/wd4464)
add_compile_options(/wd4514)
add_compile_options(/wd4820)
add_compile_options(/wd5045)
add_compile_options(/wd5219)
add_compile_options(/wd5220)

SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -MP -Wall")


file(GLOB BSP           ../common/BSP/*.*)
file(GLOB SRC           src/*.*)
file(GLOB DISPLAY       src/Display/*.*)
file(GLOB DISPLAY_TOUCH src/Display/Touch/*.*)
file(GLOB HARDWARE      src/Hardware/*.*)
file(GLOB HARDWARE_HAL  src/Hardware/HAL/*.*)

source_group(BSP           FILES ${BSP})
source_group(src           FILES ${SRC})
source_group(Display       FILES ${DISPLAY})
source_group(Display/Touch FILES ${DISPLAY_TOUCH})
source_group(Hardware      FILES ${HARDWARE})
source_group(Hardware/HAL  FILES ${HARDWARE_HAL})

add_library(${PROJECT_NAME} ${BSP} ${SRC}
                            ${DISPLAY} ${DISPLAY_TOUCH}
                            ${HARDWARE} ${HARDWARE_HAL}
)
