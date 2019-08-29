exports_files(
    ["tsconfig.json"],
    visibility = ["//:__subpackages__"],
)

load("@npm_bazel_typescript//:index.bzl", "ts_devserver")
load("@npm_bazel_typescript//:index.bzl", "ts_library")
load("@build_bazel_rules_nodejs//:defs.bzl", "rollup_bundle")

ts_library(
    name = "app",
    srcs = [
        "src/main.tsx",
    ],
    tsconfig = "//ui:tsconfig.json",
    deps = [
        "@npm//@types/react",
        "@npm//@types/react-dom",
        "@npm//react",
        "@npm//react-dom",
    ],
)

rollup_bundle(
    name = "bundle",
    entry_point = "src/main.tsx",
    deps = [":app"],
)

ts_devserver(
    name = "devserver",
    port = 9999,
    serving_path = "/bundle.es2015.js",
    static_files = [
        ":index.html",
    ],
    deps = [
        ":app",
    ],
)
