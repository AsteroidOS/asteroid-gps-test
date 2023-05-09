cmake_minimum_required(VERSION 3.6.0)

project(asteroid-gps-test
	VERSION 0.0.1
	DESCRIPTION "A gps test app for AsteroidOS")

find_package(ECM REQUIRED NO_MODULE)
find_package(AsteroidApp REQUIRED)

set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH} ${ASTEROID_MODULE_PATH})

include(FeatureSummary)
include(GNUInstallDirs)
include(ECMFindQmlModule)
include(AsteroidCMakeSettings)
include(AsteroidTranslations)

ecm_find_qmlmodule(QtPositioning 5.2)

add_subdirectory(src)

configure_file(${CMAKE_CURRENT_SOURCE_DIR}/asteroid-gps-test.in
	${CMAKE_BINARY_DIR}/asteroid-gps-test
	@ONLY)

install(PROGRAMS ${CMAKE_BINARY_DIR}/asteroid-gps-test
	DESTINATION ${CMAKE_INSTALL_BINDIR})

build_translations(i18n)
generate_desktop(${CMAKE_SOURCE_DIR} asteroid-gps-test)

feature_summary(WHAT ALL FATAL_ON_MISSING_REQUIRED_PACKAGES)
