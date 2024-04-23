# Установка минимальной версии CMake
cmake_minimum_required(VERSION 3.12)

# Определение названия проекта
set(PROJECT_NAME VoxelEngine)
project(${PROJECT_NAME})

# Добавления поддиректории для модуля PixelEngineCore (ядро движка)
add_subdirectory(VoxelEngineCore)

# Добавления поддиректории для модуля PixelEngineEditor (запускаем файл приложения)
add_subdirectory(VoxelEngineEditor)

# Установка PixelEngineEditor в качестве стартового проекта для Visual Studio
set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT VoxelEngineEditor)