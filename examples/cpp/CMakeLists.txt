ADD_EXECUTABLE ( cpp_apartner apartner.cpp snap7.cpp snap7.h )
TARGET_LINK_LIBRARIES ( cpp_apartner snap7 )

ADD_EXECUTABLE ( cpp_client client.cpp snap7.cpp snap7.h )
TARGET_LINK_LIBRARIES ( cpp_client snap7 )

ADD_EXECUTABLE ( cpp_ppartner ppartner.cpp snap7.cpp snap7.h )
TARGET_LINK_LIBRARIES ( cpp_ppartner snap7 )

ADD_EXECUTABLE ( cpp_server server.cpp snap7.cpp snap7.h )
TARGET_LINK_LIBRARIES ( cpp_server snap7 )

