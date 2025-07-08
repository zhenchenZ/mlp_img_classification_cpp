# Create a static library target
add_library(libmlp STATIC
    MLP_Layer.cpp
    MLP_Network.cpp
    MLP_Layer_SGD.cpp
    MLP_Network_SGD.cpp
    MLP_Layer_ADAM.cpp
    MLP_Network_ADAM.cpp
    # Optionally you can list headers for IDE browsing
    MLP_Layer.h
    MLP_Network.h
    MLP_Layer_SGD.h
    MLP_Network_SGD.h
    MLP_Layer_ADAM.h
    MLP_Network_ADAM.h
)

# Specify C++20
target_compile_features(libmlp PRIVATE cxx_std_20)

# If your compiler needs stdc++fs, link it (old GCC)
if(CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
    target_link_libraries(libmlp PRIVATE stdc++fs)
endif()

# Optionally suppress warnings
# (Not generally recommended—better to fix warnings)
# But to reproduce warn_off:
if(MSVC)
    target_compile_options(libmlp PRIVATE /W0)
else()
    target_compile_options(libmlp PRIVATE -w)
endif()

# Make headers visible to dependents
target_include_directories(libmlp
    PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}
)
