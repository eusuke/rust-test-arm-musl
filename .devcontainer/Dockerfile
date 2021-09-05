FROM ubuntu:20.04

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
    ca-certificates \
    gcc-9-arm-linux-gnueabihf \
	gcc-9-cross-base \
	libgcc-9-dev-armhf-cross \
	libatomic1-armhf-cross \
	gcc-9-multilib \
	build-essential \
	linux-libc-dev \
	curl \
    git \
 && apt-get -y clean \
 && rm -rf /var/lib/apt/lists/*

RUN ln -s /usr/include/asm-generic/ /usr/include/asm

#ENV RUSTUP_HOME=/usr/local/rustup \
#    CARGO_HOME=/usr/local/cargo \
#    PATH=/usr/local/cargo/bin:$PATH

#RUN curl https://sh.rustup.rs -sSf | sh -s -- -y

#RUN rustup target add armv7-unknown-linux-musleabi

RUN adduser rust
USER rust

# install Rust
RUN curl https://sh.rustup.rs -sSf | sh -s -- -y
ENV PATH /home/rust/.cargo/bin:$PATH

# install cross target
RUN rustup target add armv7-unknown-linux-musleabi
ENV CC_armv7_unknown_linux_musleabi arm-linux-gnueabihf-gcc-9
