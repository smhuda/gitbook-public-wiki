# Command Line Arguments

### Example 1: Generate Help Argument and Message

Consider the code sample below:

```text
import argparse

parser = argparse.ArgumentParser(description='A test program.')
args = parser.parse_args()
```

```text
$ ./test.py -h
$ ./test.py --help

A test program.

optional arguments:
  -h, --help  show this help message and exit
```

### Example 2: Handle a String Argument

```text
import argparse

parser = argparse.ArgumentParser(description='A test program.')

parser.add_argument("print_string", help="Prints the supplied argument.")

args = parser.parse_args()

print(args.print_string)
```

```text
usage: test.py [-h] [print_string]

A test program.


positional arguments:

  print_string  Prints the supplied argument.


optional arguments:

  -h, --help    show this help message and exit
```

To define and parse optional arguments, you can use “–” \(double dash\) and change their default values using the “default” argument.

```text
import argparse

parser = argparse.ArgumentParser(description='A test program.')

parser.add_argument("--print_string", help="Prints the supplied argument.", default=”A random string.”)

args = parser.parse_args()

print(args.print_string)
```

```text
$ ./test.py --print_string My-Test-String
My-Tesr
```

You can also define shorthand versions of the argument using “-” \(single dash\) to reduce verbosity.

```text
import argparse

parser = argparse.ArgumentParser(description='A test program.')

parser.add_argument(“-p”, "--print_string", help="Prints the supplied argument.", default=”A random string.”)

args = parser.parse_args()

print(args.print_string)
```

```text
$ ./test.py -p Test-String
```

### Example 3: Handle an Integer Argument

```text
import argparse

parser = argparse.ArgumentParser(description='A test program.')

parser.add_argument("-p", "--print_string", help="Prints the supplied argument.", type=int)

args = parser.parse_args()

print(args.print_string)
```

```text
usage: test.py [-h] [-p PRINT_STRING]

test.py: error: argument -p/--print_string: invalid int value: 'LinuxHint.com'
```

### Example 4: Handle True and False Toggles

```text
import argparse

parser = argparse.ArgumentParser(description='A test program.')

parser.add_argument("-p", "--print_string", help="Prints the supplied argument.", action="store_true")

args = parser.parse_args()

print(args.print_string)
```

### Example 5: Treat Argument Values as List

If you want to get multiple values at once and store them in list, you need to supply “nargs” keyword in following format:

```text
import argparse

parser = argparse.ArgumentParser(description='A test program.')

parser.add_argument("-p", "--print_string", help="Prints the supplied argument.", nargs='*')

args = parser.parse_args()

print(args.print_string)
```

```text
$ ./test.py -p “a” “b”
```

```text
['a', 'b']
```

### Example 6: File as command line argument for argparse - error message if argument is not valid

You just need to write a function which checks if the file is valid and writes an error otherwise. Use that function with the `type` option. Note that you could get more fancy and create a custom action by subclassing `argparse.Action`, but I don't think that is necessary here. In my example, I return an open file handle \(see below\):

```text
#!/usr/bin/env python

from argparse import ArgumentParser
import os.path


def is_valid_file(parser, arg):
    if not os.path.exists(arg):
        parser.error("The file %s does not exist!" % arg)
    else:
        return open(arg, 'r')  # return an open file handle


parser = ArgumentParser(description="ikjMatrix multiplication")
parser.add_argument("-i", dest="filename", required=True,
                    help="input file with two matrices", metavar="FILE",
                    type=lambda x: is_valid_file(parser, x))
args = parser.parse_args()

A, B = read(args.filename)
C = ikjMatrixProduct(A, B)
printMatrix(C)
```

### Example 7: File Extension Checking - argsparse

```text
import argparse
import os.path

parser = argparse.ArgumentParser()

def file_choices(choices,fname):
    ext = os.path.splitext(fname)[1][1:]
    if ext not in choices:
       parser.error("file doesn't end with one of {}".format(choices))
    return fname

parser.add_argument('fn',type=lambda s:file_choices(("csv","tab"),s))

parser.parse_args()
```

### Example 8: Require either of two arguments using argparse

```text
import argparse

parser = argparse.ArgumentParser()
group = parser.add_mutually_exclusive_group(required=True)
group.add_argument('--foo',action=.....)
group.add_argument('--bar',action=.....)
args = parser.parse_args() 
```

If you need some check that is not provided by the module you can always do it manually:

```text
pa = argparse.ArgumentParser()
...
args = pa.parse_args()

if args.foo is None and args.bar is None:
   pa.error("at least one of --foo and --bar required")
```

### Example 8: If arg is A, do this, if B do that, if none of the above show help and quit

```text
import argparse

parser = argparse.ArgumentParser()
parser.add_argument("a")
args = parser.parse_args()

if args.a == 'magic.name':
    print 'You nailed it!'
```

**adding to it:**

```text
...
parser.add_argument("a", nargs='?', default="check_string_for_empty")
...
if args.a == 'check_string_for_empty':
    print 'I can tell that no argument was given and I can deal with that here.'
elif args.a == 'magic.name':
    print 'You nailed it!'
else:
    print args.a
```

**Or try the following:**

Here's the way I do it with `argparse` \(with multiple args\):

```text
parser = argparse.ArgumentParser(description='Description of your program')
parser.add_argument('-f','--foo', help='Description for foo argument', required=True)
parser.add_argument('-b','--bar', help='Description for bar argument', required=True)
args = vars(parser.parse_args())
```

`args` will be a dictionary containing the arguments:

```text
if args['foo'] == 'Hello':
    # code here

if args['bar'] == 'World':
    # code her
```



