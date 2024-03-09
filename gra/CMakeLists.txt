cmake_minimum_required(VERSION 3.0)
project(MyProject)

set(CMAKE_BINARY_DIR ${CMAKE_SOURCE_DIR}/build)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR})

# Ścieżki do folderów
set(SRC_DIR "${CMAKE_SOURCE_DIR}/src")
set(INCLUDE_DIR "${CMAKE_SOURCE_DIR}/include")
set(LIBRARY_DIR "${CMAKE_SOURCE_DIR}/library")

# Ścieżka do folderu zasobów
set(ASSETS_DIR "${CMAKE_SOURCE_DIR}/assets")

# Ustalenie zmiennych z plikami źródłowymi i nagłówkowymi
file(GLOB SRC_FILES "${SRC_DIR}/*.cpp")
file(GLOB HEADER_FILES "${INCLUDE_DIR}/*.h")

# Kopiowanie zasobów do folderu wyjściowego
file(COPY ${ASSETS_DIR} DESTINATION ${CMAKE_BINARY_DIR})

# Ścieżka do biblioteki SFML
set(SFML_DIR "${LIBRARY_DIR}/lib")
set(SFML_INCLUDE_DIR "${LIBRARY_DIR}/include")
set(SFML_LIBRARY_DIR "${LIBRARY_DIR}/lib")
set(SFML_BIN_DIR "${LIBRARY_DIR}/bin")

# Dodanie folderu include
include_directories(${INCLUDE_DIR})

# Dodanie plików źródłowych
add_executable(MyExecutable ${SRC_FILES} ${HEADER_FILES})

link_directories(${SFML_LIBRARY_DIR})

# Dodanie ścieżki do bibliotek SFML
link_directories(${SFML_LIBRARY_DIR})

# Linkowanie z bibliotekami SFML
target_link_libraries(MyExecutable sfml-graphics sfml-window sfml-system sfml-network)