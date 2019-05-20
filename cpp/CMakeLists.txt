project(OmegaMaxEnt)
enable_language(C CXX)

find_package(BLAS REQUIRED)
include_directories(${BLAS_INCLUDE_DIRS})

find_package(LAPACK REQUIRED)
include_directories(${LAPACK_INCLUDE_DIRS})

find_package(FFTW REQUIRED)
include_directories(${FFTW_INCLUDE_DIRS})

find_package(GSL REQUIRED)
include_directories(${GSL_INCLUDE_DIRS})

add_executable(OmegaMaxEnt graph_2D.cpp graph_3D.cpp generique.cpp OmegaMaxEnt_data.cpp OmegaMaxEnt_main.cpp)

target_compile_options(OmegaMaxEnt PRIVATE -std=c++11 -O0)

target_compile_definitions(OmegaMaxEnt PRIVATE ARMA_DONT_USE_WRAPPER)

target_link_libraries(OmegaMaxEnt ${BLAS_LIBRARIES} ${LAPACK_LIBRARIES} ${GSL_LIBRARIES} ${FFTW_LIBRARIES})

install(TARGETS OmegaMaxEnt DESTINATION bin)

