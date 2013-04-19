SET( INCLUDE_DIRS
    ${PROJECT_SOURCE_DIR}/include
)

SET( CMAKE_INCLUDE_CURRENT_DIR ON )

INCLUDE_DIRECTORIES( ${INCLUDE_DIRS} )

SET( SOURCE_FILES
    sqstdblob.cpp
    sqstdio.cpp
    sqstdstream.cpp
    sqstdmath.cpp
    sqstdsystem.cpp
    sqstdstring.cpp
    sqstdaux.cpp
    sqstdrex.cpp
)

ADD_LIBRARY( sqstdlib
    STATIC
    ${INCLUDE_FILES}
    ${SOURCE_FILES}
)

# Export the include directory.
SET( SQSTDLIB_INCLUDE_DIRS ${INCLUDE_DIRS} PARENT_SCOPE )