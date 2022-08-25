# CMakeList.txt : projet CMake pour FirstProject_ImGui, incluez la source et définissez
# la logique spécifique au projet ici.
#
cmake_minimum_required (VERSION 3.8)

find_package(glfw3 CONFIG REQUIRED)
find_package(imgui CONFIG REQUIRED)
find_package(Vulkan REQUIRED)

project("firstproject_imgui")

# Ajoutez une source à l'exécutable de ce projet.
add_executable (FirstProject_ImGui
					"main.cpp"
					"main.hpp"

					"imgui_impl_glfw.cpp"
					"imgui_impl_glfw.h"
					"imgui_impl_vulkan.cpp"
					"imgui_impl_vulkan.h"

					"UseImGUI.cpp"
					"UseImGUI.hpp")


if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET FirstProject_ImGui PROPERTY CXX_STANDARD 20)
endif()

# TODO: Ajoutez des tests et installez des cibles si nécessaire.

target_link_libraries(FirstProject_ImGui PRIVATE imgui::imgui)

target_link_libraries(FirstProject_ImGui PRIVATE glfw)

include_directories(${Vulkan_INCLUDE_DIRS})
target_link_libraries(FirstProject_ImGui PRIVATE Vulkan::Vulkan)
