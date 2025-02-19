# Platforms docs

XQUIC currently supports `Android` , `iOS` , `Linux` and `MacOS` .

## Android/iOS Compile Script

The Android and iOS use `.so` files, there is a [ `xqc_build.sh` ](../xqc_build.sh) script in the xquic library directory, execute the script to compile to complete the corresponding compilation.

```bash
sh xqc_build.sh ios/android <build_dir> <artifact_dir>
```

> Note: You need to specify the IOS/andriod build toolchain before compiling, download and set the environment variable IOS_CMAKE_TOOLCHAIN or ANDROID_NDK, or directly modify CMAKE_TOOLCHAIN_FILE in `xqc_build.sh` .

## Linux Release

The default `CMAKE_BUILD_TYPE` is `Release` , so you only need to compile BoringSSL or BabaSSL, and then build xquic.

```bash
# build xquic with BabaSSL
git submodule update --init --recursive
mkdir build; cd build
cmake ..
make -j

# build xquic with BoringSSL
git submodule update --init --recursive
mkdir build; cd build
cmake -DSSL_TYPE=${SSL_TYPE_STR} -DSSL_PATH=${SSL_PATH_STR} -DSSL_INC_PATH=${SSL_INC_PATH_STR} -DSSL_LIB_PATH=${SSL_LIB_PATH_STR} ..
make -j
```

## MacOS Release

You can use the cmake variables `-DPLATFORM=mac` to build xquic on MacOS.

```bash
# build xquic with BabaSSL
git submodule update --init --recursive
mkdir build; cd build
cmake -DPLATFORM=mac ..
make -j

# build xquic with BoringSSL
git submodule update --init --recursive
mkdir build; cd build
cmake -DPLATFORM=mac -DSSL_TYPE=${SSL_TYPE_STR} -DSSL_PATH=${SSL_PATH_STR} -DSSL_INC_PATH=${SSL_INC_PATH_STR} -DSSL_LIB_PATH=${SSL_LIB_PATH_STR} ..
make -j
```
