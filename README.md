cata_libintl is a simple cross-platform internationalization library compatible with gettext MO files.

It's main use is to enable runtime loading, merging and use of multiple MO files without separating them into "translation domains".

### Features
* Loads MO files from specified paths
* Validates MO files before use
* Cross-platform and lightweight
* Locale independent
* Full support for plural forms, aims to be compatible with [Poedit](https://poedit.net/)

### Differences from libintl
* No translation domains
* No encoding conversion, UTF-8 only
* Does not use locale or environment variables, instead requires explicit file paths
* Supports merging multiple MO files at runtime


### Example usage

```cpp
#include "cata_libintl.h"

using namespace cata_libintl;

void main() {
  // Load and validate MO files
  std::vector<trans_catalogue> list;
  list.push_back( trans_catalogue::load_from_file( "./foo.mo" ) );
  list.push_back( trans_catalogue::load_from_file( "./bar.mo" ) );
  list.push_back( trans_catalogue::load_from_file( "./baz.mo" ) );

  // Merge strings
  trans_library lib = trans_library::create( std::move( list ) );

  // Query translation by message id
  const char* hello_world = lib.get( "Hello, world!" );

  // Query translation by message id and context
  const char* spring = lib.get_ctx( "Where river starts", "Spring" );

  // Query translation by message id and plural form
  int n_worlds = 1337;
  const char* many_worlds = lib.get( "World", "Worlds", n_worlds );

  // Query translation by message id, context and plural form
  int n_springs = 1234;
  const char* many_springs = lib.get_ctx_pl( "Coiled metal wire", "Spring", "Springs", n_springs );
}
```

### Dependencies
This library uses [fmtlib](https://github.com/fmtlib/fmt) to format error messages, and [Catch2](https://github.com/catchorg/Catch2) for testing.

### Building with CMake
Source build is available with CMake (minimum required version 3.11):
```sh
mkdir build
cd build
cmake ..
cmake --build .
```
Tests will be built by default, this behavior can be disabled by `CATA_LIBINTL_TESTS` option.
