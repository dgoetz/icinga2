# Icinga 2 | (c) 2012 Icinga GmbH | GPLv2+

set(mkembedconfig_SOURCES
  mkembedconfig.c
)

add_executable(mkembedconfig ${mkembedconfig_SOURCES})

set_target_properties (
  mkembedconfig PROPERTIES
  FOLDER Bin
)

macro(MKEMBEDCONFIG_TARGET EmbedInput EmbedOutput)
  add_custom_command(
    OUTPUT ${EmbedOutput}
    COMMAND mkembedconfig
    ARGS ${EmbedInput} ${CMAKE_CURRENT_BINARY_DIR}/${EmbedOutput}
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    DEPENDS mkembedconfig ${EmbedInput}
  )
  set_property(SOURCE ${CMAKE_CURRENT_BINARY_DIR}/${EmbedOutput} PROPERTY EXCLUDE_UNITY_BUILD TRUE)
endmacro()

