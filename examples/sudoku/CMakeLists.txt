PROTOBUF_GENERATE_RPC(PROTO_SRCS sudoku.proto)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-error=conversion -Wno-extra")
include_directories(${PROJECT_BINARY_DIR})

add_library(sudoku_proto2 ${PROTO_SRCS})

#TODO set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-error=conversion")

add_executable(protobuf_rpc_sudoku_client2 client.cc)
target_link_libraries(protobuf_rpc_sudoku_client2 sudoku_proto2 muduo_protorpc2)

add_executable(protobuf_rpc_sudoku_server2 server.cc)
target_link_libraries(protobuf_rpc_sudoku_server2 sudoku_proto2 muduo_protorpc2)
