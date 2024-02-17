# Add component into the build system of esp-at project
set(ENV{AT_CUSTOM_COMPONENTS} ${CMAKE_CURRENT_SOURCE_DIR} )

file(GLOB_RECURSE srcs *.c)

set(includes "include")

# Add more required components you need here, separated by spaces
set(require_components at freertos nvs_flash)

idf_component_register(
    SRCS ${srcs}
    INCLUDE_DIRS ${includes}
    REQUIRES ${require_components})

target_link_libraries(${COMPONENT_LIB} INTERFACE "-u esp_at_custom_cmd_regist")