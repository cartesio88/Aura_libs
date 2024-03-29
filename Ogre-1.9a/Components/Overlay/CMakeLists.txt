#-------------------------------------------------------------------
# This file is part of the CMake build system for OGRE
#     (Object-oriented Graphics Rendering Engine)
# For the latest info, see http://www.ogre3d.org/
#
# The contents of this file are placed in the public domain. Feel
# free to make use of it in any way you like.
#-------------------------------------------------------------------

############################################################
# Overlay optional component
############################################################

PROJECT(OgreOverlay)

# define header and source files for the library
set (HEADER_FILES
	include/OgreOverlayPrerequisites.h
	include/OgreOverlay.h
	include/OgreOverlayContainer.h
	include/OgreOverlayElement.h
	include/OgreOverlayElementCommands.h
	include/OgreOverlayElementFactory.h
	include/OgreOverlayManager.h
	include/OgrePanelOverlayElement.h
	include/OgreTextAreaOverlayElement.h
	include/OgreBorderPanelOverlayElement.h
	include/OgreFont.h
	include/OgreFontManager.h
	include/OgreOverlayProfileSessionListener.h
	include/OgreOverlaySystem.h
)

set (SOURCE_FILES
	src/OgreOverlay.cpp
	src/OgreOverlayContainer.cpp
	src/OgreOverlayElement.cpp
	src/OgreOverlayElementCommands.cpp
	src/OgreOverlayElementFactory.cpp
	src/OgreOverlayManager.cpp
	src/OgrePanelOverlayElement.cpp
	src/OgreTextAreaOverlayElement.cpp
	src/OgreBorderPanelOverlayElement.cpp
	src/OgreFont.cpp
	src/OgreFontManager.cpp
	src/OgreOverlayProfileSessionListener.cpp
	src/OgreOverlaySystem.cpp
)


# Add needed definitions 
add_definitions(-DOGRE_OVERLAY_EXPORTS -D_MT -D_USRDLL)

# include headers
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)
include_directories(${OGRE_SOURCE_DIR}/OgreMain/include)

# setup target
ogre_add_library(OgreOverlay ${OGRE_COMP_LIB_TYPE} ${HEADER_FILES} ${SOURCE_FILES} ${PLATFORM_HEADER_FILES} ${PLATFORM_SOURCE_FILES})
set_target_properties(OgreOverlay PROPERTIES VERSION ${OGRE_SOVERSION} SOVERSION ${OGRE_SOVERSION})
target_link_libraries(OgreOverlay OgreMain ${FREETYPE_LIBRARIES})
if (OGRE_CONFIG_THREADS)
  target_link_libraries(OgreOverlay ${OGRE_THREAD_LIBRARIES})
endif ()

# install 
ogre_config_framework(OgreOverlay)
ogre_config_component(OgreOverlay)

install(FILES ${HEADER_FILES}
  DESTINATION include/OGRE/Overlay
)

