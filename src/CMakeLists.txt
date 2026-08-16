add_library(asteroid-gps-test main.cpp)
set_target_properties(asteroid-gps-test PROPERTIES PREFIX "")

asteroid_app_qml_module(
  asteroid-gps-test
	main.qml
)

target_link_libraries(
	asteroid-gps-test
	PUBLIC
		Asteroid::AsteroidApp6
)

install(
	TARGETS asteroid-gps-test
	DESTINATION ${CMAKE_INSTALL_LIBDIR}
)
