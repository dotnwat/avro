subdir('buffer')
subdir('buffer/detail')

foreach header : headers
  configure_file(
    copy: true,
    input: header,
    output: '@PLAINNAME@')
endforeach
