load("@crates//:defs.bzl", "aliases", "all_crate_deps")
load("@rules_rust//rust:defs.bzl", "rust_library")

rust_library(
    name = "highlight",
    aliases = aliases(),
    crate_name = "tree_sitter_highlight",
    crate_root = "src/lib.rs",
    deps = all_crate_deps(
        normal = True,
    ) + [
        #"@crates//:tree-sitter-cli",
        #"@crates//:tree-sitter",
        "//lib/language",
        "//lib",
        #":build_script"
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