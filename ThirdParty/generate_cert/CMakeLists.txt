find_program(GO_EXECUTABLE NAMES go)
if(GO_EXECUTABLE)
  add_custom_target(generate_cert ALL
    COMMAND GOPATH=${CMAKE_BINARY_DIR}/go ${GO_EXECUTABLE} build -o ${CMAKE_BINARY_DIR}/bin/generate_cert ${CMAKE_CURRENT_SOURCE_DIR}/generate_cert.go
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    SOURCES generate_cert.go
    )
  install(PROGRAMS ${CMAKE_BINARY_DIR}/bin/generate_cert DESTINATION bin)
  list(APPEND ADDITIONAL_MAKE_CLEAN_FILES ${CMAKE_BINARY_DIR}/bin/generate_cert)
  set(ADDITIONAL_MAKE_CLEAN_FILES ${ADDITIONAL_MAKE_CLEAN_FILES} PARENT_SCOPE)
endif()
