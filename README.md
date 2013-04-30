# ffi-hunspell

* [Source](https://github.com/postmodern/ffi-hunspell)
* [Issues](https://github.com/postmodern/ffi-hunspell/issues)
* [Documentation](http://rubydoc.info/gems/ffi-hunspell)
* [Email](postmodern.mod3 at gmail.com)

[![Build Status](https://secure.travis-ci.org/postmodern/ffi-hunspell.png?branch=master)](https://travis-ci.org/postmodern/ffi-hunspell)

## Description

Ruby FFI bindings for [Hunspell][libhunspell].

## Examples

Open a dictionary:

    require 'ffi/hunspell'
    
    FFI::Hunspell.dict do |dict|
      # ...
    end

    FFI::Hunspell.dict('en_GB') do |dict|
      # ...
    end

    dict = FFI::Hunspell.dict('en_GB')
    # ...
    dict.close

Check if a word is valid:

    dict.check?('dog')
    # => true

    dict.check?('d0g')
    # => false

Find the stems of a word:

    dict.stem('dogs')
    # => ["dog"]

Suggest alternate spellings for a word:

    dict.suggest('arbitrage')
    # => ["arbitrage", "arbitrages", "arbitrager", "arbitraged", "arbitrate"]

## Requirements

* [libhunspell] >= 1.2.0
* [ffi] ~> 1.0

## Install

    $ gem install ffi-hunspell

## Known Issues

Some Linux distributions do not install the `libhunspell-1.2.so`
shared library file, but instead installs `libhunspell-1.2.so.0`.
Simply create a symbolic link to the hunspell shared library,
so that {FFI::Hunspell} can find the library:

    # ln -s /usr/lib/libhunspell-1.2.so.0 /usr/lib/libhunspell-1.2.so

## License

Copyright (c) 2010-2013 Hal Brodigan

See {file:LICENSE.txt} for license information.

[libhunspell]: http://hunspell.sourceforge.net/
[ffi]: https://github.com/ffi/ffi
