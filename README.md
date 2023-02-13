# objc-ubuntu-helloworld

This is a how-to guide for setting up a simple Objective-C project on Ubuntu.

It is based on the 'libobjc2' project and doesn't require the GNUstep libraries.

## Install dependencies

    sudo apt-get install clang cmake
    git clone https://github.com/gnustep/libobjc2.git
    cd libobjc2
    git submodule init && git submodule update
    mkdir Build && cd Build
    cmake .. -DCMAKE_C_COMPILER=clang -DCMAKE_CXX_COMPILER=clang++
    make -j8
    sudo -E make install
    sudo ldconfig

## Create a "main.m" file

#include <stdio.h>
int main() {
    @autoreleasepool {
         printf("Hola món\n");
    }
    return 0;
}

## Compile and run

    clang main.m -fobjc-runtime=gnustep-2.0 -L/usr/local/lib -lobjc -o main
    ./main