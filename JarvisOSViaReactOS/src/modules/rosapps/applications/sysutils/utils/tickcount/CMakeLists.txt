
add_executable(tickcount tickcount.c)
set_module_type(tickcount win32cui UNICODE)
add_importlibs(tickcount ntdll msvcrt kernel32)
add_cd_file(TARGET tickcount DESTINATION jarvisos/bin FOR all)
