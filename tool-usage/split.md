---
description: >-
  The split command or utility allows you to split by lines, size or the number
  of smaller files you need. Another related utility is csplit than can also be
  used.
---

# Split

### Split files based on \# of lines

Let’s say we want to split the file into several files based on a predetermined number of lines. This works best if the file contains lines separated by the end of line character, as it usually does. Let’s split our big file \(eg. _bigfile.txt_\) into files with 275 lines each.

```text
$ split -l 275 bigfile.txt
```

This will split the files into several files, named _xaa_, _xab_, _xac_ etc. each of which contain 275 lines each. If you don’t specify the number of lines \(_-l_\) then the default is 1000. The default for the output file prefix is _x_ in most cases. I usually like to specify a prefix that ends with “-“, but that is upto you.

```text
$ split -l 275 bigfile.txt smallfile-
```

If you prefer numerical suffixes instead of the character suffixes in the output, use the _-d_ option with the command.

```text
$ split -l 275 -d bigfile.txt smallfile-
```

Sometimes, you want a specific extension for your files such as _.txt_. You can do this using the command line option _–additional-suffix_

```text
$ split -l 275 -d bigfile.txt smallfile- --additional-suffix=.txt
```

### Split files based on size

Let’s say we want to divide the file into several files each of which is 5k in size. You can specify the size in bytes, kilobytes, mega bytes etc. as well.

```text
$ split -b 5k bigfile.txt smallfile-
```

### Split into specific number of files

If you want to split the file into 2 equally sized files, then you can do something like this:

```text
$ split -n 2 -d bigfile.txt smallfile-

```

Of course, to split it in to even more number of files you specify the number with the _-n_ option. One issue with splitting it like this is that it could cause the lines to be split between the files. In most cases, you want the lines to be preserved so that the entire line is within the same output file.

```text
$ split -n l/10 -d bigfile.txt smallfile-

```

The above example will split the file into 10 equally sized files while preserving the lines. That means that lines will not be split between files. The value or argument is a lowercase L, just to be clear.

Sometimes, you want just part of the file and not the entire file. For example, if you want to split the file into 4 equal parts but is only interested in the 3rd section or part, then you could do something like:

```text
$ split -n l/3/4 bigfile.txt > myfile.txt
```

### Split based on content

Another common use case is when you want to split based on the content of the file. This is a specialized use case, but can be very useful. The utility named **csplit** can be used to split files into sections determined by the context or content of the lines.

The generic syntax of the _**csplit**_ command is

```text
$ csplit [options] <source file> <regex expression>

```

So, as an example if you want to split a file when you encounter the text or line _Error_, then you could do…

```text
$ csplit -k bigfile.txt '/^Error/' {*}

```

The above command will split the file whenever it finds a line that starts with the word _Error_. The argument _‘/^Error/’_ is the regular expression we are matching against. The next argument **{\*}** specifies how many times the match should be repeated. The argument _‘{\*}’_ specifies that it will repeated till the end of file.

