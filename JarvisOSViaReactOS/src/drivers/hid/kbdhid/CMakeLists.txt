
add_definitions(-DDEBUG_MODE)
include_directories(${JARVISOS_SOURCE_DIR}/src/ntoskrnl/include)
add_library(kbdhid MODULE kbdhid.c kbdhid.rc)
set_module_type(kbdhid kernelmodedriver)
add_importlibs(kbdhid ntoskrnl hal hidparse)
add_cd_file(TARGET kbdhid DESTINATION jarvisos/system32/drivers NO_CAB FOR all)
