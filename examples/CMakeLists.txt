OPTION ( WITH_EXAMPLES "Build the examples" OFF )

IF ( WITH_EXAMPLES )
    ADD_SUBDIRECTORY ( plain-c )
    ADD_SUBDIRECTORY ( cpp )
ENDIF ()

