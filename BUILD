load("@bazel_tools//tools/jdk:default_java_toolchain.bzl", "VANILLA_TOOLCHAIN_CONFIGURATION", "default_java_toolchain")

# Define a java_toolchain and a toolchain for building java_library, java_binary targets, etc.
# The important bit to distinguish these from above is: @bazel_tools//tools/jdk:toolchain_type (inside default_java_toolchain)
default_java_toolchain(
    name = "java_toolchain_11",
    configuration = VANILLA_TOOLCHAIN_CONFIGURATION,
    java_runtime = "@optjdk//:jdk",
    source_version = "11",
    target_version = "11",
)
config_setting(
    name = "java_runtime_version_11_setting",
    values = {"java_runtime_version": "11"},
)

toolchain(
    name = "java_runtime_toolchain_11",
    target_settings = [":java_runtime_version_11_setting"],
    toolchain = "@optjdk//:jdk",
    # Not strictly necessary as we do not deal with any other OS or CPU
    # exec_compatible_with = [
    #     "@platforms//os:linux",
    #     "@platforms//cpu:x86_64",
    # ],
    toolchain_type = "@bazel_tools//tools/jdk:runtime_toolchain_type",
)

java_binary(
	name = 'foo',
	main_class = "Foo",
	srcs = ["Foo.java"],
)
