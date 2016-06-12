# Mustache

C++11 header-only [Mustache](http://mustache.github.io) templates with no external dependencies.

[![travis](https://travis-ci.org/kainjow/Mustache.svg?branch=master)](https://travis-ci.org/kainjow/Mustache) [![appveyor](https://ci.appveyor.com/api/projects/status/6uh5d5weajrffkyw?svg=true)](https://ci.appveyor.com/project/kainjow/mustache) [![codecov](https://codecov.io/gh/kainjow/Mustache/branch/master/graph/badge.svg)](https://codecov.io/gh/kainjow/Mustache)

## Example 1

````cpp
Kainjow::Mustache tmpl{"Hello {{what}}!"};
std::cout << tmpl.render({"what", "World"}) << std::endl;
// Hello World!
````

## Example 2

````cpp
using Data = Kainjow::Mustache::Data;
Kainjow::Mustache tmpl{"{{#employees}}{{name}}, {{/employees}}"};
Data employees{Data::List()};
employees << Data{"name", "Steve"} << Data{"name", "Bill"};
tmpl.render({"employees", employees}, std::cout);
// Steve, Bill, 
````

## Example 3

````cpp
Kainjow::Mustache tmpl("Hello {{what}}!");
std::stringstream ss;
tmpl.render({"what", "World"}, [&ss](const std::string& str) {
    ss << str;
});
// ss.str() == "Hello World!"
````

## Supported Features

This library supports all current Mustache features.

- Variables
- HTML escaping
- Sections
- Inverted Sections
- True/False
- Lists
- Lambdas
- Partials
- Comments
- Set Delimiter

## Compilers Tested

- Xcode 4.6 - 7.0
- GCC 4.8 - 5.2
- Clang 3.3, 3.4
- Visual Studio 2013, 2015

## Run Tests

For *nix:

    make

For OS X:

    make mac

For Visual Studio 2013 (CMake 2.8+ required):

    build.bat

For Visual Studio 2015 (CMake 3.1+ required):

    build.bat 14

## License

    Copyright 2015-2016 Kevin Wojniak
    
    Permission is hereby granted, free of charge, to any person or organization
    obtaining a copy of the software and accompanying documentation covered by
    this license (the "Software") to use, reproduce, display, distribute,
    execute, and transmit the Software, and to prepare derivative works of the
    Software, and to permit third-parties to whom the Software is furnished to
    do so, all subject to the following:
    
    The copyright notices in the Software and this entire statement, including
    the above license grant, this restriction and the following disclaimer,
    must be included in all copies of the Software, in whole or in part, and
    all derivative works of the Software, unless such copies or derivative
    works are solely in the form of machine-executable object code generated by
    a source language processor.
    
    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE, TITLE AND NON-INFRINGEMENT. IN NO EVENT
    SHALL THE COPYRIGHT HOLDERS OR ANYONE DISTRIBUTING THE SOFTWARE BE LIABLE
    FOR ANY DAMAGES OR OTHER LIABILITY, WHETHER IN CONTRACT, TORT OR OTHERWISE,
    ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
    DEALINGS IN THE SOFTWARE.
