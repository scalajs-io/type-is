Type-is API for Scala.js
================================
This is a Scala.js type-safe binding for [Type-is](https://www.npmjs.com/package/type-is)

Infer the content-type of a request.

#### Build Dependencies

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

```scala
import io.scalajs.nodejs.http.Http
import io.scalajs.npm.typeis.TypeIs
import scalajs.js

Http.createServer( (req, res) => {
    // req.headers.content-type = 'application/json' 
    import TypeIs._
    is(req, js.Array("json"))               // 'json'
    is(req, js.Array("html", "json"))       // 'json'
    is(req, js.Array("application/*"))      // 'application/json'
    is(req, js.Array("application/json"))   // 'application/json'
})
```

Using `Type-is` synchronously

```scala
  val hash = Type-is.hashSync(myPlaintextPassword, saltRounds)
  val isMatch = Type-is.compareSync(myPlaintextPassword, hash)
  println(s"The password was a match: $isMatch") // The password was a match: true
```

#### Artifacts and Resolvers

To add the Moment binding to your project, add the following to your build.sbt:  

```sbt
libraryDependencies += "io.scalajs.npm" %%% "type-is" % "0.3.0.3"
```

Optionally, you may add the Sonatype Repository resolver:

```sbt   
resolvers += Resolver.sonatypeRepo("releases") 
```