# Compile m17-decoder-sym

set(m17_decoder_SRC
  m17-decoder-sym.c
  golay.c
  golay.h
  viterbi.c
  viterbi.h
  crc.c
  crc.h
)

add_executable(m17-decoder-sym ${m17_decoder_SRC})
target_link_libraries(m17-decoder-sym ${MATH_LIBRARIES})

install(TARGETS m17-decoder-sym
  DESTINATION ${CMAKE_INSTALL_BINDIR}
)
