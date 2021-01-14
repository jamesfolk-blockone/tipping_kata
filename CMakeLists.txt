project(tipping)
#
cmake_minimum_required(VERSION 3.5)
#
include(ExternalProject)
#                       # if no cdt root is given use default path
#                       # if(EOSIO_CDT_ROOT STREQUAL "" OR NOT EOSIO_CDT_ROOT)
#                       #    find_package(eosio.cdt PATHS ${CMAKE_SOURCE_DIR}/../../eosio.cdt/build)
#                       # endif()
#
find_package(eosio.cdt)
#
message("EOSIO_CDT_ROOT = ${EOSIO_CDT_ROOT}")

#
set(EOSIO_ROOT "/Users/james.folk/eosio/eos/build")
message("EOSIO_ROOT = ${EOSIO_ROOT}")
#
#
ExternalProject_Add(
   tipping_project
   SOURCE_DIR ${CMAKE_SOURCE_DIR}/src
   BINARY_DIR ${CMAKE_BINARY_DIR}/tipping
   CMAKE_ARGS -DCMAKE_TOOLCHAIN_FILE=${EOSIO_CDT_ROOT}/lib/cmake/eosio.cdt/EosioWasmToolchain.cmake
   UPDATE_COMMAND ""
   PATCH_COMMAND ""
   TEST_COMMAND ""
   INSTALL_COMMAND ""
   BUILD_ALWAYS 1
)
#
#
# ExternalProject_Add(
#         kata1_test_project
#         SOURCE_DIR ${CMAKE_SOURCE_DIR}/tests
#         BINARY_DIR ${CMAKE_BINARY_DIR}/tests
#         CMAKE_ARGS -DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE} -DEOSIO_ROOT=${EOSIO_ROOT} -DEOSIO_DEPENDENCY=${EOSIO_DEPENDENCY}
#         TEST_COMMAND ./kata1_test --color_output  --log_level=all -- --verbose
#         INSTALL_COMMAND ""
#         BUILD_ALWAYS 1
# )

ExternalProject_Add(
        kata1_test_project
        # LIST_SEPARATOR | # Use the alternate list separator
        CMAKE_ARGS -DCMAKE_BUILD_TYPE=${TEST_BUILD_TYPE} -DCMAKE_FRAMEWORK_PATH=${TEST_FRAMEWORK_PATH} -DCMAKE_MODULE_PATH=${TEST_MODULE_PATH} -DEOSIO_ROOT=${EOSIO_ROOT} -DLLVM_DIR=${LLVM_DIR}
        SOURCE_DIR ${CMAKE_SOURCE_DIR}/tests
        BINARY_DIR ${CMAKE_BINARY_DIR}/tests
        BUILD_ALWAYS 1
        TEST_COMMAND   ""
        INSTALL_COMMAND ""
)

# message(FATAL_ERROR "EOSIO_DEPENDENCY ${EOSIO_ROOT}")
add_dependencies( kata1_test_project tipping_project)