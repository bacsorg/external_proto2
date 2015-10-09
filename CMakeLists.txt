cmake_minimum_required(VERSION 3.0)

include(${CMAKE_SOURCE_DIR}/system-config.cmake OPTIONAL)

project(bacs_external)

if(BunsanCMakeBuiltin)
    BunsanCMakeLoad()
else()
    find_package(BunsanCMake CONFIG REQUIRED)
endif()

bunsan_add_protobuf_cxx_library(
    TARGET ${PROJECT_NAME}_pb
    PROTOS
        bacs/external/contest.proto
        bacs/external/external.proto
        bacs/external/language.proto
        bacs/external/result.proto
        bacs/external/submit.proto
    GRPC
    LIBRARIES ${bunsan_common_LIBRARIES}
    INCLUDE_DIRECTORIES ${bunsan_common_INCLUDE_DIRS}
    INSTALL
)

bunsan_install_headers()
#bunsan_install_targets()
bunsan_install_project()

bunsan_include_tests()
