load("@crates//:defs.bzl", "aliases", "all_crate_deps")
load("@rules_rust//rust:defs.bzl", "rust_library")

cc_library(
    name = "api",
    srcs = glob(
        [
            "src/*.c",
        ],
        exclude = [
            "src/lib.c",
        ],
    ) + glob(
        [
            "src/**/*.h",
        ],
    ),
    hdrs = [
        "include/tree_sitter/api.h",
    ],
    strip_include_prefix = "include/",
)

rust_library(
    name = "lib",
    srcs = glob(["binding_rust/*.rs"]),
    aliases = aliases(),
    compile_data = [
        "src/parser.h",
        "binding_rust/README.md",
    ],
    crate_features = ["std"],
    crate_name = "tree_sitter",
    crate_root = "binding_rust/lib.rs",
    proc_macro_deps = all_crate_deps(
        proc_macro = True,
    ),
    visibility = ["//visibility:public"],
    deps = all_crate_deps(
        normal = True,
    ) + [
        ":api",
        "//lib/language",
    ],
)
