load("@build_bazel_rules_apple//apple:ios.bzl", "ios_application")
load("@build_bazel_rules_swift//swift:swift.bzl", "swift_library")

exports_files([
    "Launch.storyboard",
])

filegroup(
    name = "AppIcon.xcassets",
    srcs = glob(["AppIcon.xcassets/**"]),
)

swift_library(
    name = "Sources",
    srcs = [
        "AppDelegate.swift",
    ],
    module_name = "Sources",
    private_deps = [
        "//srcs/A:a_lib",
        "//srcs/B:b_lib",
    ]
    # deps = [
    #     "//srcs/A:a_lib",
    #     "//srcs/B:b_lib",
    # ]
)

ios_application(
    name = "private_deps_demo",
    app_icons = ["//:AppIcon.xcassets"],
    bundle_id = "com.example.privatedepsdemo",
    families = [
        "iphone",
        "ipad",
    ],
    infoplists = [":Info.plist"],
    launch_storyboard = "//:Launch.storyboard",
    minimum_os_version = "15.0",
    deps = [":Sources"],
)