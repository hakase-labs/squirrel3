SET( INCLUDE_DIRS
    ${CMAKE_CURRENT_LIST_DIR}/../include
    ${CMAKE_CURRENT_LIST_DIR}
)
INCLUDE_DIRECTORIES( ${INCLUDE_DIRS} )

SET( SOURCE_FILES
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
    ${INCLUDE_FILES}
    ${SOURCE_FILES}
)

# Export the include directory.
SET( SQUIRREL_INCLUDE_DIRS ${INCLUDE_DIRS} PARENT_SCOPE )