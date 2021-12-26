# DaWaPack AsyncAPI contract sample

The AsyncAPI Specification is a project used to describe and document message-driven APIs in a machine-readable format.
It’s protocol-agnostic, so we can use it for APIs that work over any protocol.

The AsyncAPI Specification defines a set of files required to describe such an API. These files can then be used to
create utilities, such as documentation, integration and/or testing tools.

In this example, we built an isolated application with publishing and consuming capabilities. The daemon part of the
application handle channels declarations and workers using it.

- `dawapack.yml` file describes operations the `workers` accepts.
- `infrastructure.yml` file describes channels the `daemon` **MUST** declare.

## Definitions

### Application

An application is any kind of computer program or a group of them. It **MUST** be a producer, a consumer or both.
An application **MAY** be a microservice, IoT device (sensor), mainframe process, etc. An application **MAY** be written
in any number of different programming languages as long as they support the selected protocol. An application **MUST**
also use a protocol supported by the server in order to connect and exchange messages.

### Producer / Publisher

A producer is a type of application, connected to a server, that is creating messages and addressing them to channels.
A producer **MAY** be publishing to multiple channels depending on the server, protocol, and use-case pattern.

### Consumer / Subscriber

A consumer is a type of application, connected to a server via a supported protocol, that is consuming messages from
channels. A consumer **MAY** be consuming from multiple channels depending on the server, protocol, and the use-case
pattern.

### Message

A message is the mechanism by which information is exchanged via a channel between servers and applications. A message
**MUST** contain a payload and **MAY** also contain headers. The headers **MAY** be subdivided into protocol-defined
headers and header properties defined by the application which can act as supporting metadata. The payload contains the
data, defined by the application, which **MUST** be serialized into a format (JSON, XML, Avro, binary, etc.). Since a
message is a generic mechanism, it can support multiple interaction patterns such as event, command, request, or
response.

### Channel

A channel is an addressable component, made available by the server, for the organization of messages. Producer
applications send messages to channels and consumer applications consume messages from channels. Servers **MAY** support
many channel instances, allowing messages with different content to be addressed to different channels. Depending on the
server implementation, the channel **MAY** be included in the message via protocol-defined headers.

### Protocol

A protocol is the mechanism (wireline protocol or API) by which messages are exchanged between the application and the
channel. Example protocols include, but are not limited to, AMQP, HTTP, JMS, Kafka, Anypoint MQ, MQTT, STOMP, Mercure,
WebSocket.

### Bindings

A "binding" (or "protocol binding") is a mechanism to define protocol-specific information. Therefore, a protocol
binding **MUST** define protocol-specific information only.