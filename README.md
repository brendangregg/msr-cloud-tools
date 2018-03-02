MSR Cloud Tools
===============

Some Model Specific Register (MSR) tools for Xen guests (eg, AWS EC2).

## Prereqs

So far only written for Intel(R) Xeon(R) CPU E5-2670 v2s (Ivy Bridge).

Tested on Ubuntu Trusty.

```
# sudo apt-get install msr-tools
# sudo modprobe msr
```

## Contents

- [showboost](showboost): show the real CPU clock rate to understand the current level of turbo boost.
- [cputemp](cputemp): show per-CPU temperatures.
- [cpuhot](cpuhot): show per-CPU temperature throttle flags (from IA32_THERM_STATUS 15:0), for evidence of thermal throttling.

## Screenshots

Measure the actual clock rate for CPU 0:

<pre>
# <b>./showboost</b>
Base CPU MHz : 3000
Set CPU MHz  : 3000
Turbo MHz(s) : 3400 3500
Turbo Ratios : 113% 116%
CPU 0 summary every 1 seconds...

TIME       C0_MCYC      C0_ACYC        UTIL  RATIO    MHz
21:41:43   3021819807   3521745975     100%   116%   3496
21:41:44   3021682653   3521564103     100%   116%   3496
21:41:45   3021389796   3521576679     100%   116%   3496
21:41:46   3021685725   3521635645     100%   116%   3496
21:41:47   3021297135   3521362183     100%   116%   3496
[...]
</pre>

Show average CPU utilization, and per-CPU temperatures, every second:

<pre>
# <b>./cputemp -u 1</b>
AvgUtil CPU1 CPU2 CPU3 CPU4 CPU5 CPU6 CPU7 CPU8 CPU9 CPU10 CPU11 CPU12 CPU13 CPU14 CPU15 CPU16
56 77 77 77 73 76 78 77 72 77 76 76 74 75 79 77 73
57 77 76 77 75 75 79 76 72 77 76 77 74 76 78 77 73
57 77 76 77 74 76 78 76 73 77 77 77 73 76 78 77 72
57 77 76 77 73 76 78 77 73 77 76 77 74 76 79 77 73
57 77 77 77 73 76 78 77 72 77 76 77 74 76 78 75 72
57 77 77 77 73 76 79 76 73 77 76 77 73 76 79 76 73
58 77 76 77 73 76 78 77 72 77 77 77 74 77 78 77 73
[...]
</pre>

Check that no CPU thermal throttled flags have been set:

<pre>
# <b>./cpuhot</b>
- CPU1 CPU2 CPU3 CPU4 CPU5 CPU6 CPU7 CPU8 CPU9 CPU10 CPU11 CPU12 CPU13 CPU14 CPU15 CPU16
PROCHOT 95 95 95 95 95 95 95 95 95 95 95 95 95 95 95 95
Celsius 77 75 76 73 76 77 75 72 76 72 75 77 76 72 76 75
Flags 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0 0x0
</pre>
