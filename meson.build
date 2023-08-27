project('xdg-desktop-portal-hyprland', 'cpp', 'c',
	version: '2.0.0',
	license: 'MIT',
	meson_version: '>=0.63.0',
	default_options: [
		'warning_level=2',
		'optimization=3',
		'buildtype=release',
		'debug=false',
    # 'cpp_std=c++23' # not yet supported by meson, as of version 0.63.0
	],)

# clang v14.0.6 uses C++2b instead of C++23, so we've gotta account for that
# replace the following with a project default option once meson gets support for C++23
cpp_compiler = meson.get_compiler('cpp')
if cpp_compiler.has_argument('-std=c++23')
  add_global_arguments('-std=c++23', language: 'cpp')
elif cpp_compiler.has_argument('-std=c++2b')
  add_global_arguments('-std=c++2b', language: 'cpp')
else
  error('Could not configure current C++ compiler (' + cpp_compiler.get_id() + ' ' + cpp_compiler.version() + ') with required C++ standard (C++23)')
endif

add_project_arguments(cpp_compiler.get_supported_arguments([
	'-Wall',
	'-Wextra',
	'-Wno-pointer-arith',
  '-Wno-unused-parameter',
  '-Wno-unused-value',
  '-Wno-missing-field-initializers',
  '-Wno-narrowing',
]), language: 'cpp')

wayland_protos = dependency('wayland-protocols', version: '>=1.24')
