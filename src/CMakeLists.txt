${POD_NAME}add_definitions(-DBASE_PATH="${BASE_PATH}")
add_library(${POD_NAME} SHARED path_util.c)

# make the shared library public
pods_install_libraries(${POD_NAME})
#make the header public
pods_install_headers(path_util.h DESTINATION path_util)

pods_install_pkg_config_file(${POD_NAME}
    LIBS -l${POD_NAME}
    REQUIRES
    VERSION 0.0.1)
