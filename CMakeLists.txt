# ---------------------------------------------------------
cmake_minimum_required(VERSION 2.6)

if(COMMAND cmake_policy)
   cmake_policy(SET CMP0003 NEW)
endif(COMMAND cmake_policy)

set(CMAKE_MODULE_PATH
  "${CMAKE_CURRENT_SOURCE_DIR}/CMake"
  "${CMAKE_CURRENT_SOURCE_DIR}/CMake/Utils"
  "${CMAKE_CURRENT_SOURCE_DIR}/CMake/Packages"
)

# Include necessary submodules
include(CMakeDependentOption)
include(CheckCXXCompilerFlag)
include(MacroLogFeature)
include(PreprocessorUtils)

# Ogre
subdirs(Ogre-1.9a)