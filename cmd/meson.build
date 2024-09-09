# project('injector_cmd', 'c',
  # default_options : ['warning_level=3', 'c_std=c11'])

# Get the root project's source directory
root_src_dir = meson.source_root()

# Include directories
inc = include_directories('../include')

# Common source files
sources = ['main.c']

# Platform-specific configurations
host_system = host_machine.system()

if host_system == 'windows'
  src_dir = '../src/windows'
  sources += '../util/ya_getopt.c'
  extra_libs = ['dbghelp']
elif host_system == 'darwin'
  src_dir = '../src/macos'
  sources += '../util/ya_getopt.c'
  extra_libs = []
elif host_system == 'linux'
  src_dir = '../src/linux'
  extra_libs = []
else
  error('Unsupported operating system')
endif

# Dependency on the injector library
# injector_lib = dependency('injector', fallback : ['injector', 'injector_static_dep'])

# Build the injector command-line tool
executable('injector',
  sources,
  include_directories : inc,
  dependencies : [injector_dep],
  link_args : extra_libs,
  install : true)