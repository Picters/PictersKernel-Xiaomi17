Picters CPU performance controls
===============================

The optional ``CONFIG_PICTERS_PERF`` driver manages independent CPU frequency
QoS requests. It does not replace the active governor, change the supported
frequency table, or remove requests owned by thermal cooling devices. The
existing kernel bases and KMI generation are unchanged.

The interface is under ``/sys/kernel/picters_perf``:

* ``capabilities`` reports ``api=2 cpu_max_freq cpu_min_freq``.
* ``available`` lists ``<first-related-cpu>:<hardware-maximum-kHz>``.
* ``cpu_max_freq`` accepts ``<cpu>:<kHz>`` pairs for independent maximum
  requests. Writing ``<cpu>:0`` removes that policy's request.
* ``cpu_min_freq`` accepts the same pairs for independent minimum requests.
  Writing ``<cpu>:0`` removes the minimum request without changing the maximum.
* ``profile`` is a label round-tripped by the application, with no policy side
  effects in the driver.

For example, ``echo '0:3000000 6:4000000' > cpu_min_freq`` requests those
minimums for the two CPU policies. The hardware's existing range bounds every
request. Existing thermal maximums still limit the effective frequency.
Requests are removed with a policy and reinstated when the policy is created
again, so CPU hotplug does not lose the configured state.

Gaming and frequency locking
----------------------------

The PictersKernelPack application discovers the available governors for each CPU
policy and GPU devfreq domain. Gaming selects ``performance`` only where the
driver exposes it; unsupported domains are reported in the interface. The
previous live governor of each changed domain is saved and restored when
leaving Gaming. The default boot governor is unchanged.

Frequency locking is a separate application setting. CPU minimum requests
use ``cpu_min_freq`` when the running kernel provides it, with the existing
writable minimum-frequency sysfs interface as a fallback. GPU minimums use
the driver's writable devfreq minimum. Original minimums are saved before
changing them and restored when unlocking. No thermal or charging interface
is modified by this driver.

Local validation
----------------

The ARM64 driver object has been compiled against the Android 16 / 6.12.23
source. Application tests exercise sysfs simulations for independent governors
and locks, restoration, readback failures and rollback. PictersKernelPack boot-service
tests exercise persisted requests with the feature enabled and disabled.
These checks do not establish device runtime, vendor CRC, or boot compatibility
for a newly built image; both kernel variants still require build and device
verification before release.
