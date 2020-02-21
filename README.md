# izumi-reflect

> In case something looks like a TypeTag and works like a TypeTag it may be considered as a replacement for the TypeTag

`izumi-reflect` is a fast, lightweight, portable and efficient alternative for `TypeTag` from `scala-reflect`.

`izumi-reflect` uses its own lightweight model of Scala types and provides a simulator of an important part of Scala typechecker.

## Why it's better than `scala-reflect`

1. `izumi-reflect` compiles and initializes lot faster than `scala-reflect` tags,
2. `izumi-reflect` supports ScalaJS and ScalaNative,
3. `izumi-reflect` allows you to obtain tags to unapplied types `F[_]` and combine then in runtime.

## Credits

`izumi-reflect` has been implemented by [7mind](https://7mind.io) as part of [Izumi](https://github.com/7mind/izumi) and donated to ZIO.
This repository contains an independent and more conservative copy of the code comparing to Izumi one.

<p align="center">
  <a href="https://izumi.7mind.io/">
  <img width="40%" src="https://github.com/7mind/izumi/blob/develop/doc/microsite/src/main/tut/media/izumi-logo-full-purple.png?raw=true" alt="Izumi"/>
  </a>
</p>


## Limitations

`izumi-reflect` model is imperfect, though "good enough" for the vast majority of the usecases.

Known limitations are:

1. Type boundaries support is very limited because of a [problematic behavior](https://github.com/scala/bug/issues/11673) of Scala 2.13 compiler
2. Path-Dependent Types are handled by symbolic names and may cause unexpected false-positives (comparing to Scala typer)

## Build

`build.sbt` is generated by [sbtgen](https://github.com/7mind/sbtgen). During development you may not want to mess with ScalaJS and ScalaNative, you may generate a pure-JVM Scala project:

```bash
./sbtgen.sc
```

Once you finished tinkering with the code you may want to generate full project and test it for all the platforms:

```bash
./sbtgen.sc --js --native
```
