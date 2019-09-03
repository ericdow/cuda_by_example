# collect source files
file( GLOB  cu  *.cu)

set(libs_to_link 
  ${OPENGL_LIBRARIES} 
  ${GLUT_LIBRARY} 
)

set(include_dirs 
  ${OPENGL_INCLUDE_DIRS} 
  ${GLUT_INCLUDE_DIR} 
)

# build each source file into separate executable
foreach(file ${cu})
  get_filename_component(exe ${file} NAME_WE)
  CUDA_ADD_EXECUTABLE(${exe} ${file})
  target_link_libraries(${exe} ${libs_to_link})
  target_include_directories(${exe} PUBLIC ${include_dirs})
endforeach()

