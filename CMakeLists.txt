cmake_minimum_required(VERSION 3.7 FATAL_ERROR)
project(cuda_by_example)

find_package(CUDA REQUIRED)
find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)

if(CUDA_FOUND)

  set(CUDA_NVCC_FLAGS "-ccbin /usr/bin/gcc;")
  CUDA_SELECT_NVCC_ARCH_FLAGS(ARCH_FLAGS Auto)
  set(CUDA_NVCC_FLAGS ${CUDA_NVCC_FLAGS} ${ARCH_FLAGS})
  # set(CUDA_NVCC_FLAGS ${CUDA_NVCC_FLAGS} -maxrregcount=20)

  # add -Wextra compiler flag for gcc compilations
  if (UNIX)
    set(CUDA_NVCC_FLAGS ${CUDA_NVCC_FLAGS} "-Xcompiler -Wextra")
  endif (UNIX)

  # add debugging to CUDA NVCC flags.  For NVidia's NSight tools.
  set(CUDA_NVCC_FLAGS_DEBUG ${CUDA_NVCC_FLAGS_DEBUG} "-G")

  add_subdirectory (chapter03)
  add_subdirectory (chapter04)
  add_subdirectory (chapter05)
else(CUDA_FOUND)
  message("CUDA is not installed on this system.")
endif()
