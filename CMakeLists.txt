CMAKE_MINIMUM_REQUIRED( VERSION 2.8.3 )

PROJECT( Squirrel3 )

OPTION( SQUIRREL_BUILD_64BIT_LIB "Build the 64-bit version of squirrel/sqstdlib." ON )
OPTION( SQUIRREL_BUILD_VM_ONLY "Build only the Squirrel VM without the compiler." OFF )
OPTION( SQUIRREL_NO_GC "Disable garbage collection in the Squirrel VM." OFF )
OPTION( SQUIRREL_UNICODE_ENABLED "If enabled the Squirrel VM and compiler will use 16-bit character strings." OFF )
OPTION( ENABLE_64BIT "Build the 64-bit version of squirrel/sqstdlib/sq. If the system architecture is 64-bit then this has no effect." OFF )
OPTION( ENABLE_UNICODE "Compile squirrel/sqstdlib/sq with wide string support. Only works on Windows platforms." OFF )

SET( SQUIRREL_COMPILE_FLAGS "-O2 -s -fno-exceptions -fno-rtti" )

#
# Unicode support (currently Windows/MSVC only!)
#
IF( ENABLE_UNICODE )
  IF(COMPILER_MSVC)
    ADD_DEFINITIONS(-DSQUNICODE)
  ELSE()
    MESSAGE( "Unicode is only supported on Windows/MSVC." )
  ENDIF()
ENDIF( ENABLE_UNICODE )

#
# 64-bit support
#
IF( ENABLE_64BIT )
    MESSAGE( "Building Squirrel as 64-bit." )
    ADD_DEFINITIONS(-D_SQ64)
    
    IF( CMAKE_COMPILER_IS_GNUCXX )
        SET( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -m64" )
    ENDIF()
ENDIF( ENABLE_64BIT )

#
# MSVC-specific settings
#
# Remove security warnings with Visual C++
#
IF( COMPILER_MSVC )
    ADD_DEFINITIONS( -D_CRT_SECURE_NO_DEPRECATE )
ENDIF()

SET( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${SQUIRREL_COMPILE_FLAGS}" )

ADD_SUBDIRECTORY( squirrel )
ADD_SUBDIRECTORY( sqstdlib )
ADD_SUBDIRECTORY( sq )
