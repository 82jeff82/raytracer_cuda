
cmake_minimum_required(VERSION 3.8 FATAL_ERROR)
project(cmake_and_cuda LANGUAGES CXX CUDA)

include(CTest)

#add_library(particles STATIC
#  randomize.cpp
#  randomize.h
#  particle.cu
#  particle.h
#  v3.cu
#  v3.h
#  )

# Request that particles be built with -std=c++11
# As this is a public compile feature anything that links to particles
# will also build with -std=c++11
#target_compile_features(raytracer PUBLIC cxx_std_11)

# We need to explicitly state that we need all CUDA files in the particle
# library to be built with -dc as the member functions could be called by
# other libraries and executables
#set_target_properties( raytracer
#                       PROPERTIES CUDA_SEPARABLE_COMPILATION ON
#                      )

if(BUILD_TESTING)

  add_executable(raytracer main.cc vec3.h color.h)
  target_compile_options(raytracer PRIVATE -Wall -g3)


  #set_target_properties(particle_test PROPERTIES CUDA_SEPARABLE_COMPILATION ON)
  #target_link_libraries(particle_test PRIVATE particles)

  #add_test(NAME particles_10k COMMAND particle_test 10000 )
  #add_test(NAME particles_256k COMMAND particle_test 256000 )
endif()


