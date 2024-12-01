load("@crates//:defs.bzl", "aliases", "all_crate_deps")
load("@rules_rust//rust:defs.bzl", "rust_library")
load("@rules_rust//cargo:defs.bzl", "cargo_build_script")

cargo_build_script(
    name = "build_script",
    srcs = ["build.rs"],
    data = [
        "emscripten-version",
    ],
    # Optional environment variables passed during build.rs compilation
    rustc_env = {
        "EMSCRIPTEN_VERSION": "0.0.0",
        "TARGET": "x86_64-unknown-linux-gnu",
        "HOST": "x86_64-unknown-linux-gnu",
    },
)

rust_library(
    name = "loader",
    srcs = glob(["src/**/*.rs"]),
    aliases = aliases(),
    compile_data = [
        "README.md",
    ],
    crate_name = "tree_sitter_loader",
    crate_root = "src/lib.rs",
    crate_features = ["std", "tree-sitter-highlight","tree-sitter-tags"],
    proc_macro_deps = all_crate_deps(
        proc_macro = True,
    ),
    visibility = ["//visibility:public"],
    deps = all_crate_deps(
        normal = True,
    ) + [
        ":build_script",
        "//lib",
        "//tags",
        "//highlight"
    ],
)
