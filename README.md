# FastCommunity Clustering Algorithm

Slightly modified version of [fastmodularity](http://www.cs.unm.edu/~aaron/research/fastmodularity.htm) that works on Linux.

## Usage
This program is rather complicated and requires a specific kind of input,
so some notes on how to use it are in order. Mainly, the program requires
a specific structure input file (.pairs) that has the following characteristics:

  1. pairs is a list of tab-delimited pairs of numeric indices, e.g.,
```
		54\t91\n
```
  2. the network described is a **SINGLE COMPONENT**
  3. there are **NO SELF-LOOPS** or **MULTI-EDGES** in the file; you can use
     the 'netstats' utility to extract the giantcomponent (-gcomp.pairs)
     and then use that file as input to this program
  4. the `MINIMUM NODE ID = 0` in the input file; the maximum can be
     anything (the program will infer it from the input file)

Description of command line arguments:

* `-f <filename>` give the target `.pairs` file to be processed
* `-l <text>`the text label for this run; used to build output filenames
* `-t <int>` timer period for reporting progress of file input to screen
* `-s` calculate and record the support of the `dQ` matrix
* `-v --v ---v`	differing levels of screen output verbosity
* `-o <directory>` directory for file output
* `-c <int>` record the agglomerated network at step `<int>`

## Algorithm

See http://www.arxiv.org/abs/cond-mat/0408187 for more information

  - read network structure from data file (see below for constraints)
  - builds dQ, H and a data structures
  - runs new fast community structure inference algorithm
  - records Q(t) function to file
  - (optional) records community structure (at t==cutstep)
  - (optional) records the list of members in each community (at t==cutstep)

## Compiling

On Debian install:
```
$ sudo apt-get install build-essential
```

And compile using `make`:

```
$ make
```

## License

GNU GPLv2

## Authors

  * Aaron Clauset  (aaron@cs.unm.edu)

### Collaborators

  * Dr. Cris Moore (moore@cs.unm.edu)
  * Dr. Mark Newman (mejn@umich.edu)
