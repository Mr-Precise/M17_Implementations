# Compile m17-coder-sym

set(m17_coder_SRC
  m17-coder-sym.c
)

include_directories(${libm17_SRC_DIR})

add_executable(m17-coder-sym ${m17_coder_SRC})

target_link_libraries(m17-coder-sym m17 ${MATH_LIBRARIES} ${STATIC_LNK})

install(TARGETS m17-coder-sym
  DESTINATION ${CMAKE_INSTALL_BINDIR}
)
