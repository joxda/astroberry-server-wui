cmake_minimum_required(VERSION 2.8)
PROJECT(astroberry-server-wui NONE)

#set (VERSION_MAJOR 2)
#set (VERSION_MINOR 0)
#set (VERSION_RELEASE 5)

#configure_file(${CMAKE_CURRENT_SOURCE_DIR}/files/astroberry.version.cmake ${CMAKE_CURRENT_BINARY_DIR}/astroberry.version)


##!/bin/bash
#sudo apt -y install novnc websockify nginx #certbot python3-certbot-nginx
#sudo mkdir /etc/selfsigned/
#sudo openssl req -new -x509 -days 365 -nodes -out /etc/selfsigned/self.pem -keyout /etc/selfsigned/key.pem


set(CONFIG_INSTALL_DIR "/etc")
set(WWW_INSTALL_DIR "/var/www")

if (${CMAKE_SYSTEM_NAME} MATCHES "Linux")
	install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/files/astroberry DESTINATION ${CONFIG_INSTALL_DIR}/nginx/sites-available)
        install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/files/astroberry_ssl DESTINATION ${CONFIG_INSTALL_DIR}/nginx/sites-available)
	install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/files/astroberry.crt DESTINATION ${CONFIG_INSTALL_DIR}/ssl)
	install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/files/astroberry.key DESTINATION ${CONFIG_INSTALL_DIR}/ssl)
        install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/files/html DESTINATION ${WWW_INSTALL_DIR})
	install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/files/gpspanel DESTINATION ${WWW_INSTALL_DIR})
        install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/files/astropanel DESTINATION ${WWW_INSTALL_DIR})
	#install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/files/indiwebmanager DESTINATION ${WWW_INSTALL_DIR})
	#install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/files/novnc DESTINATION ${WWW_INSTALL_DIR})
	install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/files/gpspanel/gpspanel.service DESTINATION ${CONFIG_INSTALL_DIR}/systemd/system)
        install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/files/astropanel/astropanel.service DESTINATION ${CONFIG_INSTALL_DIR}/systemd/system)
	#install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/files/indiwebmanager/indiwebmanager.service DESTINATION ${CONFIG_INSTALL_DIR}/systemd/system)
    #install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/files/novnc/novnc.service DESTINATION ${CONFIG_INSTALL_DIR}/systemd/system)
	#install(FILES ${CMAKE_CURRENT_BINARY_DIR}/astroberry.version DESTINATION ${CONFIG_INSTALL_DIR})
endif()
