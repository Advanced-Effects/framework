cmake_minimum_required(VERSION 3.24)

project(Framework LANGUAGES CXX C)

set(CMAKE_AUTOMOC ON) # this is a setting for Qt macros
set(CMAKE_AUTOUIC ON)
cmake_policy(SET CMP0091 OLD) # not set MSVC default args

##########################
# Options
##########################

set(MUSE_ENABLE_UNIT_TESTS ON)
set(MUSE_MODULE_ACCESSIBILITY ON)
set(MUSE_MODULE_ACTIONS ON)
set(MUSE_MODULE_AUTOBOT ON) # If turned on, project doesn't compile
set(MUSE_MODULE_DIAGNOSTICS ON)
set(MUSE_MODULE_DRAW ON)
set(MUSE_MODULE_DRAW_TESTS OFF)
set(MUSE_MODULE_EXTENSIONS ON)
set(MUSE_MODULE_GLOBAL ON)
set(MUSE_MODULE_GLOBAL_TESTS OFF)
set(MUSE_MODULE_LANGUAGES ON)
set(MUSE_MODULE_LEARN ON)
set(MUSE_MODULE_MULTIINSTANCES ON)
set(MUSE_MODULE_NETWORK ON)
set(MUSE_MODULE_SHORTCUTS ON)
set(MUSE_MODULE_UI ON)
set(MUSE_MODULE_UI_TESTS OFF)
set(MUSE_MODULE_DOCKWINDOW ON)
set(MUSE_MODULE_UPDATE OFF)
set(MUSE_MODULE_WORKSPACE ON)

##########################
# Configure environment
##########################

if (NOT MUSE_FRAMEWORK_PATH)
        set(MUSE_FRAMEWORK_PATH ${PROJECT_SOURCE_DIR})
endif()

set(CMAKE_MODULE_PATH
        ${CMAKE_MODULE_PATH}
        ${CMAKE_CURRENT_SOURCE_DIR}/buildscripts
        ${CMAKE_CURRENT_SOURCE_DIR}/buildscripts/cmake)

include(GetPlatformInfo)
include(GetPaths)
include(DeclareModuleSetup)

include(SetupBuildEnvironment)
include(GetPlatformInfo)
if (MUE_COMPILE_USE_CCACHE)
        include(TryUseCcache)
endif(MUE_COMPILE_USE_CCACHE)

##########################
# Qt setup
##########################
set(QT_MIN_VERSION "6.9.2")
include(SetupQt6)

qt_policy(SET QTP0001 NEW)

set(QT_ADD_STATEMACHINE ON)
set(QT_ADD_LINGUISTTOOLS ON)
set(QT_ADD_CONCURRENT ON)
set(QT_ADD_WEBSOCKET OFF)
set(QT_QPROCESS_SUPPORTED ON)
set(QT_CONCURRENT_SUPPORTED ON)

##########################
# Framework
##########################

add_subdirectory(src)
