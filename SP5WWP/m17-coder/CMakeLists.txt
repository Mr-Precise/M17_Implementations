# Compile m17-coder-sym

set(m17_coder_SRC
  m17-coder-sym.c
  golay.c
  golay.h
  crc.c
  crc.h
)

add_executable(m17-coder-sym ${m17_coder_SRC})
target_link_libraries(m17-coder-sym ${MATH_LIBRARIES})

install(TARGETS m17-coder-sym
  DESTINATION ${CMAKE_INSTALL_BINDIR}
)
