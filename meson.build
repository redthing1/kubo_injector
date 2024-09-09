project('injector', 'c',
  default_options : ['warning_level=3', 'c_std=c11'])

# Determine the operating system
host_system = host_machine.system()

# Set the appropriate source directory based on the OS
if host_system == 'windows'
  subdir('src/windows')
elif host_system == 'darwin'
  subdir('src/macos')
elif host_system == 'linux'
  subdir('src/linux')
else
  error('Unsupported operating system')
endif

# Build the command-line tool
subdir('cmd')

# # Set up tests
# subdir('tests')

# The 'all' target is implicit in Meson
# The 'clean' target is handled automatically by Meson/Ninja