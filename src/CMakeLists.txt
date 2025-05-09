include_directories(${CMAKE_SOURCE_DIR}/include)
add_executable(${PROJECT_NAME}
			   ${CMAKE_CURRENT_SOURCE_DIR}/main.c)
target_link_libraries(${PROJECT_NAME} PRIVATE cjson)
