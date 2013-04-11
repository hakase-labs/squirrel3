SET( INCLUDE_DIRS
    ${CMAKE_CURRENT_LIST_DIR}/../include
    ${CMAKE_CURRENT_LIST_DIR}
)
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

IF( CMAKE_COMPILER_IS_GNUCXX )
    IF( SQUIRREL_BUILD_64BIT_LIB )
        SET( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O2 -m64 -D_SQ64 -fno-exceptions -fno-rtti -Wall -fno-strict-aliasing" )
    ELSE()
        SET( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O2 -m32 -fno-exceptions -fno-rtti -Wall -fno-strict-aliasing" )
    ENDIF( SQUIRREL_BUILD_64BIT_LIB )
ENDIF()

ADD_LIBRARY( sqstdlib
    STATIC
    ${INCLUDE_FILES}
    ${SOURCE_FILES}
)

# Export the include directory.
SET( SQSTDLIB_INCLUDE_DIRS ${INCLUDE_DIRS} PARENT_SCOPE )