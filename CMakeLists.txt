set(requires
    "AsyncTCP"
)

# register_component() is now deprecated and will be removed in IDF v.5
# See: https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-guides/build-system.html#no-longer-available-in-cmake
set(sources
    "src/AsyncEventSource.cpp"
    "src/AsyncWebSocket.cpp"
    "src/SPIFFSEditor.cpp"
    "src/WebAuthentication.cpp"
    "src/WebHandlers.cpp"
    "src/WebRequest.cpp"
    "src/WebResponses.cpp"
    "src/WebServer.cpp"
)

idf_component_register(
    SRCS "${sources}"
    INCLUDE_DIRS "src"
    REQUIRES "${requires}"
)

#find_library(md5lib mbedtls_esp32)
#target_link_libraries(${COMPONENT_TARGET} PUBLIC ${md5lib})

target_compile_definitions(${COMPONENT_TARGET} PUBLIC -DESP32)
target_compile_options(${COMPONENT_TARGET} PRIVATE -fno-rtti)
