PROJECT ( snap7 )
CMAKE_MINIMUM_REQUIRED ( VERSION 2.8.11 )

FIND_PACKAGE ( Threads REQUIRED )

IF ( WIN32 AND NOT MSVC )
    MESSAGE ( FATAL "Currently only MSVC is supported on Windows." )
ENDIF ()

# static libs are disabled for now

# Build shared/static
#OPTION ( BUILD_SHARED "Build shared libraries" ON )
#IF ( BUILD_SHARED )
    SET ( LIBRARY_TYPE SHARED )
#ELSE ()
#    SET ( LIBRARY_TYPE STATIC )
#ENDIF ()

# Core files
SET ( core_SOURCES
    core/s7_client.cpp
    core/s7_isotcp.cpp
    core/s7_micro_client.cpp
    core/s7_partner.cpp
    core/s7_peer.cpp
    core/s7_server.cpp
    core/s7_text.cpp
)
SET ( core_HEADERS
    core/s7_client.h
    core/s7_firmware.h
    core/s7_isotcp.h
    core/s7_micro_client.h
    core/s7_partner.h
    core/s7_peer.h
    core/s7_server.h
    core/s7_text.h
    core/s7_types.h
)

# System files
SET ( sys_SOURCES
    sys/snap_msgsock.cpp
    sys/snap_sysutils.cpp
    sys/snap_tcpsrvr.cpp
    sys/snap_threads.cpp
)
SET ( sys_HEADERS
    sys/snap_msgsock.h
    sys/snap_platform.h
    sys/snap_sysutils.h
    sys/snap_tcpsrvr.h
    sys/snap_threads.h
)
IF ( WIN32 )
    LIST ( APPEND sys_HEADERS sys/win_threads.h )
ELSEIF ( UNIX )
    LIST ( APPEND sys_HEADERS sys/unix_threads.h )
ENDIF ()

# Library files
SET ( lib_SOURCES lib/snap7_libmain.cpp )
SET ( lib_HEADERS lib/snap7_libmain.h )
IF ( WIN32 AND BUILD_SHARED )
    SET ( lib_DEFINITIONS lib/snap7.def )
ENDIF ()

# Dependencies
SET ( DEPENDENCIES )
IF ( UNIX )
    LIST ( APPEND DEPENDENCIES rt )
ENDIF ()

# includes
INCLUDE_DIRECTORIES ( core/ )
INCLUDE_DIRECTORIES ( sys/ )
INCLUDE_DIRECTORIES ( lib/ )

# Build the library
ADD_LIBRARY ( snap7 ${LIBRARY_TYPE}
    ${core_SOURCES} ${core_HEADERS}
    ${sys_SOURCES}  ${sys_HEADERS}
    ${lib_SOURCES}  ${lib_HEADERS}  ${lib_DEFINITIONS}
)
TARGET_LINK_LIBRARIES ( snap7 ${CMAKE_THREAD_LIBS_INIT} ${DEPENDENCIES} )

# install library and headers
INSTALL ( TARGETS snap7
    RUNTIME DESTINATION lib
    ARCHIVE DESTINATION lib
    LIBRARY DESTINATION lib
)
INSTALL (
    FILES
        ${core_HEADERS}
        ${sys_HEADERS}
        ${lib_HEADERS}
    DESTINATION
        include/snap7
)

ADD_SUBDIRECTORY ( examples )

