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

ADD_LIBRARY( squirrel
    STATIC
    ${SQUIRREL_SOURCE_FILES}
)

IF( SQUIRREL_BUILD_VM_ONLY )
    MESSAGE( "Building only the Squirrel VM (no compiler)." )
    ADD_DEFINITIONS(-DNO_COMPILER)
ENDIF( SQUIRREL_BUILD_VM_ONLY )

IF( SQUIRREL_NO_GC )
    MESSAGE( "No garbage collection." )
    ADD_DEFINITIONS(-DNO_GARBAGE_COLLECTOR)
ENDIF( SQUIRREL_NO_GC )

# Export the include directory.
SET( SQUIRREL_INCLUDE_DIRS ${INCLUDE_DIRS} PARENT_SCOPE )