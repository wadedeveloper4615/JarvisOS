
include_directories(BEFORE ${JARVISOS_SOURCE_DIR}/sdk/include/jarvisos/wine)

list(APPEND SOURCE
    cred.c
    crypt.c
    crypt_lmhash.c
    crypt_md4.c
    crypt_md5.c
    crypt_sha.c
    eventlog.c
    lsa.c
    registry.c
    security.c
    service.c
    precomp.h)

add_executable(advapi32_winetest ${SOURCE} testlist.c)

if(USE_CLANG_CL OR (NOT MSVC))
    add_target_compile_flags(advapi32_winetest "-Wno-format")
endif()

set_module_type(advapi32_winetest win32cui)
add_importlibs(advapi32_winetest advapi32 ole32 user32 msvcrt kernel32 ntdll)
add_pch(advapi32_winetest precomp.h SOURCE)
add_rostests_file(TARGET advapi32_winetest)
