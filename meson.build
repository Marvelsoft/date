project('datelib',
        'cpp',
        version: run_command('cat', files('version.txt')).stdout().strip(),
        default_options: ['cpp_std=c++14'])

tz_dir_flag = '-DINSTALL=' + meson.build_root()
cpp_flags = ['-DTARGET_PLATFORM_LINUX', 
             '-DHAS_REMOTE_API=0', 
             '-DAUTO_DONWNLOAD=0', 
             tz_dir_flag, 
             '-Wno-constant-logical-operand'
            ]

libcurl = dependency('libcurl')
thread_dep = dependency('threads')
date_src = files('src/tz.cpp')
date_inc = include_directories('include')

date_hdr = declare_dependency(include_directories: date_inc)
date_lib = shared_library(
  'date', 
  include_directories: date_inc, 
  sources: date_src, 
  dependencies: [libcurl, thread_dep],
  cpp_args: cpp_flags)

date_dep = declare_dependency(
  include_directories: date_inc,
  link_with: date_lib)

