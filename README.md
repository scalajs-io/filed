Filed API for Scala.js
================================
This is a Scala.js type-safe binding for [Filed](https://www.npmjs.com/package/filed)

A Simplified file library.

#### Build Requirements

* [ScalaJs.io v0.3.x](https://github.com/ldaniels528/scalajs.io)
* [SBT v0.13.13](http://www.scala-sbt.org/download.html)


#### Build/publish the SDK locally

```bash
 $ sbt clean publish-local
```

#### Running the tests

Before running the tests the first time, you must ensure the npm packages are installed:

```bash
$ npm install
```

Then you can run the tests:

```bash
$ sbt test
```

#### Examples

If you pipe it to a destination it'll be a read stream.

```scala
Filed("/myfile").pipe(Fs.createWriteStream("/out"))
```

And of course you can pipe a filed object from itself to itself and it'll figure it out.

```scala
Filed("/myfile").pipe(Filed("/newfile"))
```

Those familiar with request will be familiar seeing object capability detection when doing HTTP. 
`Filed` does this as well.

```scala
Http.createServer((req, resp) => Filed("/data.json").pipe(resp))
```

#### Artifacts and Resolvers

To add the Moment binding to your project, add the following to your build.sbt:  

```sbt
libraryDependencies += "io.scalajs.npm" %%% "filed" % "0.3.0.3"
```

Optionally, you may add the Sonatype Repository resolver:

```sbt   
resolvers += Resolver.sonatypeRepo("releases") 
```
