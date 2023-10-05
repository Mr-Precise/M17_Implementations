
set(m17_packet_encode_SRC
    m17-packet-encode.c
    crc.c
    crc.h
)

set(m17_packet_decode_SRC
    m17-packet-decode.c
    viterbi.c
    crc.c
)

add_executable(m17-packet-encode ${m17_packet_encode_SRC})
add_executable(m17-packet-decode ${m17_packet_decode_SRC})

target_link_libraries(m17-packet-encode ${MATH_LIBRARIES})
target_link_libraries(m17-packet-decode ${MATH_LIBRARIES})

install(TARGETS m17-packet-encode m17-packet-decode
  DESTINATION ${CMAKE_INSTALL_BINDIR}
)
