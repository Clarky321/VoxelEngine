# Установка минимальной версии CMake
cmake_minimum_required(VERSION 3.12)

# Определение названия проекта PixelEngineEditor
set(EDITOR_PROJECT_NAME VoxelEngineEditor)

# Создание исполняемого файла с названием VoxelEngineEditor и указание его исходного файла
add_executable(${EDITOR_PROJECT_NAME}
	src/main.cpp
)

# Линковка исполняемого файла с библиотекой VoxelEngineCore
target_link_libraries(${EDITOR_PROJECT_NAME} VoxelEngineCore)

# Установка стандарта C++ для компиляции
target_compile_features(${EDITOR_PROJECT_NAME} PUBLIC cxx_std_17)

# Установка каталога для вывода исполняемого файла
set_target_properties(${EDITOR_PROJECT_NAME} PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin/)