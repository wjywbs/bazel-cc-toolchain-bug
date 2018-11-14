bazel 0.19.0

```
bazel build ...
INFO: Build options have changed, discarding analysis cache.
ERROR: toolchain/BUILD:17:1: in cc_toolchain rule //toolchain:cc-k8: Error while selecting cc_toolchain: Toolchain identifier 'cc-k8' was not found

bazel build ... --crosstool_top=//toolchain:toolchain
# PASS
```

However, if `toolchain_identifier = "cc-k8",` in toolchain/BUILD is commented out:

```
bazel build ...
# PASS

bazel build ... --crosstool_top=//toolchain:toolchain
ERROR: No toolchain found for cpu 'k8'. Valid cpus from default_toolchain entries are: [
]. Valid toolchains are: [
  cc-k8: --cpu='k8' --compiler='local',
]
```

