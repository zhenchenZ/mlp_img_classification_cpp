# Create the executable
add_executable(irm_mlp_test
    irm_mlp_test.cpp
)

# Link the internal libraries
target_link_libraries(irm_mlp_test
    PRIVATE
        libmlp
        libread
)

# Add include directories for headers
target_include_directories(irm_mlp_test
    PRIVATE
        ${CMAKE_SOURCE_DIR}/libmlp
        ${CMAKE_SOURCE_DIR}/libread
)

# Use C++20
target_compile_features(irm_mlp_test PRIVATE cxx_std_20)

# If using GCC before version 9, link stdc++fs
if(CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
    target_link_libraries(irm_mlp_test PRIVATE stdc++fs)
endif()
