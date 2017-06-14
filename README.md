[](This file is part of linux-patches. It is subject to the license terms in the COPYRIGHT file found in the top-level directory of this distribution and at https://raw.githubusercontent.com/libertine-linux/linux-patches/master/COPYRIGHT. No part of linux-patches, including this file, may be copied, modified, propagated, or distributed except according to the terms contained in the COPYRIGHT file.)
[](Copyright © 2016 The developers of linux-patches. See the COPYRIGHT file in the top-level directory of this distribution and at https://raw.githubusercontent.com/libertine-linux/linux-patches/master/COPYRIGHT.)

# linux-patches

[linux-patches] is a collection of patches to apply to a [linux-stable](https://github.com/libertine-linux-forks/linux-stable) kernel. Preference is given to those stable kernels that are longterm. Ordinarily, Libertine Linux keeps patches inside the relevant package (in this case `linux_prep`). However, because this patch set is so large it is inefficient and unfeasible to apply it as part of the build. Additionally, the generation of new Linux `.config` files (which we use in `package-configurations` as `linux-prep.mk`) is made substantially easier if a patched kernel sourceis available.


## Applicable Linux Version

Applicable Linux versions are modelled as folders in `patches/LINUX_VERSION` and identify threefold versions, eg `4.9.31` for `LINUX_VERSION`. If a version isn't there, it isn't applicable.

## Order of Application

The `grsecurity` patch is applied first, followed by `ours`, then by any remaining third-party patches in `patches/LINUX_VERSION`.

The patch `ours` is generated automatically by `upstream/ours/create-our-patch` from files in `upstream/ours/LINUX_VERSION`.


## Patches

All patches are held in the `upstream` folder. They are then symlinked into version folders (eg `4.4.35`) under `patches`. They are then name prefixed `NNN-ORIGIN-`, with NNN a three digit number and ORIGIN one of the values below. This approach ensures patches are applied in shell glob expansion order. Patches for `grsecurity` and `ours` are applied before these patches.

We are aware of patches for the Budget Fair Queuing ([BFQ](http://algo.ing.unimo.it/people/paolo/disk_sched/patches)) disk scheduler and Con Kolivas' [cq1](http://ck.kolivas.org/patches/4.0/4.4/4.4-ck1/patch-4.4-ck1.xz) patches (the Brain Fuck Scheduler (BFS) and others) but these are not currently compatible with grsecurity.


### `ours` patch

* Fixes to support musl
	* We have incorporated a patch for Linux 4.4.10, `0001-archscripts.diff` from [musl-cross-make](https://github.com/richfelker/musl-cross-make) into ours
	* We patch `vdso2c.c` to include `stdbool.h`
		* Inspired by work originally done by Sabotage Linux and Alpine Linux.
	* We patch various exported Linux kernel headers to support musl, particularly for compiling BusyBox
		* Inspired by work originally done by Sabotage Linux and Alpine Linux.
* Fixes to support hardening
	* We apply a 'default PIE' adjusted gcc setting so that the default GCC can be static PIE hardened
		* Inspired by work originally done by Sabotage Linux and Alpine Linux.
* Fixes to optimise compilation for modern 64-bit x85 CPUs
	* We make changes that are broadly the same as graysky's [kernel_gcc_patch](https://github.com/graysky2/kernel_gcc_patch.git)
	* We have adjusted these to work with grsecurity


## Licensing

The license for this project is MIT. The grsecurity patch is currently GPL 2.

[linux-patches]: https://github.com/libertine-linux/linux-patches "linux-patches GitHub page"
