boost = dependency('boost', modules : ['iostreams'])
deps = [boost]

cpp_args = ['-Wno-non-virtual-dtor', '-Wno-inconsistent-missing-override']
snappy = dependency('snappy', required: false)
if snappy.found()
  deps += [snappy]
  cpp_args += ['-DSNAPPY_CODEC_AVAILABLE']
endif

sources = files(
  'impl/Compiler.cc',
  'impl/Node.cc',
  'impl/LogicalType.cc',
  'impl/NodeImpl.cc',
  'impl/ResolverSchema.cc',
  'impl/Schema.cc',
  'impl/Types.cc',
  'impl/ValidSchema.cc',
  'impl/Zigzag.cc',
  'impl/BinaryEncoder.cc',
  'impl/BinaryDecoder.cc',
  'impl/Stream.cc',
  'impl/FileStream.cc',
  'impl/Generic.cc',
  'impl/GenericDatum.cc',
  'impl/DataFile.cc',
  'impl/parsing/Symbol.cc',
  'impl/parsing/ValidatingCodec.cc',
  'impl/parsing/JsonCodec.cc',
  'impl/parsing/ResolvingDecoder.cc',
  'impl/json/JsonIO.cc',
  'impl/json/JsonDom.cc',
  'impl/Resolver.cc',
  'impl/Validator.cc',
  'impl/CustomAttributes.cc')

headers = files(
  'api/AvroParse.hh',
  'api/AvroSerialize.hh',
  'api/AvroTraits.hh',
  'api/Compiler.hh',
  'api/Config.hh',
  'api/DataFile.hh',
  'api/Decoder.hh',
  'api/Encoder.hh',
  'api/Exception.hh',
  'api/Generic.hh',
  'api/GenericDatum.hh',
  'api/Layout.hh',
  'api/LogicalType.hh',
  'api/Node.hh',
  'api/NodeConcepts.hh',
  'api/NodeImpl.hh',
  'api/Parser.hh',
  'api/Reader.hh',
  'api/Resolver.hh',
  'api/ResolverSchema.hh',
  'api/ResolvingReader.hh',
  'api/Schema.hh',
  'api/SchemaResolution.hh',
  'api/Serializer.hh',
  'api/Specific.hh',
  'api/Stream.hh',
  'api/Types.hh',
  'api/ValidSchema.hh',
  'api/Validator.hh',
  'api/Writer.hh',
  'api/Zigzag.hh',
  'api/CustomAttributes.hh')

buffer_headers = files(
  'api/buffer/Buffer.hh',
  'api/buffer/BufferPrint.hh',
  'api/buffer/BufferReader.hh',
  'api/buffer/BufferStream.hh',
  'api/buffer/BufferStreambuf.hh')

buffer_detail_headers = files(
  'api/buffer/detail/BufferDetail.hh',
  'api/buffer/detail/BufferDetailIterator.hh')

# https://github.com/mesonbuild/meson/issues/2546
# another workaround may be to simply move the headers
# into a 'avro' subdir as part of the meson changes.
subdir('include-workaround-meson/avro')

avro = library('avrocpp',
  sources,
  include_directories: include_directories('api'),
  cpp_args: cpp_args + ['-Wno-unused-but-set-variable'],
  dependencies: deps)

avro_dep = declare_dependency(
  dependencies: deps,
  include_directories: include_directories('include-workaround-meson'),
  link_with: avro)
