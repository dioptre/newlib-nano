project('newlib-nano', 'c',
	default_options: [
		'buildtype=debugoptimized',
		'c_std=gnu99',
	],
	version: '2.10.0',
)

targets = []

enable_multilib = get_option('multilib')
enable_tests = get_option('tests')
newlib_tinystdio = get_option('newlib-tinystdio')

newlib_io_pos_args = get_option('newlib-io-pos-args')
newlib_io_c99_formats = get_option('newlib-io-c99-formats')
newlib_register_fini = get_option('newlib-register-fini')
newlib_io_long_long = get_option('newlib-io-long-long')
newlib_io_long_double = get_option('newlib-io-long-double')
newlib_mb = get_option('newlib-mb')
newlib_iconv_encodings = get_option('newlib-iconv-encodings')
newlib_iconv_from_encodings = get_option('newlib-iconv-from-encodings')
newlib_iconv_to_encodings = get_option('newlib-iconv-to-encodings')
newlib_iconv_external_ccs = get_option('newlib-iconv-external-ccs')
newlib_atexit_dynamic_alloc = get_option('newlib-atexit-dynamic-alloc')
newlib_global_atexit = get_option('newlib-global-atexit')
newlib_reent_small = get_option('newlib-reent-small')
newlib_global_stdio_streams = get_option('newlib-global-stdio-streams')
newlib_fvwrite_in_streamio = get_option('newlib-fvwrite-in-streamio')
newlib_fseek_optimization = get_option('newlib-fseek-optimization')
newlib_wide_orient = get_option('newlib-wide-orient')
newlib_nano_malloc = get_option('newlib-nano-malloc')
newlib_unbuf_stream_opt = get_option('newlib-unbuf-stream-opt')
lite_exit = get_option('lite-exit')
newlib_nano_formatted_io = get_option('newlib-nano-formatted-io')
newlib_retargetable_locking = get_option('newlib-retargetable-locking')
newlib_long_time_t = get_option('newlib-long-time_t')
newlib_multithread = get_option('newlib-multithread')
newlib_iconv = get_option('newlib-iconv')
newlib_io_float = get_option('newlib-io-float')
newlib_supplied_syscalls = get_option('newlib-supplied-syscalls')
hw_fp = get_option('hw-fp')

if enable_multilib
  foreach target : run_command(meson.get_compiler('c'), '--print-multi-lib').stdout().strip().split('\n')
    tmp = target.split(';')
    flags = []
    if tmp.length() > 1
      foreach flag : tmp[1].strip('@').split('@')
	if flag != ''
	  flags += '-' + flag
	endif
      endforeach
      if tmp[0] == '.'
	name = ''
      else
	name = tmp[0].underscorify()
      endif
    else
      name = ''
    endif
    targets += name
    value = [tmp[0], flags]
    set_variable('target_' + name, value)
  endforeach
else
  targets = ['']
  target_ = ['.', []]
endif

conf_data = configuration_data()

NEWLIB_MAJOR_VERSION=2
NEWLIB_MINOR_VERSION=10
NEWLIB_PATCHLEVEL_VERSION=0

conf_data.set('_WANT_IO_C99_FORMATS', newlib_io_c99_formats)
conf_data.set('_WANT_REGISTER_FINI', newlib_register_fini)
conf_data.set('_WANT_IO_LONG_LONG', newlib_io_long_long)
conf_data.set('_WANT_IO_LONG_DOUBLE', newlib_io_long_double)
conf_data.set('_WANT_IO_POS_ARGS', newlib_io_pos_args)
conf_data.set('_WANT_REENT_SMALL', newlib_reent_small)
conf_data.set('_WANT_REENT_GLOBAL_STDIO_STREAMS', newlib_global_stdio_streams)
conf_data.set('_MB_CAPABLE', newlib_mb)
conf_data.set('_MB_LEN_MAX', newlib_mb ? '8' : '1')
conf_data.set('__SINGLE_THREAD__', newlib_multithread == false)
conf_data.set('_ICONV_ENABLE_EXTERNAL_CCS', newlib_iconv_external_ccs)
conf_data.set('_ICONV_ENABLED', newlib_iconv)
conf_data.set('_ICONV_ENABLE_EXTERNAL_CCS', newlib_iconv_external_ccs)
conf_data.set('_ATEXIT_DYNAMIC_ALLOC', newlib_atexit_dynamic_alloc)
conf_data.set('_REENT_GLOBAL_ATEXIT', newlib_global_atexit)
conf_data.set('_FVWRITE_IN_STREAMIO', newlib_fvwrite_in_streamio)
conf_data.set('_FSEEK_OPTIMIZATION', newlib_fseek_optimization)
conf_data.set('_WIDE_ORIENT', newlib_wide_orient)
conf_data.set('_NANO_MALLOC', newlib_nano_malloc)
conf_data.set('_UNBUF_STREAM_OPT', newlib_unbuf_stream_opt)
conf_data.set('_LITE_EXIT', lite_exit)
conf_data.set('_NANO_FORMATTED_IO', newlib_nano_formatted_io)
conf_data.set('_RETARGETABLE_LOCKING', newlib_retargetable_locking)
conf_data.set('_WANT_USE_LONG_TIME_T', newlib_long_time_t)
conf_data.set('TINY_STDIO', newlib_tinystdio, description: 'Use tiny stdio from gcc avr')
conf_data.set('__CUSTOM_FILE_IO__', newlib_tinystdio, description: 'Use tiny stdio FILE')
conf_data.set('_IEEE_LIBM', true, description: 'math library only offers ieee semantics')

version_data = configuration_data()

version_array = meson.project_version().split('.')

version_data.set('_NEWLIB_VERSION', '"@0@"'.format(meson.project_version()), description: 'The newlib version in string format.')
version_data.set('_NEWLIB__', version_array[0], description: 'The newlib major version number.')
version_data.set('_NEWLIB_MINOR__', version_array[1], description: 'The newlib minor version number.')
version_data.set('__NEWLIB_PATCHLEVEL__', version_array[2], description: 'The newlib patch level.')

if newlib_tinystdio
  inc = include_directories(
    '.',
    'newlib/libc/tinystdio',
    'newlib/libc/include'
  )
else
  inc = include_directories(
    '.',
    'newlib/libc/include'
  )
endif

includedir = join_paths(get_option('prefix'), get_option('includedir'))

configure_file(output : 'newlib.h',
	       configuration: conf_data,
	       install_dir: includedir)

configure_file(output : '_newlib_version.h',
	       configuration: version_data,
	       install_dir: includedir)

arguments = ['-g', '-ffunction-sections', '-fdata-sections']
if get_option('target-optspace')
  arguments += '-Os'
endif

add_project_arguments(arguments, language: 'c')

subdir('newlib')

if enable_tests
  subdir('test')
endif
