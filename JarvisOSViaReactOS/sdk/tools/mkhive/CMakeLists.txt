
list(APPEND SOURCE
    binhive.c
    cmi.c
    mkhive.c
    reginf.c
    registry.c
    rtl.c)

add_host_tool(mkhive ${SOURCE})
target_include_directories(mkhive PRIVATE ${JARVISOS_SOURCE_DIR}/sdk/lib/rtl)
target_compile_definitions(mkhive PRIVATE -DMKHIVE_HOST)
if(NOT MSVC)
    add_target_compile_flags(mkhive "-fshort-wchar")
endif()

target_link_libraries(mkhive PRIVATE host_includes unicode cmlibhost inflibhost)
