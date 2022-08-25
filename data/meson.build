app_id = conf.get('appid')

app_resources = gnome.compile_resources(app_id,
    app_id + '.gresource.xml',
    gresource_bundle: true,
    dependencies: [
      configure_file(
        input: 'about.ui.in',
        output: 'about.ui',
        configuration: conf,
      ),
    ],
    install: true,
    install_dir: pkgdatadir
)

desktop_file = files('vn.hoabinh.quan.CoBang.desktop')

desktop_utils = find_program('desktop-file-validate', required: false)
if desktop_utils.found()
  test('Validate desktop file', desktop_utils,
    args: [desktop_file]
  )
  install_data(desktop_file,
    install_dir: get_option('datadir') / 'applications'
  )
endif

themedir = get_option('datadir') / 'icons/hicolor'
install_data('vn.hoabinh.quan.CoBang.svg',
  install_dir: themedir / 'scalable/apps'
)

appstream_file = files('vn.hoabinh.quan.CoBang.appdata.xml')

appstream_util = find_program('appstream-util', required: false)
if appstream_util.found()
  test('Validate appstream file', appstream_util,
    args: ['validate-relax', appstream_file]
  )
  install_data(appstream_file,
    install_dir: get_option('datadir') / 'metainfo'
  )
endif

install_data('vn.hoabinh.quan.CoBang.gschema.xml',
  install_dir: get_option('datadir') / 'glib-2.0/schemas'
)

compile_schemas = find_program('glib-compile-schemas', required: false)
if compile_schemas.found()
  test('Validate schema file', compile_schemas,
    args: ['--strict', '--dry-run', meson.current_source_dir()]
  )
endif
