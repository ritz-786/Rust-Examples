# Introduction

Greetings, one and all.  Today we shall explore how to build and
deploy a `ggez` game for every possible platform.  For platforms like
Linux it's pretty darn simple.  For ones like Android it gets
harder and you have to jump through hoops.  The purpose of this is to
document the hoops and give you a cookbook on the best jumping methods
and trajectories.  We will progress generally from the easiest to
hardest jumps.

## Project setup

We will use the `02_hello_world` example program from ggez for all these
examples.  To do the initial setup, assuming you have cargo installed:

```sh
cargo init --bin hello_world
cd hello_world
```

Now copy-paste the contents of
<https://raw.githubusercontent.com/ggez/ggez/master/examples/02_hello_world.rs>
into `hello_world/src/main.rs`, or if you are on Linux, just wget it:

```sh
wget https://raw.githubusercontent.com/ggez/ggez/master/examples/02_hello_world.rs -O src/main.rs
```

You'll need a font to print "Hello world!" with, so we need to fetch one and
put it in a subdirectory called `resources` in your project root:

```sh
mkdir resources
cd resources
wget https://raw.githubusercontent.com/ggez/ggez/master/resources/DejaVuSerif.ttf
```

Then edit your `Cargo.toml` with your favorite super duper editor and under `[dependencies]` add:

```
ggez = "0.5"
```

Now run `cargo run` and it should build
and run!  ...maybe.  It depends on what platform you're on and what
libraries you have installed.  To make super-duper sure you have all
the bits and pieces in the right places to make this always work, read
on!

# Linux

## Debian

Very easy, just install the required dev packages:

```sh
apt install libasound2-dev libudev-dev pkg-config
```

Then you should be able to build with `cargo run`

## Redhat

Same libraries as Debian, slightly different names.  On CentOS 7 at
least you can install them with:

```sh
yum install alsa-lib-devel
```

## Distributing

You should be able to just copy-paste the executable file and the `resources` directory to wherever you want.


# Windows

Should just build.  We recommend using the MSVC toolchain whenever possible, the MinGW one can be pretty jank and difficult to set up.

## Distributing

Just copy-paste the exe and resource files to the destination computer.

# Android

Not officially supported yet. ;_; See https://github.com/ggez/ggez/issues/70

# Web/wasm/emscripten

Not officially supported yet. ;_; See https://github.com/ggez/ggez/issues/71

