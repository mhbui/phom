# This file is automatically generated from cmake.toml - DO NOT EDIT
# See https://github.com/build-cpp/cmkr for more information

# Create a configure-time dependency on cmake.toml to improve IDE support
if(CMKR_ROOT_PROJECT)
	configure_file(cmake.toml cmake.toml COPYONLY)
endif()

# Target: hello-test
if(PHOM_BUILD_TESTS) # build-tests
	set(CMKR_TARGET hello-test)
	enable_testing()
	include(GoogleTest)

	set(hello-test_SOURCES
		cmake.toml
		hello_test.cc
	)

	add_executable(hello-test)

	target_sources(hello-test PRIVATE ${hello-test_SOURCES})
	source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${hello-test_SOURCES})

	target_link_libraries(hello-test PRIVATE
		GTest::gtest
		GTest::gtest_main
		GTest::gmock
		GTest::gmock_main
	)

	get_directory_property(CMKR_VS_STARTUP_PROJECT DIRECTORY ${PROJECT_SOURCE_DIR} DEFINITION VS_STARTUP_PROJECT)
	if(NOT CMKR_VS_STARTUP_PROJECT)
		set_property(DIRECTORY ${PROJECT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT hello-test)
	endif()

	gtest_discover_tests(hello-test)

endif()
