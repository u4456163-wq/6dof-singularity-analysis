cmake_minimum_required(VERSION 3.8)
project(robot_6dof_description)

find_package(ament_cmake REQUIRED)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  set(ament_cmake_copyright_FOUND TRUE)
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

# Instalar carpetas de recursos (Asegúrate que estos nombres existan en src)
install(DIRECTORY
  launch
  meshes
  rviz
  urdf
  worlds
  DESTINATION share/${PROJECT_NAME}
)

ament_package()
