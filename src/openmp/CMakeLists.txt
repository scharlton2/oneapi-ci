cmake_minimum_required (VERSION 3.9)

project (openmp Fortran)

include(GNUInstallDirs)

find_package(OpenMP REQUIRED)

add_executable(openmp openmp_sample.f90)
target_link_libraries(openmp PUBLIC OpenMP::OpenMP_Fortran)

install (TARGETS openmp DESTINATION "${CMAKE_INSTALL_BINDIR}")

include(CTest)

add_test(TestRun openmp)


