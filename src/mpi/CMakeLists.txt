cmake_minimum_required (VERSION 3.9)

project (hello_mpi Fortran)

include(GNUInstallDirs)

find_package(MPI REQUIRED)

add_executable(hello_mpi hello_world_mpi.f90)
target_link_libraries(hello_mpi PUBLIC MPI::MPI_Fortran)

install (TARGETS hello_mpi DESTINATION "${CMAKE_INSTALL_BINDIR}")

include(CTest)

add_test(run_single hello_mpi)

add_test(NAME run_mpi
COMMAND ${MPIEXEC} ${MPIEXEC_NUMPROC_FLAG} 3 ${MPIEXEC_PREFLAGS} $<TARGET_FILE:hello_mpi> ${MPIEXEC_POSTFLAGS}
)


