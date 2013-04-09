SET( INCLUDE_DIRS
    ${PROJECT_SOURCE_DIR}/include
)

SET( CMAKE_INCLUDE_CURRENT_DIR ON )

INCLUDE_DIRECTORIES( ${INCLUDE_DIRS} )

SET( SQUIRREL_SOURCE_FILES
    sqapi.cpp
    sqbaselib.cpp
    sqfuncstate.cpp
    sqdebug.cpp
    sqlexer.cpp
    sqobject.cpp
    sqcompiler.cpp
    sqstate.cpp
    sqtable.cpp
    sqmem.cpp
    sqvm.cpp
    sqclass.cpp
)

IF( CMAKE_COMPILER_IS_GNUCXX )
    SET( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O2 -fno-exceptions -fno-rtti -Wall -fno-strict-aliasing" )
ENDIF()

ADD_LIBRARY( squirrel
    STATIC
    ${SQUIRREL_SOURCE_FILES}
)

IF( SQUIRREL_BUILD_64BIT_LIB )
    MESSAGE( "Building Squirrel in 64-bit mode." )
    ADD_DEFINITIONS(-D_SQ64)
    # SET_TARGET_PROPERTIES(squirrel PROPERTIES COMPILE_FLAGS "-m64" LINK_FLAGS "-m64")
    IF( CMAKE_COMPILER_IS_GNUCXX )
        SET( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -m64" )
    ENDIF()
ELSE( )
#    MESSAGE( "Building Squirrel in 32-bit mode." )
#    SET_TARGET_PROPERTIES(squirrel PROPERTIES COMPILE_FLAGS "-m32" LINK_FLAGS "-m32")
    IF( CMAKE_COMPILER_IS_GNUCXX )
        SET( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -m32" )
    ENDIF()
ENDIF( SQUIRREL_BUILD_64BIT_LIB )

IF( SQUIRREL_BUILD_VM_ONLY )
    MESSAGE( "Building only the Squirrel VM (no compiler)." )
    ADD_DEFINITIONS(-DNO_COMPILER)
ENDIF( SQUIRREL_BUILD_VM_ONLY )

IF( SQUIRREL_NO_GC )
    MESSAGE( "No garbage collection." )
    ADD_DEFINITIONS(-DNO_GARBAGE_COLLECTOR)
ENDIF( SQUIRREL_NO_GC )

IF( SQUIRREL_UNICODE_ENABLED )
    MESSAGE( "Using 16-bit character strings (unicode enabled)." )
    ADD_DEFINITIONS(-DSQUNICODE)
ENDIF( SQUIRREL_UNICODE_ENABLED )


# Export the include directory.
SET( SQUIRREL_INCLUDE_DIRS ${INCLUDE_DIRS} PARENT_SCOPE )