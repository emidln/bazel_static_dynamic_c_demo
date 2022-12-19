# libbar is available as a dynamic library or a static library (default)
cc_library(
    name = "bar",
    srcs = ["bar.c"],
    hdrs = ["bar.h"],
)

# libqux is only available as a static library
cc_library(
    name = "qux",
    linkstatic = 1,
    srcs = ["qux.c"],
    hdrs = ["qux.h"],
)

# we explicitly say we want foo to not be static wherever possible
# since libqux is only available as a static library, we only link libbar
# dynamically
# use `lld bazel-bin/foo` (on Linux) or `otool -l bazel-bin/foo` (on MacOS) to check this
cc_binary(
    name = "foo",
    deps = [":bar", ":qux"],
    srcs = ["foo.c"],
    linkstatic = 0,
)
