CMAKE_MINIMUM_REQUIRED( VERSION 2.8.3 )

PROJECT( Squirrel3 )

OPTION( SQUIRREL_BUILD_64BIT_LIB "Build the 64-bit version of squirrel/sqstdlib." OFF )
OPTION( SQUIRREL_BUILD_VM_ONLY "Build only the Squirrel VM without the compiler." OFF )
OPTION( SQUIRREL_NO_GC "Disable garbage collection in the Squirrel VM." OFF )
OPTION( SQUIRREL_UNICODE_ENABLED "If enabled the Squirrel VM and compiler will use 16-bit character strings." OFF )

# remove SL security warnings with Visual C++
if(COMPILER_MSVC)
    add_definitions(-D_CRT_SECURE_NO_DEPRECATE)
endif()

ADD_SUBDIRECTORY( squirrel )
ADD_SUBDIRECTORY( sqstdlib )
ADD_SUBDIRECTORY( sq )