`randchoice` is a tiny script that helps indecisive people choose from a list
of options passed in either through `stdin` or as arguments to the script.

## Usage

There are two modes of using `randchoice`: either providing a list of options
as arguments to the script or by piping in a list through `stdin` (e.g. `$ less
./tests/restaurants.txt | ./randchoice`). By default, the output will be
"prettily" printed to terminal outputs and plainly printed otherwise. In the
latter case, the trailing newline can be omitted with the `-n` flag. To print
plainly to a terminal, pass the `-P` (note: that's a capital P) or `--plain`
flags.

## Examples

These examples assume that `randchoice` exists somewhere on your `$PATH`.

### Choosing an option from arguments

```sh
$ randchoice "foo bar" baz quux

The choice is  quux 

```

Note that compound elements (e.g. "foo bar") must be wrapped in quotes.

### Choose a random element of a directory

```sh
$ ls -1 /path/to/dir | randchoice | cat
node
```

This demonstrates how `randchoice` plays nicely with piping.
