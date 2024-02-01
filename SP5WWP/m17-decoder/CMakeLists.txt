# Compile m17-decoder-sym

set(m17_decoder_SRC
  m17-decoder-sym.c
)

include_directories(${libm17_SRC_DIR})

add_executable(m17-decoder-sym ${m17_decoder_SRC})

target_link_libraries(m17-decoder-sym m17 ${MATH_LIBRARIES} ${STATIC_LNK})

install(TARGETS m17-decoder-sym
  DESTINATION ${CMAKE_INSTALL_BINDIR}
)
