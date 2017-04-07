Filed API for Scala.js
================================
[filed](https://www.npmjs.com/package/filed) - Simplified file library.

### Description

**Super simple to use**

Filed does a lazy stat call so you can actually open a file and begin writing to it and if the 
file isn't there it will just be created.

### Build Requirements

* [SBT v0.13.13](http://www.scala-sbt.org/download.html)


### Build/publish the SDK locally

```bash
 $ sbt clean publish-local
```

### Running the tests

Before running the tests the first time, you must ensure the npm packages are installed:

```bash
$ npm install
```

Then you can run the tests:

```bash
$ sbt test
```

### Examples

If you pipe it to a destination it'll be a read stream.

```scala
import io.scalajs.nodejs.fs.Fs
import io.scalajs.npm.filed._

Filed("/myfile").pipe(Fs.createWriteStream("/out"))
```

And of course you can pipe a filed object from itself to itself and it'll figure it out.

```scala
import io.scalajs.npm.filed._

Filed("/myfile").pipe(Filed("/newfile"))
```

Those familiar with request will be familiar seeing object capability detection when doing HTTP. 
`Filed` does this as well.

```scala
import io.scalajs.nodejs.http.Http
import io.scalajs.npm.filed._

Http.createServer((req, resp) => Filed("/data.json").pipe(resp))
```

### Artifacts and Resolvers

To add the `Filed` binding to your project, add the following to your build.sbt:  

```sbt
libraryDependencies += "io.scalajs.npm" %%% "filed" % "0.4.0-pre3"
```

Optionally, you may add the Sonatype Repository resolver:

```sbt   
resolvers += Resolver.sonatypeRepo("releases") 
```
