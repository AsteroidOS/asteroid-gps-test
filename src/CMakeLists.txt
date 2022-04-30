add_library(asteroid-gps-test main.cpp resources.qrc)
set_target_properties(asteroid-gps-test PROPERTIES PREFIX "" SUFFIX "")

target_link_libraries(asteroid-gps-test PUBLIC
	AsteroidApp)

install(TARGETS asteroid-gps-test
	DESTINATION ${CMAKE_INSTALL_BINDIR})