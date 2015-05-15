ADD_EXECUTABLE ( c_apartner apartner.c snap7.h )
TARGET_LINK_LIBRARIES ( c_apartner snap7 )

ADD_EXECUTABLE ( c_client client.c snap7.h )
TARGET_LINK_LIBRARIES ( c_client snap7 )

ADD_EXECUTABLE ( c_ppartner ppartner.c snap7.h )
TARGET_LINK_LIBRARIES ( c_ppartner snap7 )

ADD_EXECUTABLE ( c_server server.c snap7.h )
TARGET_LINK_LIBRARIES ( c_server snap7 )

