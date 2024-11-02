project(
    'example_library',
    'cpp',
    'c',
    version: '0.1',
    default_options: [
        'b_colorout=always',
        'b_lto=true',
        'b_lto_mode=thin',
        'b_lto_threads=4',
        'b_pie=true',
        'b_staticpic=true',
        'b_lundef=true',
        'cpp_std=c++2a',
        'prefer_static=true',
        'werror=true',
        'warning_level=3',
    ],
)

cpp_flags = [
'-Wdouble-promotion',
'-Wduplicated-branches',
'-Wduplicated-cond',
'-Wformat=2',
'-Wlogical-op',
'-Wnull-dereference',
'-Wold-style-cast',
'-Woverloaded-virtual',
'-Wpessimizing-move',
'-Wredundant-move',
'-Wshadow',
'-Wunused',
'-Wuninitialized',
'-Wuseless-cast',
]

dep_list = []

# statically link libstdc++ (https://mesonbuild.com/Creating-Linux-binaries.html#building-and-installing)
add_global_arguments('-static-libstdc++', language: ['cpp', 'c'])
# add_global_arguments('--cudart=static', language: ['cuda'])
add_global_link_arguments('-fuse-ld=mold', language: ['cpp', 'c'])

if meson.current_build_dir().contains('debugsan')
    message('debugsan build type in use')
elif meson.current_build_dir().contains('debug')
    message('debug build type in use')
    add_project_link_arguments(['-DDEBUG', '-ggdb'], language: 'cpp')
elif meson.current_build_dir().contains('release')
    message('release build type in use')
elif meson.current_build_dir().contains('coverage')
    message('coverage build type in use')
endif

###############################################################################################
# dependencies (system, in this case, a container)

# threads
thread_dep = dependency('threads')
dep_list += thread_dep

# dl
# https://github.com/ReneNyffenegger/gcc-create-library/blob/master/src/meson.build
cpp = meson.get_compiler('cpp')
libdl_dep = cpp.find_library('dl')
dep_list += libdl_dep

###############################################################################################
# wrap dependencies
# requires a 'meson wrap install <name of library>' before the below scripting will work

# put wrap library deps here


###############################################################################################
# now, binary build targets and libraries

subdir('libraries')

subdir('applications')
