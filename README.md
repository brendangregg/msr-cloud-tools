MSR Cloud Tools
===============

Some Model Specific Register (MSR) tools for Xen guests (eg, AWS EC2). So far only written for Intel(R) Xeon(R) CPU E5-2670 v2s (Ivy Bridge).

Tested on Ubuntu Trusty.

## Prereqs

```
# sudo apt-get install msr-tools
# sudo modprobe msr
```

## Contents

- [showboost](showboost): show the real CPU clock rate to understand the current level of turbo boost.
- [cputemp](cputemp): show per-CPU temperatures.
- [cpuhot](cpuhot): show per-CPU temperature throttle flags (from IA32_THERM_STATUS 15:0), for evidence of thermal throttling.
