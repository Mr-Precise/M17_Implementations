# Compile libm17

set(EXCLUDE_DIR "/unit_tests/")

# search sources
file(GLOB_RECURSE libm17_SRC "${libm17_SRC_DIR}/**.c")

# exclude unit tests
foreach(TMP_PATH ${libm17_SRC})
  string(FIND ${TMP_PATH} ${EXCLUDE_DIR} EXCLUDE_DIR_FOUND)
  if(NOT ${EXCLUDE_DIR_FOUND} EQUAL -1)
    list(REMOVE_ITEM libm17_SRC ${TMP_PATH})
  endif()
endforeach(TMP_PATH)

include_directories(${libm17_SRC_DIR})

add_library(m17 SHARED ${libm17_SRC})

target_link_libraries(m17 ${MATH_LIBRARIES})

install(TARGETS m17
  DESTINATION ${CMAKE_INSTALL_LIBDIR}
)
