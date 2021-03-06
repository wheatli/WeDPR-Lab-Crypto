# ffi_c_crypto

## build with feature

``bash
cargo build --release
# or choose features
cargo build --features "wedpr_f_hex wedpr_f_signature_secp256k1" --no-default-features
``

# ffi ios

before compile 

- install openssl
- install xcode
- install ios toolchain

```bash
rustup target add aarch64-apple-ios armv7-apple-ios armv7s-apple-ios x86_64-apple-ios i386-apple-ios
```

open cross compile with openssl

```bash
# for example, in your environment
export PATH="/usr/local/opt/openssl/bin:$PATH"
export LDFLAGS="-L/usr/local/opt/openssl/lib"
export CPPFLAGS="-I/usr/local/opt/openssl/include"
export PKG_CONFIG_PATH="/usr/local/opt/openssl/lib/pkgconfig"
export PKG_CONFIG_ALLOW_CROSS=1
```

generate .h

```bash
cbindgen src/lib.rs -l c > wedpr_ffi_c_crypto.h
```

```bash
# for aarch64
cargo build --target=aarch64-apple-ios --release
```