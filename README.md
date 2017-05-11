[](This file is part of linux-patches. It is subject to the license terms in the COPYRIGHT file found in the top-level directory of this distribution and at https://raw.githubusercontent.com/libertine-linux/linux-patches/master/COPYRIGHT. No part of linux-patches, including this file, may be copied, modified, propagated, or distributed except according to the terms contained in the COPYRIGHT file.)
[](Copyright © 2016 The developers of linux-patches. See the COPYRIGHT file in the top-level directory of this distribution and at https://raw.githubusercontent.com/libertine-linux/linux-patches/master/COPYRIGHT.)

# linux-patches

[linux-patches] is a collection of patches to apply to a [linux-stable](https://github.com/libertine-linux-forks/linux-stable) kernel. Preference is given to those stable kernels that are longterm. Ordinarily, Libertine Linux keeps patches inside the relevant package (in this case `linux_prep`). However, because this patch set is so large it is inefficient and unfeasible to apply it as part of the build. Additionally, the generation of new Linux `.config` files (which we use in `package-configurations` as `linux-prep.mk`) is made substantially easier if a patched kernel sourceis available.


## Applicable Linux Version

Applicable Linux versions are modelled as folders in `patches/` and identify threefold versions, eg `4.4.35`. If a version isn't there, it isn't applicable.


## Patches

All patches are held in the `upstream` folder. They are then symlinked into version folders (eg `4.4.35`) under `patches`. They are then name prefixed `NNN-ORIGIN-`, with NNN a three digit number and ORIGIN on e of the values below. This approach ensures patches are applied in shell glob expansion order.

* `alpine-linux`: Patches from Alpine Linux's aports git repository
* `bfq`: Budget Fair Queuing (BFQ) disk scheduler patches
	* Downloaded from <http://algo.ing.unimo.it/people/paolo/disk_sched/patches>
* `ck1`: Contains the Brain Fuck Scheduler (BFS) and other Con Kolivas patches
	* ***NOT COMPATIBLE with current grsecurity and so NOT USED***
	* Downloaded from <http://ck.kolivas.org/patches/4.0/4.4/4.4-ck1/patch-4.4-ck1.xz>
	* `mkdir -m 0755 -p patches/ck1; wget -q -O - http://ck.kolivas.org/patches/4.0/4.4/4.4-ck1/patch-4.4-ck1.xz | unxz >patches/ck1/patch-4.4-ck1.patch`
* `grsecurity`: Contains grsecurity patches
	 * Are only publically available for the latest stable kernel release. They are not necessarily available publically without subscription for the latest longterm kernel release
	 * Alpine Linux maintains backports via their [aports package manager](git://git.alpinelinux.org/aports) in location `aports/main/linux-grsec/APKBUILD`
		 * Alpine Linux patches may be available via URLs such as:-
		 	 * `http://dev.alpinelinux.org/~ncopa/grsec/grsecurity-3.1-4.4.36-201604252206-alpine.patch`
			 * `http://dev.alpinelinux.org/~ncopa/grsec/hardened-3.1-4.9.27-201704252333-alpine.patch`
		 * Sadly these URLs are not secure
		 * These URLs will eventually go away as grsecurity will no longer maintain public patches
* `kernel_gcc_patch`
	* Provided as a git submodule from <https://github.com/graysky2/kernel_gcc_patch.git>
	* Patch itself then adjusted to work with MPSC by the developers of linux-patches
	* Actual patch then at upstream
* `musl-cross-make`
	* Patches provided originally in the git repository at <https://github.com/richfelker/musl-cross-make>
* `ours`
	* Patch to `vdso.c` to use `stdbool.h`
	* Patches created to support the musl c library. Inspired by work originally done by Sabotage Linux and Alpine Linux. 

## Licensing

The license for this project is MIT. Individual patches may be licensed differently. The patches in `musl/` are part of this project.

[linux-patches]: https://github.com/libertine-linux/linux-patches "linux-patches GitHub page"
