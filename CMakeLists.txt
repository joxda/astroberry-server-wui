cmake_minimum_required(VERSION 2.8)
PROJECT(tahti-server-wui NONE)


set(WWW_INSTALL_DIR "/var/www")

if (${CMAKE_SYSTEM_NAME} MATCHES "Linux")
	install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/files/html DESTINATION ${WWW_INSTALL_DIR})
endif()
