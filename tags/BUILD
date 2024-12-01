load("@crates//:defs.bzl", "aliases", "all_crate_deps")
load("@rules_rust//rust:defs.bzl", "rust_library")

rust_library(
    name = "tags",
    srcs = glob(["src/*.rs"]),
    aliases = aliases(),
    compile_data = [
        "README.md",
    ],
    crate_features = ["std"],
    crate_name = "tree_sitter_tags",
    proc_macro_deps = all_crate_deps(
        proc_macro = True,
    ),
    visibility = ["//visibility:public"],
    deps = all_crate_deps(
        normal = True,
    ) + [
        "//lib",
    ],
)
