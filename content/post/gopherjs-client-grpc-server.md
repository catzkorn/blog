+++
date = "2017-04-17T19:58:04+01:00"
draft = true
title = "GopherJS Client and gRPC Server"
+++
I've been using [gRPC](http://www.grpc.io/) and [Go](https://golang.org/) a lot in the last year.
At [Cognitive Logic](https://www.cognitivelogic.com) every one of our backend services is
implemented with Go and gRPC, and it enables us to abstract away most of the complexities
of networked micro services and keep interfaces typed and well defined using
[Google protobuffers](https://developers.google.com/protocol-buffers/).

I really enjoy using both, but sometimes I need to write a frontend to a
web server and I despise writing Javascript. So what do? Use Go of course!

With [GopherJS](https://github.com/gopherjs/gopherjs) it's possible to write safe
statically typed code that transpiles to Javascript. It comes with a couple of
quirks but as long as I don't have to use Javascript I'm happy.

Naturally, I want to be able to use Go and gRPC in the backend as well if I can,
and with the use of the[gRPC HTTP Gateway](https://github.com/grpc-ecosystem/grpc-gateway)
it becomes as simple as writing a normal gRPC service.

So what are the steps required to get a GopherJS frontend client talking to a gRPC backend
seamlessly? In short:

* [Create the protobuf interface](/post/gopherjs-client-grpc-server-1/)
* [Implement the server](#server)
* [Implement the client](#client)
* [Putting it all together](#main)

If you want to skip ahead, the finished example can be found on
[my github](https://github.com/johanbrandhorst/gopherjs-grpc-websocket).

## Preparation
Some structure will help organization. Let's create a `client`, `server`, and `protos` folder:

```bash
$ tree -L 1 -d
.
|-- client
|-- protos
`-- server
```

Next up we'll create the proto interface.

[Part 1](/post/gopherjs-client-grpc-server-1/)