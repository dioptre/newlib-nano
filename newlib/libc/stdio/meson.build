srcs_stdio = [
    'asiprintf.c',
    'asniprintf.c',
    'asnprintf.c',
    'asprintf.c',
    'clearerr.c',
    'clearerr_u.c',
    'diprintf.c',
    'dprintf.c',
    'fcloseall.c',
    'fclose.c',
    'fdopen.c',
    'feof.c',
    'feof_u.c',
    'ferror.c',
    'ferror_u.c',
    'fflush.c',
    'fflush_u.c',
    'fgetc.c',
    'fgetc_u.c',
    'fgetpos.c',
    'fgets.c',
    'fgets_u.c',
    'fgetwc.c',
    'fgetwc_u.c',
    'fgetws.c',
    'fgetws_u.c',
    'fileno.c',
    'fileno_u.c',
    'findfp.c',
    'fiprintf.c',
    'fiscanf.c',
    'flags.c',
    'fmemopen.c',
    'fopen.c',
    'fopencookie.c',
    'fprintf.c',
    'fpurge.c',
    'fputc.c',
    'fputc_u.c',
    'fputs.c',
    'fputs_u.c',
    'fputwc.c',
    'fputwc_u.c',
    'fputws.c',
    'fputws_u.c',
    'fread.c',
    'fread_u.c',
    'freopen.c',
    'fscanf.c',
    'fseek.c',
    'fseeko.c',
    'fsetlocking.c',
    'fsetpos.c',
    'ftell.c',
    'ftello.c',
    'funopen.c',
    'fvwrite.c',
    'fwalk.c',
    'fwide.c',
    'fwprintf.c',
    'fwrite.c',
    'fwrite_u.c',
    'fwscanf.c',
    'getc.c',
    'getchar.c',
    'getchar_u.c',
    'getc_u.c',
    'getdelim.c',
    'getline.c',
    'gets.c',
    'getw.c',
    'getwc.c',
    'getwchar.c',
    'getwchar_u.c',
    'getwc_u.c',
    'iprintf.c',
    'iscanf.c',
    'makebuf.c',
    'mktemp.c',
    'nano-vfprintf.c',
    'nano-vfprintf_float.c',
    'nano-vfprintf_i.c',
    'nano-vfscanf.c',
    'nano-vfscanf_float.c',
    'nano-vfscanf_i.c',
    'open_memstream.c',
    'perror.c',
    'printf.c',
    'putc.c',
    'putchar.c',
    'putchar_u.c',
    'putc_u.c',
    'puts.c',
    'putw.c',
    'putwc.c',
    'putwchar.c',
    'putwchar_u.c',
    'putwc_u.c',
    'refill.c',
    'remove.c',
    'rename.c',
    'rewind.c',
    'rget.c',
    'scanf.c',
    'sccl.c',
    'setbuf.c',
    'setbuffer.c',
    'setlinebuf.c',
    'setvbuf.c',
    'siprintf.c',
    'siscanf.c',
    'sniprintf.c',
    'snprintf.c',
    'sprintf.c',
    'sscanf.c',
    'stdio.c',
    'stdio_ext.c',
    'swprintf.c',
    'swscanf.c',
    'tmpfile.c',
    'tmpnam.c',
    'ungetc.c',
    'ungetwc.c',
    'vasiprintf.c',
    'vasniprintf.c',
    'vasnprintf.c',
    'vasprintf.c',
    'vdiprintf.c',
    'vdprintf.c',
    'vfprintf.c',
    'vfscanf.c',
    'vfwprintf.c',
    'vfwscanf.c',
    'viprintf.c',
    'viscanf.c',
    'vprintf.c',
    'vscanf.c',
    'vsiprintf.c',
    'vsiscanf.c',
    'vsniprintf.c',
    'vsnprintf.c',
    'vsprintf.c',
    'vsscanf.c',
    'vswprintf.c',
    'vswscanf.c',
    'vwprintf.c',
    'vwscanf.c',
    'wbuf.c',
    'wprintf.c',
    'wscanf.c',
    'wsetup.c',
]
hdrs_stdio = [
    'floatio.h',
    'fvwrite.h',
    'local.h',
    'nano-vfprintf_local.h',
    'nano-vfscanf_local.h',
    'stdio_ext.h',
    'stdio.h',
    'vfieeefp.h',
]
foreach target : targets
	value = get_variable('target_' + target)
	set_variable('lib_stdio' + target,
		static_library('stdio' + target,
			srcs_stdio,
			pic: false,
			include_directories: inc,
			c_args: value[1]))
endforeach
