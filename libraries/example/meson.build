example_source = files('example_example.cpp')

example_include = include_directories('.')

# format: lib + <shared|static> + namespace + <class|module|component>
lib_static_example_example = static_library(
    # <class|module|component> + <shared|static>
    'example_static',
    example_source,
    cpp_args: cpp_flags,
    dependencies: [dep_list],
)

lib_static_example_example_dep = declare_dependency(
    link_with: lib_static_example_example,
    include_directories: example_include,
)
