project(tipping)

set(EOSIO_WASM_OLD_BEHAVIOR "Off")
find_package(eosio.cdt)

add_contract( tipping tipping tipping.cpp )
target_include_directories( tipping PUBLIC ${CMAKE_SOURCE_DIR}/../include )
target_ricardian_directory( tipping ${CMAKE_SOURCE_DIR}/../ricardian )