cmake_minimum_required(VERSION 3.27)

project("checo_rpg_io_tests" LANGUAGES CXX)
enable_testing()

# Dependencies and modules
find_package(GTest REQUIRED)
include(GoogleTest)

# Project target
add_executable(${PROJECT_NAME}
	"src/ability_io_tests.cpp"
	"src/character_io_tests.cpp"
	"src/currency_io_tests.cpp"
	"src/entity_io_tests.cpp"
	"src/inventory_io_tests.cpp"
	"src/item_io_tests.cpp"
	"src/stat_io_tests.cpp"
	"src/status_effect_io_tests.cpp"
	"src/test_support.cpp"
)

# Target compile settings
target_compile_features(${PROJECT_NAME} PUBLIC cxx_std_23)

# Link dependencies
target_link_libraries(${PROJECT_NAME}
	PUBLIC
		checo::rpg::io
		checo::rpg::test_support
		GTest::gtest_main
)

# Register tests
gtest_discover_tests(${PROJECT_NAME})
