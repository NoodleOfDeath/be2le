# be2le
Simple bash command line script for converting big endian byte strings to little endian byte strings

## Usage
```
$ git clone https://github.com/NoodleOfDeath/be2le
Cloning into 'be2le'...
remote: Enumerating objects: 3, done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 3
Receiving objects: 100% (3/3), done.
$ cd be2le
$ chmod +x be2le
$ ./be2le -h
be2le v.1.0 (c) 2019 NoodleOfDeath

usage: be2le [options] <hex-string> ...[hex-string]

options:
  -h|--help                             displays this help message
  -f format|--format=format             specifies the output format; values can be "preserve", "int", "char", or "raw". Default is "preserve"
  -d delimiter|--delimiter=delimiter    specifies the delimiter used to separate converted strings; default is a newline character
  -n|--no-newline                       omits the trailing newline when printing to stdout
  -j|--join                             prints all converted strings as a single joined string
  -s|--strip-null                       strips leading null bytes.

examples:

$ be2le d76f411475428afc90947ee320
20e37e9490fc8a427514416fd7

$ be2le 0x3 0x41 67328fa 0x100aaf
0x03
0x41
fa287306
0xaf0a10

$ be2le aaff ade0 0x0dd '\x8700' -s -d ", "
ffaa, e0ad, 0xdd00, \x87

$ be2le 0xffee af0a d9c3 -j
0xeeff0aafc3d9 

$ be2le 0x33ffadfe -f char
\xfe\xad\xff\x33

$ be2le 0x00aa 0xaa aaaa00 -f int
0xaa 0x00 
0xaa 
0x00 0xaa 0xaa
