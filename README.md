# Access to kallsyms on Linux 5.7+

`kallsyms_lookup_name` is a wonderful interface that is useful for quickly hacking kernel code without recompiling most of default kernels. Unfortunately, it is also very easy to abuse it, and deincentivizes hardware manufacturers from open-sourcing their drivers and adding them to mainline kernel tree. This is one of the reasons, why the function was unexported in Linux release 5.7.

This library is meant specifically for hacking the kernel code away, for not too serious projects - those that almost certainly wouldn't be included in the kernel. It uses the kernel livepatching interface which has been available at least in 5.0+, to trick it into giving us the `kallsyms_lookup_name` address without actually patching the function. As long as there isn't an active patch on the function, this method should work just fine.
