# ============================================================================
# Copyright (c) 2015 <provider-name>
# All rights reserved.
#
# See COPYING file for license information.
# ============================================================================

##############################################################################
# @file  CMakeLists.txt
# @brief Build configuration of software.
##############################################################################


# ============================================================================
# library target(s)
# ============================================================================

# Add library target for each library using basis_add_library().
#
# This command can not only be used to build libraries from C/C++, but also source
# code written in other programming languages such as Java, Python, Perl,
# MATLAB, and Bash. Note that here we consider modules written in a scripting
# language which are no executables but to be included by other scripts written
# in the particular language as libraries.
#
# Note: Public modules written in a scripting language such as Python, Perl,
#       MATLAB, or Bash which are intended for use by other packages should
#       be placed in the lib/[<lang>/]grl/ directory,
#       where <lang> is the language name in lowercase and is optional.
#       BASIS will automatically add a library build target for these modules.
if(FUSIONTRACK_FOUND)
basis_include_directories(${GRL_INCLUDE_DIRS}/thirdparty/vrep/include ${FUSIONTRACK_INCLUDE_DIRS} ${grl_INCLUDE_DIRS}/thirdparty/vrep/include ${FLATBUFFERS_INCLUDE_DIRS})
basis_add_library(v_repExtAtracsysFusionTrack SHARED v_repExtAtracsysFusionTrack.cpp )
basis_target_link_libraries(v_repExtAtracsysFusionTrack ${Boost_LIBRARIES}   ${CMAKE_THREAD_LIBS_INIT} ${FUSIONTRACK_LIBRARIES}  v_repLib  ${FLATBUFFERS_STATIC_LIB})
basis_add_dependencies(v_repExtAtracsysFusionTrack grlflatbuffers)
endif()


# ============================================================================
# executable target(s)
# ============================================================================

# Add executable target for each executable program using basis_add_executable().
#
# This command can not only be used to build executables from C/C++, but also
# source code written in other programming languages such as Java, Python, Perl,
# MATLAB, and Bash.


