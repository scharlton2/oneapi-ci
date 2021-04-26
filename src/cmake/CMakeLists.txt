cmake_minimum_required (VERSION 3.9)

project (console Fortran)

include(GNUInstallDirs)

add_executable(hello Console1.f90)

install (TARGETS hello DESTINATION "${CMAKE_INSTALL_BINDIR}")

include(CTest)

add_test(TestRun hello)


