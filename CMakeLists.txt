cmake_minimum_required(VERSION 3.0)
project( 
    minicom 
    VERSION 1.1.1
    LANGUAGES C
    )

# Override some CMAKE defaults for our own purposes...
set(EXECUTABLE_OUTPUT_PATH deploy)

# Offer an option, CAN bus support on or off...
option(CAN_BUS_SUPPORT "Build with CAN-Bus support" OFF)

# Set some additional flags...some out of box, some depending on options...
set(CMAKE_C_FLAGS ${CMAKE_C_FLAGS} -DPACKAGE_VERSION='"${PROJECT_VERSION}"')
if (CAN_BUS_SUPPORT)
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DUSE_CAN=1")
    set(CAN_BUS_SOURCE "can.c")
else  (CAN_BUS_SUPPORT)
    set(CAN_BUS_SOURCE "")       
endif (CAN_BUS_SUPPORT)

# Add our executable...
add_executable (
    microcom 
    microcom.c 
    ${CAN_BUS_SOURCE} 
    commands.c 
    commands_fsl_imx.c 
    linenoise.c 
    mux.c 
    parser.c 
    serial.c 
    telnet.c
    )
    
target_link_libraries(microcom pthread)

# Set up install rules...
install(TARGETS microcom RUNTIME DESTINATION bin)

