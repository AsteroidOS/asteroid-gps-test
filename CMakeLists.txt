cmake_minimum_required(VERSION 3.10.0)

project(
	asteroid-gps-test
	VERSION 2.1.0
	DESCRIPTION "A gps test app for AsteroidOS"
)

find_package(ECM REQUIRED NO_MODULE)
find_package(AsteroidApp6 REQUIRED)

set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH} ${ASTEROID_MODULE_PATH})

include(FeatureSummary)
include(GNUInstallDirs)
include(ECMFindQmlModule)
include(Asteroid6CMakeSettings)
include(Asteroid6Translations)

ecm_find_qmlmodule(QtPositioning 6.11)

add_subdirectory(src)

configure_file(
	${CMAKE_CURRENT_SOURCE_DIR}/asteroid-gps-test.in
	${CMAKE_BINARY_DIR}/asteroid-gps-test
	@ONLY
)

install(
	PROGRAMS ${CMAKE_BINARY_DIR}/asteroid-gps-test
	DESTINATION ${CMAKE_INSTALL_BINDIR}
)

build_translations(i18n)
generate_desktop(${CMAKE_SOURCE_DIR} asteroid-gps-test)

feature_summary(WHAT ALL FATAL_ON_MISSING_REQUIRED_PACKAGES)
