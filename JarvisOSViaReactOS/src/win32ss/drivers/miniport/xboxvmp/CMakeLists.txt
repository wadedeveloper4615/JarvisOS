
list(APPEND SOURCE
    xboxvmp.c
    xboxvmp.h)

add_library(xboxvmp MODULE
    ${SOURCE}
    xboxvmp.rc)

set_module_type(xboxvmp kernelmodedriver)
add_importlibs(xboxvmp ntoskrnl videoprt)
add_cd_file(TARGET xboxvmp DESTINATION jarvisos/system32/drivers FOR all)
add_registry_inf(xboxvmp_reg.inf)
