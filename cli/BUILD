load("@crates//:defs.bzl", "aliases", "all_crate_deps")
load("@rules_rust//rust:defs.bzl", "rust_binary", "rust_library")

rust_library(
    name = "cli",
    srcs = glob(["src/**/*.rs"]),
    aliases = aliases(),
    compile_data = [
        "README.md",
        "vendor/xterm-colors.json",
        "src/playground.html",
    ] + glob(
        ["src/templates/*"],
        exclude = ["src/templates/*.rs"],
    ),
    crate_name = "tree_sitter_cli",
    proc_macro_deps = all_crate_deps(
        proc_macro = True,
    ),
    visibility = ["//visibility:public"],
    #crate_root = "src/main.rs",
    deps = all_crate_deps(
        normal = True,
    ) + [
        "//cli/config",
        "//cli/generate",
        "//cli/loader",
        "//highlight",
        "//lib",
        "//lib/language",
        "//tags",
    ],
)

rust_binary(
    name = "tree-sitter",
    srcs = ["src/main.rs"],
    aliases = aliases(),
    crate_root = "src/main.rs",
    proc_macro_deps = all_crate_deps(
        proc_macro = True,
    ),
    deps = all_crate_deps(
        normal = True,
    ) + [
        ":cli",
        "//cli/config",
        "//cli/generate",
        "//cli/loader",
        "//highlight",
        "//lib",
        "//tags",
    ],
)
