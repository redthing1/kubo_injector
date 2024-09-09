# project('injector', 'c',
  # default_options : ['warning_level=3', 'c_std=c11'])

inc = include_directories('../../include')

injector_sources = [
  'elf.c',
  'injector.c',
  'ptrace.c',
  'remote_call.c',
  'util.c',
  'shellcode.S'
]

libinjector_shared = shared_library('injector',
  injector_sources,
  include_directories : inc,
  # pic : true,
  c_args : ['-fPIC'],
)

libinjector_static = static_library('injector',
  injector_sources,
  include_directories : inc,
  pic : true,
  # c_args : injector_cflags,
  install : true)

# Declare dependencies for other parts of the project to use
injector_dep = declare_dependency(
  link_with : libinjector_shared,
  include_directories : inc)

# If you need to use the static library elsewhere in the project
injector_static_dep = declare_dependency(
  link_with : libinjector_static,
  include_directories : inc)