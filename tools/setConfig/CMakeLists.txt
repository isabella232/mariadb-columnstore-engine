
include_directories( ${ENGINE_COMMON_INCLUDES} )

configure_file("${CMAKE_CURRENT_SOURCE_DIR}/configxml.sh.in" "${CMAKE_CURRENT_SOURCE_DIR}/configxml.sh" @ONLY)

########### next target ###############

set(setConfig_SRCS main.cpp)

add_executable(mcsSetConfig ${setConfig_SRCS})

target_link_libraries(mcsSetConfig ${ENGINE_LDFLAGS} ${NETSNMP_LIBRARIES} ${MARIADB_CLIENT_LIBS} ${ENGINE_EXEC_LIBS})

install(TARGETS mcsSetConfig DESTINATION ${ENGINE_BINDIR} COMPONENT columnstore-engine)

install(PROGRAMS configxml.sh DESTINATION ${ENGINE_BINDIR} COMPONENT columnstore-engine)

