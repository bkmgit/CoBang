configure_file(
  input: 'cobang.in',
  output: 'cobang',
  configuration: conf,
  install: true,
  install_dir: get_option('bindir')
)

myprogram = join_paths(meson.project_build_root(), 'bin', meson.project_name())
run_target('run',
  command: [myprogram, '-v']
)
