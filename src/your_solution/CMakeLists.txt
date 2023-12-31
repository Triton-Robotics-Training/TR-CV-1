cmake_minimum_required(VERSION 3.5)
project(your_solution)

# Default to C99
if (NOT CMAKE_C_STANDARD)
    set(CMAKE_C_STANDARD 99)
endif ()

# Default to C++14
if (NOT CMAKE_CXX_STANDARD)
    set(CMAKE_CXX_STANDARD 14)
endif ()

if (CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
    add_compile_options(-Wall -Wextra -Wpedantic)
endif ()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)

add_executable(spin_sol src/spin_sol.cpp src/spin_sol.h)
add_executable(spin_slow_update src/spin_slow_update.cpp src/spin_slow_update.h)
ament_target_dependencies(spin_sol rclcpp std_msgs)
ament_target_dependencies(spin_slow_update rclcpp std_msgs)

install(TARGETS
        spin_sol
        DESTINATION lib/${PROJECT_NAME})

install(TARGETS
        spin_slow_update
        DESTINATION lib/${PROJECT_NAME})


# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

ament_package()
