# ------------------------------------------------------------
# Target: mlio-protobuf
# ------------------------------------------------------------

protobuf_generate_cpp(
    #SRCS
        _PROTOBUF_CXX_SRCS
    #HDRS
        _PROTOBUF_CXX_HDRS
    #PROTOS
        recordio_protobuf.proto
)

add_library(mlio-protobuf OBJECT
    ${_PROTOBUF_CXX_SRCS}
)

target_link_libraries(mlio-protobuf
    PUBLIC
        protobuf::libprotobuf
)

set_target_properties(mlio-protobuf PROPERTIES
    CXX_CLANG_TIDY
        ""
    CXX_INCLUDE_WHAT_YOU_USE
        ""
)

# Files generated by protoc cause lots of non-actionable warnings.
target_compile_options(mlio-protobuf
    PRIVATE
        -w
)
