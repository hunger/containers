# syntax=docker/dockerfile:1
FROM archlinux:latest AS base

RUN pacman -Sy --noconfirm --needed git mise rustup && \
    rm -rf /var/lib/pacman/s/* && \
    rm -rf /var/cache/pacman/pkg/*

ENV RUSTUP_HOME=/root/.rustup \
    CARGO_HOME=/root/.cargo \
    PATH="/root/.cargo/bin:${PATH}"

RUN rustup update stable --no-self-update && \
    rustup target add x86_64-unknown-linux-musl && \
    rustup component add clippy rustfmt

# Pre-fetch tools from the devbox repo's mise.toml into the system-wide
# install dir so CI runs don't re-download them.
COPY mise.toml /tmp/mise-prewarm/mise.toml
RUN cd /tmp/mise-prewarm && mise install --system && rm -rf /tmp/mise-prewarm
