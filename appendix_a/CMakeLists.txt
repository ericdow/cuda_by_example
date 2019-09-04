# collect source files
file( GLOB  cu  *.cu)

# build each source file into separate executable
foreach(file ${cu})
  get_filename_component(exe ${file} NAME_WE)
  CUDA_ADD_EXECUTABLE(${exe}_appa ${file})
endforeach()

