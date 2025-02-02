PT-BR

Introdução a Graphql

GraphQL[1] é uma linguagem de consulta criada pelo Facebook em 2012 e lançada publicamente em 2015.[2] É considerada uma alternativa para arquiteturas REST, além de oferecer um serviço runtime para rodar comandos e consumir uma API.

Why a GraphQL Client?
In the Clients section in the GraphQL part, we already covered the responsibilities of a GraphQL client on a higher level. It’s now time to get more concrete.

In short, we should use a GraphQL client for tasks that are repetitive and agnostic to the app we’re building. For example, being able to send queries and mutations without having to worry about lower-level networking details or maintaining a local cache. This is functionality we’ll want in any frontend application that’s talking to a GraphQL server. Why build these features yourself when we can use one of the amazing GraphQL clients out there?

There are several GraphQL client libraries available that all give us varying degrees of control over ongoing GraphQL operations and come with different benefits and drawbacks. For very simple use cases (such as writing scripts), graphql-request might already be enough for our needs. Libraries like it are thin layers around sending HTTP requests to our GraphQL API.

Chances are that you’re writing a somewhat larger application where you want to benefit from caching, optimistic UI updates and other handy features. In these cases you’ll likely want to use a full GraphQL client that handles the lifecycle of all your GraphQL operations. You have the choice between Apollo Client, Relay, and urql.

Apollo vs Relay vs urql
The most common question heard from people that are getting started with GraphQL on the frontend is which GraphQL client they should use. We’ll try to provide a few hints that’ll help you decide which of these clients is the right one for your next project!

Relay is Facebook’s homegrown GraphQL client that they open-sourced alongside GraphQL in 2015. It incorporates all the learnings that Facebook gathered since they started using GraphQL in 2012. Relay is heavily optimized for performance and tries to reduce network traffic where possible. An interesting side-note is that Relay itself actually started out as a routing framework that eventually got combined with data loading responsibilities. It thus evolved into a powerful data management solution that can be used in JavaScript apps to interface with GraphQL APIs.

The performance benefits of Relay come at the cost of a notable learning curve. Relay is a complex framework and understanding all of its intricacies does require some time. The overall situation in that respect has improved with the release of the 1.0 version, called Relay Modern, but if you’re looking for something to just get started with GraphQL, Relay might not be the right choice just yet.

Apollo Client is a community-driven effort to build an easy-to-understand, flexible and powerful GraphQL client. Apollo has the ambition to build one library for every major development platform that people use to build web and mobile applications. Right now there is a JavaScript client with bindings for popular frameworks like React, Angular, Ember or Vue as well as early versions of iOS and Android clients. Apollo is production-ready and has features like caching, optimistic UI, subscription support and more.

urql is a more dynamic approach on GraphQL clients and a newer project compared to Relay and Apollo. While it’s highly focused on React, at its core it focuses on simplicity and extensibility. It comes with the barebones to build an efficient GraphQL client, but gives you full control over how it processes GraphQL operations and results via “Exchanges”. Together with the first-party exchange @urql/exchange-graphcache it is basically equivalent in functionality with Apollo, but with a smaller footprint and a very focused API.