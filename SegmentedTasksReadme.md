# Segmented Taks

This is a fork of LitmusRT, a realtime extension of the Linux kernel. This fork adds support scheduling segmented tasks.

## Installation
Follow the installation instructions at www.litmus-rt.org/installation using this repo. Use the fork of liblimuts in place of the normal liblitmus installation. Note that i first tried following those instructions using Ubuntu 18, which resulted in several compiler errors. Ubuntu 16.04 worked for me.

This repo expects to be placed in the same directoy as the litmus-rt and liblitmus folders.

## Implementation
The new schedulers are implemented in `litmus/sched_psfp.c` and `litmus/sched_rtes.c`.

To support the new schedulers, two new callbacks have been added to the `sched_plugin` struct. These callbacks are called at the start and end of segments.

New fields have been added to the `rt_task` struct, which contains the definition for a real-time task, to allow setting per-segments parameters. See `segrtspin` in `liblitmus` for an example.

