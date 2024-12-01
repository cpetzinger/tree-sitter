load("@crates//:defs.bzl", "aliases", "all_crate_deps")
load("@rules_rust//rust:defs.bzl", "rust_library")

rust_library(
    name = "generate",
    aliases = aliases(),
    crate_name = "tree_sitter_generate",
    #crate_root = "src/main.rs",
    deps = all_crate_deps(
        normal = True,
    ) + [
        #"@crates//:tree-sitter-cli",
        #"@crates//:tree-sitter",
        "//lib/language",
        "//lib"
    ],
    proc_macro_deps = all_crate_deps(
       proc_macro = True,
    ),
    crate_features = ["std"],
    srcs = glob(["src/**/*.rs"]),
    compile_data = [
        "src/templates/alloc.h",
        "src/templates/array.h",
        "src/dsl.js"
    ],
    visibility = ["//visibility:public"],
)