# Create a static library target
add_library(libread STATIC
    IRM2D.cpp
    progress_bar.cpp
    gnuplot_utilities.cpp
    timing_functions.cpp

    # Headers (optional for IDE browsing)
    IRM2D.h
    progress_bar.h
    stb_image.h
    stb_image_write.h
    gnuplot_utilities.h
    timing_functions.h
)

# Use C++20
target_compile_features(libread PRIVATE cxx_std_20)

# Disable warnings if you really want the same as warn_off
# (Consider using -Wall -Wextra and fixing warnings instead)
if(MSVC)
    target_compile_options(libread PRIVATE /W0)
else()
    target_compile_options(libread PRIVATE -w)
endif()

# Make headers available to dependents
target_include_directories(libread
    PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}
)

# Link stdc++fs if needed (older GCC)
if(CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
    target_link_libraries(libread PRIVATE stdc++fs)
endif()
