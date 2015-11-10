#secp256k1 bindings for Go#

**NOTE**: This fork is designed to update the abandoned (?) effort to
create Go bindings for `libsecp256k1`, a C language library designed to
efficiently interact with the secp256k1 elliptic curve used within the
Bitcoin network. My goals regarding this fork are the following.

1. Teach myself Go.
2. Learn the (in-flux as of Nov. 2015) libsecp256k1 API.
3. Create some code (probably unit tests) that test the Go bindings and
test the actual API.
4. Better familiarize myself with Git setup, command line Git commands,
etc.

I will, to the best of my ability, avoid any internal code that Pieter
doesn't want exposed. If I'm dropping the ball, let me know! This is a
learning process. I'm doing the best I can to figure things out as I go
but can always do better.

As time goes on, I will update previously written docs, try to find a
way to automate documentation (does Doxygen or something similar work
for Go?), etc. Maybe I'll throw it up on a website. We'll see.

Oh yeah, and forget about this code working. I've updated the secp256k1
submodule to the latest (as of 2015/11/10) version. The API has shifted
quite a bit since the bindings were last updated (Mar. 2015). I'll try
to keep the status updated in the commit history.

Thanks, and happy hacking!

Douglas Roark
2015/11/10

#ORIGINAL README TEXT#
##General info##
The Go API mirrors the API of the C implementation. Therefore,
please consult `c-secp256k1/include/secp256k1.h` for documentation.
Going forward I plan to implement a new API that is more aligned
with the APIs from Go's standard lib crypto packages. Then, it makes
more sense to add a standalone documentation, and hopefully breaking
changes in the C implementation can be abstracted away.

##How to build##
```bash
git submodule update --init
cd c-secp256k1
./autogen.sh && ./configure && make
cd ..
go install
```

##How to update##
```bash
git submodule update
cd c-secp256k1
make distclean && ./autogen.sh && ./configure && make
cd ..
go clean && go install
