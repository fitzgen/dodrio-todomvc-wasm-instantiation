# Timing Wasm Instantiation Methods

This is a fork of [the `dodrio` implementation of
TodoMVC](https://github.com/fitzgen/dodrio/tree/master/examples/todomvc). It has
been modified to allow forcing Wasm instantiation to be either:

* waiting for the full network request for the `.wasm` to complete, and then
  passing the results to `WebAssembly.instantiate`,

* or using `WebAssembly.instantiateStreaming` to pipeline validation,
  compilation, and instantiation with the network request.

## Choosing Instantiation Strategy

To force enable pipelining and `instantiateStreaming`, add this query string to
the URL: `?forceEnableInstantiateStreaming`. [Alternatively, click this link to
view the `gh-pages` hosted version of this demo with pipelining force
enabled.](https://fitzgen.github.io/dodrio-todomvc-wasm-instantiation/?forceEnableInstantiateStreaming)

To force disable pipelining and *not* use `instantiateStreaming`, add this query
string to the URL: `?forceDisableInstantiateStreaming`. [Alternatively, click
this link to view the `gh-pages` hosted version of this demo with pipelining
force
disabled.](https://fitzgen.github.io/dodrio-todomvc-wasm-instantiation/?forceEnableInstantiateStreaming)

Timing information will be logged to the devtools console.

## Build

```
wasm-pack build --target no-modules
```

## Serve Locally

Use any HTTP server that supports the `application/wasm` MIME type, for example:

```
$ cargo install miniserve
$ miniserve .
```
