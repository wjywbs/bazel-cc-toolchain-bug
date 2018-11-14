## bazel 0.19.0

```
bazel build ...
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

## bazel 0.19.1

```
bazel build ...
ERROR: toolchain/BUILD:17:1: in cc_toolchain rule //toolchain:cc-k8: Error while selecting cc_toolchain: Toolchain identifier 'cc-k8' was not found, valid identifiers are [stub_armeabi-v7a, local, msys_x64_mingw, msvc_x64]

bazel build ... --crosstool_top=//toolchain:toolchain
# PASS
```

Comment out `toolchain_identifier = "cc-k8",`:

```
bazel build ...
ERROR: toolchain/BUILD:17:1: in cc_toolchain rule //toolchain:cc-k8: Error while selecting cc_toolchain: No toolchain found for cpu 'k8'. Valid cpus from default_toolchain entries are: [
]. Valid toolchains are: [
  stub_armeabi-v7a: --cpu='armeabi-v7a' --compiler='compiler',
  local: --cpu='k8' --compiler='compiler',
  msys_x64_mingw: --cpu='x64_windows' --compiler='mingw-gcc',
  msvc_x64: --cpu='x64_windows' --compiler='msvc-cl',
]

bazel build ... --crosstool_top=//toolchain:toolchain
ERROR: No toolchain found for cpu 'k8'. Valid cpus from default_toolchain entries are: [
]. Valid toolchains are: [
  cc-k8: --cpu='k8' --compiler='local',
]

```
