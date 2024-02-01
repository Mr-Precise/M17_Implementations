
set(m17_packet_encode_SRC
    m17-packet-encode.c
)

set(m17_packet_decode_SRC
    m17-packet-decode.c
)

include_directories(${libm17_SRC_DIR})

add_executable(m17-packet-encode ${m17_packet_encode_SRC})
add_executable(m17-packet-decode ${m17_packet_decode_SRC})

target_link_libraries(m17-packet-encode m17 ${MATH_LIBRARIES} ${STATIC_LNK})
target_link_libraries(m17-packet-decode m17 ${MATH_LIBRARIES} ${STATIC_LNK})

install(TARGETS m17-packet-encode m17-packet-decode
  DESTINATION ${CMAKE_INSTALL_BINDIR}
)
