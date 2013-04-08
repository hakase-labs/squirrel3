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

# Export the include directory.
SET( SQUIRREL_INCLUDE_DIRS ${INCLUDE_DIRS} PARENT_SCOPE )