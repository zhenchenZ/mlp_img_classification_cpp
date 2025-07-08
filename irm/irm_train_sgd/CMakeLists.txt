# Create the executable
add_executable(irm_mlp_train_sgd
    irm_mlp_train_sgd.cpp
)

# Link the internal libraries
target_link_libraries(irm_mlp_train_sgd
    PRIVATE
        libmlp
        libread
)

# Add include directories
target_include_directories(irm_mlp_train_sgd
    PRIVATE
        ${CMAKE_SOURCE_DIR}/libmlp
        ${CMAKE_SOURCE_DIR}/libread
)

# Use C++20
target_compile_features(irm_mlp_train_sgd PRIVATE cxx_std_20)

# Link stdc++fs if needed (old GCC)
if(CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
    target_link_libraries(irm_mlp_train_sgd PRIVATE stdc++fs)
endif()
