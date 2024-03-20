.PHONY: dist

PKG_VERSION := $(shell cargo metadata --no-deps --format-version 1 | jq -r '.packages[0].version')

debug-amd64:
	cross build --target x86_64-unknown-linux-musl

release-amd64:
	cross build --target x86_64-unknown-linux-musl --release

dist:
	# Keep these in this order, as aarch64 is based on Debian Buster (older),
	# the others on Bullseye. For some build scripts we want to build against
	# least recent LIBC.
	cross build --target aarch64-unknown-linux-musl --release

	mkdir -p ../dist

test:
	cargo fmt --check
	cargo clippy --no-deps
	TZ=UTC cargo test

test-all:
	cargo fmt --check
	cargo clippy --no-deps
	TZ=UTC cargo test --features test-all-integrations
