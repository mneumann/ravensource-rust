# Issues

## Issue 1

The bootstrap compiler needs libstdc+.so.9, which does not exist in
Ravenports. 

Solution: Copy it from base DragonFly system:

    mkdir /raven/share/raven/toolchain/temp-rust-fix
	cp /usr/lib/gcc50/libstdc++.so.9 /raven/share/raven/toolchain/temp-rust-fix

## Issue 2

While building some Rust libraries, we get following failure:

    note: /raven/toolchain/bin/ld: cannot find -lgcc_pic

On Raveports we build with gcc8, which no longer has `libgcc\_pic.so`.
Instead it uses `libgcc\_s.so`. In Ravenports, symlinking these files is
tricky, as the tools are mounted read only. 
