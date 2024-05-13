# load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# http_archive(
#     name = "build_bazel_rules_nodejs",
#     sha256 = "dddd60acc3f2f30359bef502c9d788f67e33814b0ddd99aa27c5a15eb7a41b8c",
#     strip_prefix = "rules_nodejs-6.1.0",
#     url = "https://github.com/bazelbuild/rules_nodejs/releases/download/v6.1.0/rules_nodejs-v6.1.0.tar.gz"
# )

# load("@build_bazel_rules_nodejs//:index.bzl", "node_repositories", "npm_install")

# node_repositories(package_json = ["//:package.json"])

# npm_install(
#     name = "npm",
#     package_json = "//:package.json",
#     package_lock_json = "//:package-lock.json",
# )

rules_nodejs_version = "6.1.0"

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "build_bazel_rules_nodejs",
    sha256 = "dddd60acc3f2f30359bef502c9d788f67e33814b0ddd99aa27c5a15eb7a41b8c",
    urls = [
        "https://github.com/bazelbuild/rules_nodejs/releases/download/v{version}/rules_nodejs-v{version}.tar.gz".format(
            version = rules_nodejs_version,
        ),
    ],
)

load("@build_bazel_rules_nodejs//:index.bzl", "yarn_install")

yarn_install(
    name = "npm",
    package_json = "//:package.json",
    yarn_lock = "//:yarn.lock",
)

load("@npm//:install_bazel_dependencies.bzl", "install_bazel_dependencies")

install_bazel_dependencies()

# Set up TypeScript toolchain
load("@npm_bazel_typescript//:index.bzl", "ts_setup_workspace")

ts_setup_workspace()