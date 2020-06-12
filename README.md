`randchoice` is a tiny script that helps indecisive people choose from a list
of options passed in either through `stdin` or as arguments to the script.

## Examples

### Choosing an option from arguments

```sh
randchoice "foo bar" baz quux

The choice is  quux 

```

Note that compound elements (e.g. "foo bar") must be wrapped in quotes.

### Choose a random element of a directory

```sh
$ ls -1 /path/to/dir | randchoice | cat
node
```

This demonstrates how `randchoice` plays nicely with piping.
