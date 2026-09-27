# gpui_http_client

This is a fork of `gpui_http_client` 0.2.2, kept for [cabin](https://github.com/Lyamc/cabin).

Upstream enables `zed-reqwest`'s `rustls-tls-native-roots` feature, which selects the `ring` cryptography provider. `ring` compiles C and assembly with `cc`. This fork uses `rustls-tls-native-roots-no-provider` and installs [rustls-graviola](https://github.com/ctz/graviola) as the rustls provider. Graviola is pure Rust. Its optional ML-KEM feature is left off, because that pulls `libcrux-platform`, which depends on `libc`. Call `install_tls_provider` before building a TLS client; GPUI does that from `Application::new`.
