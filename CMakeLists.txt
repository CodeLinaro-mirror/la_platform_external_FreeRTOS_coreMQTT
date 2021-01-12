
cmake_minimum_required(VERSION 2.8.9)

project (coremqtt)

#
# target coremqtt
#
set(TARGET_LIB_COREMQTT coremqtt)

# sources
set(LIB_COREMQTT_SOURCES
   source/core_mqtt.c
   source/core_mqtt_serializer.c
   source/core_mqtt_state.c
)

include_directories(BEFORE
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/source/include
    ${CMAKE_CURRENT_SOURCE_DIR}/source/interface
    ${CMAKE_CURRENT_SOURCE_DIR}/test/unit-test
    ${CMAKE_CURRENT_SOURCE_DIR}/test/unit-test/logging
)

file(GLOB headers "source/include/*.h" "source/interface/*.h" "test/unit-test/*.h"
        "test/unit-test/logging/*.h")
install(FILES ${headers}
    DESTINATION include)

# build library
add_library(${TARGET_LIB_COREMQTT} SHARED
    ${LIB_COREMQTT_SOURCES})

# install to target
install ( TARGETS ${TARGET_LIB_COREMQTT}
          ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
          LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR} )
