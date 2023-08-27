globber = run_command('find', '.', '-name', '*.cpp', check: true)
src = globber.stdout().strip().split('\n')

executable('xdg-desktop-portal-hyprland', src,
  dependencies: [
    dependency('wayland-client'),
    dependency('wayland-protocols'),
    dependency('cairo'),
    dependency('libjpeg')
    dependency('pango'),
    dependency('pangocairo')
    dependency('sdbus'),
    dependency('threads'),
		hyprland_protos,
  ],
  install: true,
  install_dir: get_option('libexecdir')
)
