project('datelib','cpp')

cpp_flags = ['-Wno-constant-logical-operand']

libcurl = dependency('libcurl')

date_src = files('tz.cpp')
date_inc = include_directories('.')

date_hdr = declare_dependency(include_directories: date_inc)
date_lib = static_library(
  'date', 
  include_directories: date_inc, 
  sources: date_src, 
  dependencies: libcurl, 
  cpp_args: cpp_flags)

date_dep = declare_dependency(
  include_directories: date_inc,
  link_with: date_lib)

