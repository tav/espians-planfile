---
id: argonought
tags: INFO
title: Argonought
---

There are literally hundreds of serialisation/exchange formats/protocols
available to us: [ASN.1], [Avro], [BERT], [BSON], [Etch], [Gob], [Hessian],
[JSON], [MessagePack], [Pickle], [Protocol Buffers], [S-Expressions],
[SOAP], [Thrift], [UBJSON], [XDR], [XML-RPC], [YAML], &c.

They are all brilliant in their own way. But, unfortunately, none of them
offer the full set of features that would be ideal and provided by Argonought:

* JSON-like simplicty.
* Efficient binary encoding.
* Rich set of builtin types -- currencies, location, sets, &c.
* Optional streaming support.
* Support for synchronous/async calls.
* Ability to define arbitrary environment/headers.
* Architecture independent representation.
* No need to escape binary data.
* Lexicographically sortable encoding.
* Dynamic (No IDLs or code generation).

[BERT] and BERT-RPC from GitHub are the closest existing format to the above
ideal. Unfortunately it doesn't support the much needed [lexicographically
sortable encoding](/item.argonought-lexicographically-sortable-representation-of-numbers)
or the full set of desired builtin types.

It may also be worth pointing out the downsides to the [CORBA](http://en.wikipedia.org/wiki/Common_Object_Request_Broker_Architecture)-esque
formats like Protocol Buffers and Thrift. These depend on specifications
being defined using an [IDL](http://en.wikipedia.org/wiki/Interface_description_language) and code
being generated to support the specification in target languages.

This can definitely be attractive in certain contexts, but it can also prove
to be a right pain as developers have to take on the burden of constantly
keeping both the IDL generated code *and* the app code up-to-date at
multiple locations.

For example, with Protocol Buffers, you'd have to first create a
specification:

  ```protobuf
  message Person {
      required string name = 1;
      required int32 id = 2;
      optional string email = 3;
  }
  ```

Then you'd have to generate the code for your target languages before you
can start doing anything, e.g.

  ```python
  person = Person()
  person.set_name("John Doe")
  person.set_id(1234)
  person.set_email("jdoe@example.com")
  ```

In contrast, consider the simplicity of JSON:

  ```javascript
  { "type": "Person",
    "name": "John Doe",
    "id": 1234,
    "email": "jdoe@example.com" }
  ```

It allows for dynamic development as there's no intermediate step. And
should the developer wish to add a new field, there'd be no need to update
the spec and the generated code in all target languages before making
changes to the actual application code!

[ASN.1]: http://en.wikipedia.org/wiki/Abstract_Syntax_Notation_One
[Avro]: http://hadoop.apache.org/avro/docs/current/
[BERT]: http://bert-rpc.org/
[BSON]: http://www.mongodb.org/display/DOCS/BSON
[Etch]: https://cwiki.apache.org/ETCH/
[Gob]: http://golang.org/pkg/gob/
[Hessian]: http://hessian.caucho.com/doc/hessian-overview.xtp
[JSON]: http://www.json.org/
[MessagePack]: http://msgpack.sourceforge.net/
[Pickle]: http://docs.python.org/library/pickle.html
[Protocol Buffers]: http://code.google.com/p/protobuf/
[S-Expressions]: http://en.wikipedia.org/wiki/S-expression
[SOAP]: http://www.w3.org/TR/soap/
[Thrift]: http://incubator.apache.org/thrift/
[UBJSON]: http://ubjson.org/
[XDR]: http://www.rfc-editor.org/rfc/rfc4506.txt
[XML-RPC]: http://www.xmlrpc.com/
[YAML]: http://www.yaml.org/