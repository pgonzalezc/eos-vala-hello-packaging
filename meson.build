# Nombre del proyecto y lenguaje de programación
project('com.github.pgonzalezc.eos-vala-hello-packaging','vala','c')

i18n = import('i18n')
add_global_arguments('-DGETTEXT_PACKAGE="@0@"'.format(meson.project_name()),language:'c')

# Creación del ejecutable, enumera los programas a compilar,
# llas dependencias e instala
executable(
    meson.project_name(),
    'src/Application.vala',
    dependencies: [
        dependency('gtk+-3.0')
    ],
    install: true
)

#Translate and install our .desktop file
i18n.merge_file(
    input: join_paths('data', 'hello-packaging.desktop.in'),
    output: meson.project_name() + '.desktop',
    po_dir: join_paths(meson.source_root(), 'po'),
    type: 'desktop',
    install: true,
    install_dir: join_paths(get_option('datadir'), 'applications')
)

#Translate and install our .appdata file
i18n.merge_file(
    input: join_paths('data', 'hello-packaging.appdata.xml.in'),
    output: meson.project_name() + '.appdata.xml',
    po_dir: join_paths(meson.source_root(), 'po'),
    install: true,
    install_dir: join_paths(get_option('datadir'), 'metainfo')
)
# Instala el icono en todos los tamaños requeridos
icon_sizes = ['16','32','48','64','128']

foreach i : icon_sizes
    install_data(
        join_paths('data',i + '.svg'),
        install_dir: join_paths(get_option('datadir'),'icons','hicolor', i + 'x' + i, 'apps'),
        rename: meson.project_name() + '.svg'
    )
    install_data(
        join_paths('data',i + '.svg'),
        install_dir: join_paths(get_option('datadir'), 'icons', 'hicolor', i + 'x' + i + '@2', 'apps')
    )
endforeach

subdir('po')
