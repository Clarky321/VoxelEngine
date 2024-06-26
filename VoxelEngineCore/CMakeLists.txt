# Установка минимальной версии CMake
cmake_minimum_required(VERSION 3.12)

# Определение названия проекта VoxelEngineCore
set(ENGINE_PROJECT_NAME VoxelEngineCore)

# Список публичных заголовочных файлов
set(ENGINE_PUBLIC_INCLUDES
	includes/Window.hpp
	includes/Events.hpp
)

# Список приватных исходных файлов
set(ENGINE_PRIVATE_SOURCES
	src/Window.cpp	
	src/Events.cpp
)

# Общий список исходных файлов
set(ENGINE_ALL_SOURCE
	${ENGINE_PUBLIC_INCLUDES}
	${ENGINE_PRIVATE_SOURCES}
)

# Создание статической библиотеки с названием VoxelEngineCore
add_library(${ENGINE_PROJECT_NAME} STATIC ${ENGINE_ALL_SOURCE})

# Группировка файлов в структуру проекта в IDE
source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${ENGINE_ALL_SOURCE})

# Добавление путей к заголовочным файлам для внешних пользователей и для компиляции
target_include_directories(${ENGINE_PROJECT_NAME}
	PUBLIC
		includes
	PRIVATE
		src
)

# Установка стандарта C++ для компиляции
target_compile_features(${ENGINE_PROJECT_NAME} PUBLIC cxx_std_17)

# ------------------------------------------------------------------------------------- #

# Добавление подмодуля GLFW и его сборка
add_subdirectory(../external/glfw ${CMAKE_CURRENT_BINARY_DIR}/glfw)
# Линковка с библиотекой GLFW
target_link_libraries(${ENGINE_PROJECT_NAME} PUBLIC glfw)

# Добавление подмодуля GLEW и его сборка
add_subdirectory(../external/glew ${CMAKE_CURRENT_BINARY_DIR}/glew)
# Линковка с библиотекой GLEW
target_link_libraries(${ENGINE_PROJECT_NAME} PUBLIC libglew_static)