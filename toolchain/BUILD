package(
    default_visibility = ["//visibility:public"],
)

cc_toolchain_suite(
    name = "toolchain",
    toolchains = {
        "k8": ":cc-k8",
    },
)

filegroup(
    name = "empty",
    srcs = [],
)

cc_toolchain(
    name = "cc-k8",
    all_files = ":empty",
    compiler_files = ":empty",
    cpu = "k8",
    dwp_files = ":empty",
    dynamic_runtime_libs = [":empty"],
    linker_files = ":empty",
    objcopy_files = ":empty",
    static_runtime_libs = [":empty"],
    strip_files = ":empty",
    supports_param_files = 1,
    toolchain_identifier = "cc-k8",
)
