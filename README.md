`randchoice` is a tiny script that helps indecisive people choose from a list
of options passed in through `stdin` and/or as arguments to the script.

## Usage

There are two modes of using `randchoice`: either providing a list of options
as arguments to the script or by piping in a list through `stdin` (e.g. `$ less
./example_data/restaurants.txt | ./randchoice`). By default, the output will be
"prettily" printed to terminal outputs and plainly printed otherwise. In the
latter case, the trailing newline can be omitted with the `-n` flag. To print
plainly to a terminal, pass the `-p` or `--plain` flag. Specify how many items
to choose with the `-c` or `--choose` flag.

If I've neglected to update this documentation after adding/changing a feature,
check the help text with the `-h` or `--help` flag.

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

### Pick a movie

```sh
$ less example_data/movies.txt | sed '/^#/d' | sort | uniq | randchoice "Heat"

The choice is  The Matrix 

```

There is much I have to learn about useful *nix programs, so I'm including the
`sed`, `sort`, and `uniq` stuff as a reminder to myself for how to filter out
comments and repeated entries. Being able to use `sed` to suppress comments
means I don't need to include that functionality in `randchoice`.

### Narrow down restaurants to 3 finalists, pick one of those

```sh
$ less example_data/restaurants.txt | randchoice -c 3 | tee /dev/tty | randchoice
In-N-Out
Sage
Castle BBQ

The choice is  In-N-Out 

```

Again, this contrived example is mostly a reminder to myself that I can display
output in the middle of a series of pipes with `tee /dev/tty` (assuming I'm
using a terminal), but I can conceive of a possible situation to use this

> Picky Person: "I don't know where I want to eat tonight. Can you choose
> something?"
>
> Nerdy Person: "How about I narrow it down to two or three choices, and you
> can pick what you're most in the mood for?"
>
> Picky Person: "No, just choose something."
>
> Nerdy Person: "Ok, between Foo, Bar, and Baz, the computer says Bar."
>
> Picky Person: "I just had Bar. Let's just go to Foo."
>
> Nerdy Person: "That works."
