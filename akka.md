# Actors

- Non-blocking operations and safeguard internal state from other objects
- Asynchronous
- No race conditions


# Streams

`Source` are parameterized with source data type, and auxilliary value type from source, or `akka.NotUsed`

`Sink` is the receiver of data

```Scala
val done: Future[Done] = source.runForeach(i ⇒ println(i))(materializer)

implicit val ec = system.dispatcher
done.onComplete(_ ⇒ system.terminate())
```

`Flow` is a starting point that is like a source but with an “open” input

Use `throttle` to limit rate of processing and create backpressure
