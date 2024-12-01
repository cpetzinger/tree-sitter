load("@crates//:defs.bzl", "aliases", "all_crate_deps")
load("@rules_rust//rust:defs.bzl", "rust_library")

rust_library(
    name = "config",
    aliases = aliases(),
    crate_name = "tree_sitter_config",
    #crate_root = "src/main.rs",
    deps = all_crate_deps(
        normal = True,
    ) + [
        "//lib/language",
        "//lib"
    ],
    proc_macro_deps = all_crate_deps(
       proc_macro = True,
    ),
    srcs = glob(["src/**/*.rs"]),
    compile_data = [
        "README.md"
    ],
    visibility = ["//visibility:public"],
)