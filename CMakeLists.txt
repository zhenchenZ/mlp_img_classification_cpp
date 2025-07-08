cmake_minimum_required(VERSION 3.14)
project(mlp_img_classification_cpp LANGUAGES CXX)

# C++20
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Add subdirectories
add_subdirectory(libmlp)
add_subdirectory(libread)
add_subdirectory(irm/irm_train_sgd)
add_subdirectory(irm/irm_test)
