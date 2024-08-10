[![Actions Status](https://github.com/hoelzro/p6-pod-eod/actions/workflows/linux.yml/badge.svg)](https://github.com/hoelzro/p6-pod-eod/actions) [![Actions Status](https://github.com/hoelzro/p6-pod-eod/actions/workflows/macos.yml/badge.svg)](https://github.com/hoelzro/p6-pod-eod/actions) [![Actions Status](https://github.com/hoelzro/p6-pod-eod/actions/workflows/windows.yml/badge.svg)](https://github.com/hoelzro/p6-pod-eod/actions)

NAME
====

Pod::EOD - Moves declarative POD blocks to the end of the POD

SYNOPSIS
========

```raku
#| Example sub!
my sub example {}

DOC INIT {
    use Pod::EOD;
    move-declarations-to-end($=pod);
}

=head1 OTHER POD
...

# Now the "Example sub" POD appears after
# the "OTHER POD" POD!
```

DESCRIPTION
===========

Many authors from a Perl background (like myself) write POD in a "all POD at the end" style; this keeps it out of the way when you're looking at the code, but in the same file. However, POD blocks are inserted into `$=pod` in the order they occur in the code, and I would rather not give up the advantages of declarative POD blocks. So this module simply moves declative POD blocks to the end of the POD document, so that the developer can keep their POD at the end, and the user can read the high-level overview of the module before encountering the reference section provided by declarative blocks.

AUTHORS
=======

  * Rob Hoelz

  * Raku Community

COPYRIGHT AND LICENSE
=====================

Copyright (c) 2016 - 2017 Rob Hoelz

Copyright (c) 2024 Raku Community

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

REFERENCE
=========

### sub move-declarations-to-end

```raku
sub move-declarations-to-end(
    $pod
) returns Mu
```

Rearranges the POD blocks in C<$pod> (you will almost always pass your module's C<$=pod> to this sub) so that declarative POD blocks (like this one) are moved to the end of the document. Note that this happens I<in place>, so your original array is modified!

