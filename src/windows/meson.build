# project('injector', 'c',
#   default_options : ['warning_level=3', 'c_std=c11'])

cc = meson.get_compiler('c')
host_machine_cpu = host_machine.cpu_family()

inc = include_directories('../../include')

# Common arguments for all targets
common_args = ['/nologo', '/O2']

# Check if ARM64EC is enabled
if get_option('arm64ec')
  common_args += ['/arm64EC']
  link_args = ['/machine:arm64ec']
else
  link_args = []
endif

# Define source files
injector_sources = ['injector.c']

# Shared library targets
shared_library('injector',
  injector_sources,
  include_directories : inc,
  c_args : common_args + ['/MD'],
  link_args : link_args + ['/DEF:injector.def'],
  name_prefix : '',
  install : true)

shared_library('injectord',
  injector_sources,
  include_directories : inc,
  c_args : common_args + ['/MDd'],
  link_args : link_args + ['/DEF:injector.def'],
  name_prefix : '',
  install : true)

# Static library targets
static_library('injector-static',
  injector_sources,
  include_directories : inc,
  c_args : common_args + ['/MD'],
  link_args : link_args,
  install : true)

static_library('injectord-static',
  injector_sources,
  include_directories : inc,
  c_args : common_args + ['/MDd'],
  link_args : link_args,
  install : true)