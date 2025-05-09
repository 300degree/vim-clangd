add_library(cjson STATIC cJSON/cJSON.c
                         cJSON/cJSON_Utils.c)
target_include_directories(cjson PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/cJSON)

if(ENABLE_TESTS)
	add_subdirectory(googletest)
endif()
