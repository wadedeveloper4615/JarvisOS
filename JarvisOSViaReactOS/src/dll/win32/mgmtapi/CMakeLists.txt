
add_definitions(-D__WINESRC__)
include_directories(${JARVISOS_SOURCE_DIR}/sdk/include/jarvisos/wine)
spec2def(mgmtapi.dll mgmtapi.spec)

list(APPEND SOURCE
    mgmtapi.c
    ${CMAKE_CURRENT_BINARY_DIR}/mgmtapi_stubs.c
    ${CMAKE_CURRENT_BINARY_DIR}/mgmtapi.def)

add_library(mgmtapi MODULE ${SOURCE})
set_module_type(mgmtapi win32dll)
target_link_libraries(mgmtapi wine)
add_importlibs(mgmtapi msvcrt kernel32 ntdll)
add_cd_file(TARGET mgmtapi DESTINATION jarvisos/system32 FOR all)
