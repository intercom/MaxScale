add_library(MySQLClient SHARED mysql_client.c mysql_common.c)
target_link_libraries(MySQLClient log_manager )
install(TARGETS MySQLClient DESTINATION ${MAXSCALE_LIBDIR})

add_library(MySQLBackend SHARED mysql_backend.c mysql_common.c)
target_link_libraries(MySQLBackend log_manager )
install(TARGETS MySQLBackend DESTINATION ${MAXSCALE_LIBDIR})

add_library(telnetd SHARED telnetd.c)
target_link_libraries(telnetd log_manager )
install(TARGETS telnetd DESTINATION ${MAXSCALE_LIBDIR})

add_library(HTTPD SHARED httpd.c)
target_link_libraries(HTTPD log_manager )
install(TARGETS HTTPD DESTINATION ${MAXSCALE_LIBDIR})

if(BUILD_TESTS)
  add_library(testprotocol SHARED testprotocol.c)
  install(TARGETS testprotocol DESTINATION ${MAXSCALE_LIBDIR})
  add_subdirectory(test)
endif()

add_library(maxscaled SHARED maxscaled.c)
target_link_libraries(maxscaled log_manager )
install(TARGETS maxscaled DESTINATION ${MAXSCALE_LIBDIR})





