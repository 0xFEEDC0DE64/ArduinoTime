set(headers
    Time.h
    TimeLib.h
)

set(sources
    DateStrings.cpp
    Time.cpp
)

set(dependencies
    esp_timer
)

idf_component_register(
    INCLUDE_DIRS
        .
    SRCS
        ${headers}
        ${sources}
    REQUIRES
        ${dependencies}
)

target_compile_options(${COMPONENT_TARGET}
    PUBLIC
        -DUSE_FACADE=true
    PRIVATE
        -fstack-reuse=all
        -fstack-protector-all
        -Wno-unused-function
        -Wno-deprecated-declarations
        -Wno-missing-field-initializers
        -Wno-parentheses
)
