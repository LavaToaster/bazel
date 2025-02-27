load("@rules_java//java:defs.bzl", "java_import", "java_library", "java_plugin")
load("@rules_license//rules:license.bzl", "license")
load("//tools/distributions:distribution_rules.bzl", "distrib_jar_filegroup", "distrib_java_import")

package(default_visibility = ["//visibility:public"])

filegroup(
    name = "srcs",
    srcs = glob(["**"]) + [
        "//third_party/allocation_instrumenter:srcs",
        "//third_party/android_dex:srcs",
        "//third_party/animal_sniffer:srcs",
        "//third_party/antlr:srcs",
        "//third_party/bazel-toolchains:srcs",
        "//third_party/checker_framework_dataflow:srcs",
        "//third_party/checker_framework_javacutil:srcs",
        "//third_party/css/bootstrap:srcs",
        "//third_party/css/font_awesome:srcs",
        "//third_party/def_parser:srcs",
        "//third_party/grpc:srcs",
        "//third_party/cncf_udpa:srcs",
        "//third_party/protoc_gen_validate:srcs",
        "//third_party/grpc-java:srcs",
        "//third_party/ijar:srcs",
        "//third_party/jarjar:srcs",
        "//third_party/java/android_databinding:srcs",
        "//third_party/java/aosp_gradle_core:srcs",
        "//third_party/java/j2objc-annotations:srcs",
        "//third_party/java/j2objc:srcs",
        "//third_party/java/jacoco:srcs",
        "//third_party/java/javapoet:srcs",
        "//third_party/java/jcommander:srcs",
        "//third_party/java/proguard:srcs",
        "//third_party/javascript/bootstrap:srcs",
        "//third_party/jaxb:srcs",
        "//third_party/jetbrains_annotations:srcs",
        "//third_party/jetifier:srcs",
        "//third_party/juniversalchardet:srcs",
        "//third_party/kotlin_stdlib:srcs",
        "//third_party/pprof:srcs",
        "//third_party/protobuf:srcs",
        "//third_party/py/abseil:srcs",
        "//third_party/py/concurrent:srcs",
        "//third_party/py/dataclasses:srcs",
        "//third_party/py/frozendict:srcs",
        "//third_party/py/mock:srcs",
        "//third_party/py/six:srcs",
        "//third_party/rules_python:srcs",
        "//third_party/zlib:srcs",
        "//third_party/upb:srcs",
        "@googleapis//:srcs",
        "@remoteapis//:srcs",
    ],
)

# Filegroup to ship the sources to the Bazel embededded tools
# This filegroup should contains all GPL with classpath exception
# and LGPL code that we use in Bazel.
filegroup(
    name = "gpl-srcs",
    srcs = [],
)

# This target only contains the jars that are used for building / running Bazel.
# The target below is for the Android tools that are not shipped with Bazel.
distrib_java_import(
    name = "android_common_25_0_0_lite",
    enable_distributions = ["debian"],
    jars = [
        "android_common/com.android.tools.layoutlib_layoutlib_26.1.2-stripped.jar",
        "android_common/com.android.tools_sdk-common_25.0.0-patched-stripped.jar",
        "android_common/com.android.tools_repository_25.0.0.jar",
    ],
    deps = [
        "//third_party/jaxb",
    ],
)

java_library(
    name = "android-annotations",
    exports = ["@maven_android//:com_android_tools_annotations"],
)

java_import(
    name = "android_common_25_0_0",
    jars = [
        "android_common/com.android_annotations_25.0.0.jar",
        "android_common/com.android.tools.build_builder_2.0.0.jar",
        "android_common/com.android.tools.build_builder-model_2.0.0.jar",
        "android_common/com.android.tools.build_builder-test-api_2.0.0.jar",
        "android_common/com.android.tools.build_manifest-merger_25.0.0-patched.jar",
        "android_common/com.android.tools.external.lombok_lombok-ast_0.2.3.jar",
        # layoutlib has been upgraded to 26.1.2 *just* for font resource support.
        # We are unable to upgrade the other libraries yet due to internal
        # constraints with Blaze. See
        # https://github.com/bazelbuild/bazel/issues/4381
        # TODO(bazel-team): Upgrade entire android_common suite to 26+ after
        # resolving internal constraint.
        "android_common/com.android.tools.layoutlib_layoutlib_26.1.2.jar",
        "android_common/com.android.tools.lint_lint-api_25.0.0.jar",
        "android_common/com.android.tools.lint_lint-checks_25.0.0.jar",
        "android_common/com.android.tools_common_25.0.0.jar",
        "android_common/com.android.tools_dvlib_25.0.0.jar",
        "android_common/com.android.tools_repository_25.0.0.jar",
        "android_common/com.android.tools_sdk-common_25.0.0-patched.jar",
        "android_common/com.android.tools_sdklib_25.0.0.jar",
    ],
    runtime_deps = [
        ":asm",
        ":asm-analysis",
        ":asm-tree",
    ],
    deps = [
        "//third_party/jaxb",
    ],
)

java_import(
    name = "apache_commons_codec",
    jars = ["apache_commons_codec/commons-codec-1.10.jar"],
)

java_library(
    name = "apache_commons_collections",
    exports = ["@maven//:commons_collections_commons_collections"],
)

java_import(
    name = "apache_commons_io",
    jars = ["apache_commons_io/commons-io-2.4.jar"],
)

java_library(
    name = "apache_commons_lang",
    exports = ["@maven//:commons_lang_commons_lang"],
)

java_library(
    name = "apache_commons_compress",
    exports = ["@maven//:org_apache_commons_commons_compress"],
)

java_library(
    name = "apache_commons_pool2",
    exports = ["@maven//:org_apache_commons_commons_pool2"],
)

java_library(
    name = "apache_velocity",
    exports = ["@maven//:org_apache_velocity_velocity"],
)

java_library(
    name = "api_client",
    exports = [
        "@maven//:com_google_api_client_google_api_client",
        "@maven//:com_google_api_client_google_api_client_gson",
        "@maven//:com_google_http_client_google_http_client",
        "@maven//:com_google_http_client_google_http_client_gson",
    ],
    runtime_deps = [
        ":gson",
    ],
)

distrib_java_import(
    name = "asm",
    enable_distributions = ["debian"],
    jars = ["asm/asm-9.2.jar"],
    srcjar = "asm/asm-9.2-sources.jar",
)

java_import(
    name = "asm-analysis",
    jars = ["asm/asm-analysis-9.2.jar"],
    srcjar = "asm/asm-analysis-9.2-sources.jar",
    runtime_deps = [":asm-tree"],
)

java_import(
    name = "asm-commons",
    jars = ["asm/asm-commons-9.2.jar"],
    srcjar = "asm/asm-commons-9.2-sources.jar",
    runtime_deps = [":asm-tree"],
)

java_import(
    name = "asm-tree",
    jars = ["asm/asm-tree-9.2.jar"],
    srcjar = "asm/asm-tree-9.2-sources.jar",
    runtime_deps = [":asm"],
)

java_import(
    name = "asm-util",
    jars = ["asm/asm-util-9.2.jar"],
    srcjar = "asm/asm-util-9.2-sources.jar",
    runtime_deps = [":asm-tree"],
)

java_library(
    name = "auth",
    exports = [
        "@maven//:com_google_auth_google_auth_library_oauth2_http",
        "@maven//:com_google_auth_google_auth_library_credentials",
    ],
    runtime_deps = [
        ":api_client",
        ":guava",
    ],
)

java_plugin(
    name = "auto_annotation_plugin",
    processor_class = "com.google.auto.value.processor.AutoAnnotationProcessor",
    deps = [
        ":apache_commons_collections",
        ":apache_velocity",
        ":auto_common",
        ":auto_service_lib",
        ":auto_value_value",
        ":guava",
        ":jsr305",
        ":tomcat_annotations_api",
    ],
)

java_library(
    name = "auto_common",
    applicable_licenses = [":auto_license"],
    exports = ["@maven//:com_google_auto_auto_common"],
)

license(
    name = "auto_license",
    package_name = "auto-common/1.8.2",
    license_kinds = [
        "@rules_license//licenses/spdx:Apache-2.0",
    ],
    license_text = "auto/LICENSE",
)

java_library(
    name = "auto_service",
    exported_plugins = [
        ":auto_service_plugin",
    ],
    exports = [
        ":auto_service_lib",
    ],
)

java_plugin(
    name = "auto_service_plugin",
    processor_class = "com.google.auto.service.processor.AutoServiceProcessor",
    deps = [
        ":auto_common",
        ":auto_service_lib",
        ":guava",
    ],
)

java_library(
    name = "auto_service_lib",
    exports = [
        "@maven//:com_google_auto_service_auto_service",
        "@maven//:com_google_auto_service_auto_service_annotations",
    ],
)

java_plugin(
    name = "auto_value_plugin",
    processor_class = "com.google.auto.value.processor.AutoValueProcessor",
    deps = [
        ":apache_commons_collections",
        ":apache_velocity",
        ":auto_common",
        ":auto_service_lib",
        ":auto_value_value",
        ":guava",
        ":tomcat_annotations_api",
    ],
)

java_plugin(
    name = "auto_oneof_plugin",
    processor_class = "com.google.auto.value.processor.AutoOneOfProcessor",
    deps = [
        ":apache_commons_collections",
        ":apache_velocity",
        ":auto_common",
        ":auto_service_lib",
        ":auto_value_value",
        ":guava",
        ":tomcat_annotations_api",
    ],
)

java_plugin(
    name = "auto_value_gson_plugin",
    processor_class = "com.ryanharter.auto.value.gson.factory.AutoValueGsonAdapterFactoryProcessor",
    deps = [
        "@maven//:com_ryanharter_auto_value_auto_value_gson_extension",
        "@maven//:com_ryanharter_auto_value_auto_value_gson_factory",
    ],
)

java_library(
    name = "auto_value",
    exported_plugins = [
        ":auto_annotation_plugin",
        ":auto_oneof_plugin",
        ":auto_value_plugin",
        ":auto_value_gson_plugin",
    ],
    exports = [
        ":auto_value_value",
        ":tomcat_annotations_api",
        "@maven//:com_ryanharter_auto_value_auto_value_gson_runtime",
    ],
)

java_library(
    name = "auto_value_value",
    exports = [
        "@maven//:com_google_auto_value_auto_value",
        "@maven//:com_google_auto_value_auto_value_annotations",
    ],
)

# For bootstrapping JavaBuilder
distrib_jar_filegroup(
    name = "auto_value-jars",
    srcs = [
        "@maven//:com_google_auto_value_auto_value_file",
        "@maven//:com_google_auto_value_auto_value_annotations_file",
    ],
    enable_distributions = ["debian"],
)

java_library(
    name = "byte_buddy",
    exports = [
        "@maven//:net_bytebuddy_byte_buddy",
        "@maven//:net_bytebuddy_byte_buddy_agent",
    ],
)

java_library(
    name = "checker_framework_annotations",
    exports = ["@maven//:org_checkerframework_checker_qual"],
)

java_import(
    name = "compile_testing",
    jars = ["compile_testing/compile-testing-0.18.jar"],
)

java_library(
    name = "gson",
    exports = ["@maven//:com_google_code_gson_gson"],
)

java_library(
    name = "caffeine",
    exports = ["@maven//:com_github_ben_manes_caffeine_caffeine"],
)

java_library(
    name = "hungarian_algorithm",
    exports = ["@maven//:com_github_kevinstern_software_and_algorithms"],
)

java_library(
    name = "threeten",
    exports = [
        "@maven//:org_threeten_threeten_extra",
    ],
)

java_library(
    name = "error_prone_annotations",
    exports = [
        "@maven//:com_google_errorprone_error_prone_annotations",
        "@maven//:com_google_errorprone_error_prone_type_annotations",
    ],
)

distrib_jar_filegroup(
    name = "error_prone_annotations-jar",
    srcs = [
        "@maven//:com_google_errorprone_error_prone_annotations_file",
        "@maven//:org_threeten_threeten_extra_file",
    ],
    enable_distributions = ["debian"],
)

java_library(
    name = "error_prone",
    exports = [
        ":error_prone_annotations",
        "@maven//:com_google_errorprone_error_prone_check_api",
        "@maven//:com_google_errorprone_error_prone_core",
    ],
)

java_library(
    name = "jcip_annotations",
    exports = [
        "@maven//:com_github_stephenc_jcip_jcip_annotations",
    ],
)

# For bootstrapping JavaBuilder
distrib_jar_filegroup(
    name = "jcip_annotations-jars",
    srcs = [
        "@maven//:com_github_stephenc_jcip_jcip_annotations_file",
    ],
    enable_distributions = ["debian"],
)

java_library(
    name = "pcollections",
    exports = ["@maven//:org_pcollections_pcollections"],
)

# For bootstrapping JavaBuilder
filegroup(
    name = "bootstrap_guava_and_error_prone-jars",
    srcs = [
        ":error_prone_annotations-jar",
        ":guava-jars",
        ":jcip_annotations-jars",
        ":jsr305-jars",
    ],
)

java_library(
    name = "guava",
    applicable_licenses = [":guava_license"],
    exports = [
        ":error_prone_annotations",
        ":jcip_annotations",
        ":jsr305",
        "@maven//:com_google_guava_guava",
    ],
)

license(
    name = "guava_license",
    package_name = "guava/31.1",
    license_kinds = [
        "@rules_license//licenses/spdx:Apache-2.0",
    ],
    license_text = "guava/LICENSE",
)

java_library(
    name = "flogger",
    applicable_licenses = [":flogger_license"],
    exports = [
        "@maven//:com_google_flogger_flogger",
        "@maven//:com_google_flogger_flogger_system_backend",
        "@maven//:com_google_flogger_google_extensions",
    ],
)

license(
    name = "flogger_license",
    package_name = "flogger/0.5.1",
    license_kinds = [
        "@rules_license//licenses/spdx:Apache-2.0",
    ],
)

distrib_jar_filegroup(
    name = "flogger-jars",
    srcs = [
        "@maven//:com_google_flogger_flogger_file",
        "@maven//:com_google_flogger_flogger_system_backend_file",
        "@maven//:com_google_flogger_google_extensions_file",
    ],
    enable_distributions = ["debian"],
)

# For bootstrapping JavaBuilder
distrib_jar_filegroup(
    name = "guava-jars",
    srcs = ["@maven//:com_google_guava_guava_file"],
    enable_distributions = ["debian"],
)

# For desugaring the Guava jar.
distrib_jar_filegroup(
    name = "guava-failureaccess-jar",
    srcs = ["@maven//:com_google_guava_failureaccess_file"],
    enable_distributions = ["debian"],
)

java_library(
    name = "javax_activation",
    exports = ["@maven//:javax_activation_javax_activation_api"],
)

# javax.annotation.Generated is not included in the default root modules in 9,
# see: http://openjdk.java.net/jeps/320.
java_library(
    name = "javax_annotations",
    exports = ["@maven//:javax_annotation_javax_annotation_api"],
    neverlink = 1,  # @Generated is source-retention
)

java_library(
    name = "rxjava3",
    exports = ["@maven//:io_reactivex_rxjava3_rxjava"],
)

java_import(
    name = "jimfs",
    jars = ["jimfs/jimfs-1.1.jar"],
)

java_library(
    name = "jsr305",
    exports = ["@maven//:com_google_code_findbugs_jsr305"],
)

# For bootstrapping JavaBuilder
distrib_jar_filegroup(
    name = "jsr305-jars",
    srcs = ["@maven//:com_google_code_findbugs_jsr305_file"],
    enable_distributions = ["debian"],
)

java_import(
    name = "jsr330_inject",
    jars = ["jsr330_inject/javax.inject.jar"],
)

UNNECESSARY_DYNAMIC_LIBRARIES = select({
    "//src/conditions:windows": "*.so *.jnilib",
    "//src/conditions:darwin": "*.so *.dll",
    "//src/conditions:linux_x86_64": "*.jnilib *.dll",
    "//src/conditions:linux_s390x": "*.jnilib *.dll",
    # The .so file is an x86/s390x one, so we can just remove it if the CPU is not x86/s390x
    "//src/conditions:arm": "*.so *.jnilib *.dll",
    "//src/conditions:linux_aarch64": "*.so *.jnilib *.dll",
    "//src/conditions:linux_ppc": "*.so *.jnilib *.dll",
    "//src/conditions:freebsd": "*.so *.jnilib *.dll",
    "//src/conditions:openbsd": "*.so *.jnilib *.dll",
    # Default is to play it safe -- better have a big binary than a slow binary
    #   The empty string means nothing is to be removed from the library;
    #   the rule command tests for the empty string explictly to avoid
    #   zip erroring when it finds nothing to remove.
    "//conditions:default": "",
})

# Remove native libraries that are for a platform different from the one we are
# building Bazel for.
genrule(
    name = "filter_netty_dynamic_libs",
    srcs = select({
        "//src/conditions:darwin_arm64": ["@maven//:io_netty_netty_tcnative_boringssl_static_osx_aarch_64_file"],
        "//src/conditions:darwin_x86_64": ["@maven//:io_netty_netty_tcnative_boringssl_static_osx_x86_64_file"],
        "//src/conditions:linux_aarch64": ["@maven//:io_netty_netty_tcnative_boringssl_static_linux_aarch_64_file"],
        "//src/conditions:linux_x86_64": ["@maven//:io_netty_netty_tcnative_boringssl_static_linux_x86_64_file"],
        "//src/conditions:windows": ["@maven//:io_netty_netty_tcnative_boringssl_static_windows_x86_64_file"],
        "//conditions:default": [],
    }),
    outs = ["netty_tcnative/netty-tcnative-filtered.jar"],
    cmd = "cp $< $@ && " +
          # Make sure we can write the output file, even if the input isn't writable.
          "chmod +w $@ && " +
          "zip -qd $@ */license/* " + UNNECESSARY_DYNAMIC_LIBRARIES,
)

distrib_java_import(
    name = "netty",
    enable_distributions = ["debian"],
    jars = [
       "@maven//:io_netty_netty_buffer_file",
       "@maven//:io_netty_netty_codec_file",
       "@maven//:io_netty_netty_codec_http2_file",
       "@maven//:io_netty_netty_codec_http_file",
       "@maven//:io_netty_netty_common_file",
       "@maven//:io_netty_netty_handler_file",
       "@maven//:io_netty_netty_handler_proxy_file",
       "@maven//:io_netty_netty_resolver_file",
       "@maven//:io_netty_netty_resolver_dns_file",
       "@maven//:io_netty_netty_transport_file",
       "@maven//:io_netty_netty_transport_classes_epoll_file",
       "@maven//:io_netty_netty_transport_classes_kqueue_file",
       "@maven//:io_netty_netty_transport_sctp_file",
    ] + select({
        "//src/conditions:darwin_arm64": ["@maven//:io_netty_netty_transport_native_unix_common_osx_aarch_64_file"],
        "//src/conditions:darwin_x86_64": ["@maven//:io_netty_netty_transport_native_unix_common_osx_x86_64_file"],
        "//src/conditions:linux_aarch64": ["@maven//:io_netty_netty_transport_native_unix_common_linux_aarch_64_file"],
        "//src/conditions:linux_x86_64": ["@maven//:io_netty_netty_transport_native_unix_common_linux_x86_64_file"],
        "//conditions:default": ["@maven//:io_netty_netty_transport_native_unix_common_file"],
    }) + select({
        "//src/conditions:darwin_arm64": ["@maven//:io_netty_netty_transport_native_kqueue_osx_aarch_64_file"],
        "//src/conditions:darwin_x86_64": ["@maven//:io_netty_netty_transport_native_kqueue_osx_x86_64_file"],
        "//conditions:default": [],
    }) + select({
        "//src/conditions:linux_aarch64": ["@maven//:io_netty_netty_transport_native_epoll_linux_aarch_64_file"],
        "//src/conditions:linux_x86_64": ["@maven//:io_netty_netty_transport_native_epoll_linux_x86_64_file"],
        "//conditions:default": [],
    }),
)

distrib_java_import(
    name = "netty_tcnative",
    enable_distributions = ["debian"],
    jars = [
        "@maven//:io_netty_netty_tcnative_classes_file",
    ] + select({
        "//src/conditions:darwin_arm64": [":netty_tcnative/netty-tcnative-filtered.jar"],
        "//src/conditions:darwin_x86_64": [":netty_tcnative/netty-tcnative-filtered.jar"],
        "//src/conditions:linux_aarch64": [":netty_tcnative/netty-tcnative-filtered.jar"],
        "//src/conditions:linux_x86_64": [":netty_tcnative/netty-tcnative-filtered.jar"],
        "//src/conditions:windows": [":netty_tcnative/netty-tcnative-filtered.jar"],
        "//conditions:default": [],
    }),
)

java_library(
    name = "tomcat_annotations_api",
    exports = ["@maven//:org_apache_tomcat_tomcat_annotations_api"],
)

# For bootstrapping JavaBuilder
distrib_jar_filegroup(
    name = "tomcat_annotations_api-jars",
    srcs = ["@maven//:org_apache_tomcat_tomcat_annotations_api_file"],
    enable_distributions = ["debian"],
)

java_library(
    name = "java-diff-utils",
    exports = ["@maven//:io_github_java_diff_utils_java_diff_utils"],
)

# Testing

# TODO: Remove this target after migrating to java-diff-utils
java_import(
    name = "diffutils",
    jars = ["diffutils/diffutils-1.3.0.jar"],
)

java_library(
    name = "guava-testlib",
    exports = ["@maven//:com_google_guava_guava_testlib"],
    testonly = 1,
)

distrib_java_import(
    name = "junit4",
    enable_distributions = ["debian"],
    jars = [
        "hamcrest/hamcrest-core-1.3.jar",
        "junit/junit-4.13.2.jar",
    ],
)

java_import(
    name = "mockito",
    jars = ["mockito/mockito-core-3.12.4.jar"],
    deps = [
        ":byte_buddy",
        ":objenesis",
    ],
)

java_import(
    name = "objenesis",
    jars = ["objenesis/objenesis-1_3.jar"],
)

filegroup(
    name = "turbine_direct",
    srcs = ["turbine/turbine_direct.jar"],
)

java_import(
    name = "turbine",
    jars = ["turbine/turbine_direct.jar"],
)

java_import(
    name = "truth",
    applicable_licenses = [":truth_license"],
    jars = ["truth/truth-1.0.1.jar"],
    exports = [
        ":truth8",
        ":truth_proto",
    ],
    deps = [
        ":diffutils",
    ],
)

license(
    name = "truth_license",
    package_name = "truth/1.0.1",
    license_kinds = [
        "@rules_license//licenses/spdx:Apache-2.0",
    ],
    license_text = "truth/LICENSE",
)

java_import(
    name = "truth8",
    applicable_licenses = [":truth8_license"],
    jars = ["truth8/truth-java8-extension-1.0.1.jar"],
)

license(
    name = "truth8_license",
    package_name = "truth8/1.0.1",
    license_kinds = [
        "@rules_license//licenses/spdx:Apache-2.0",
    ],
    license_text = "truth8/LICENSE",
)

java_import(
    name = "truth_proto",
    applicable_licenses = [":truth_proto_license"],
    jars = [
        "truth_proto/truth-liteproto-extension-1.0.1.jar",
        "truth_proto/truth-proto-extension-1.0.1.jar",
    ],
)

license(
    name = "truth_proto_license",
    package_name = "truth_proto/1.0.1",
    license_kinds = [
        "@rules_license//licenses/spdx:Apache-2.0",
    ],
    license_text = "truth_proto/LICENSE",
)

java_library(
    name = "xz",
    applicable_licenses = [":xz_license"],
    exports = ["@maven//:org_tukaani_xz"],
)

license(
    name = "xz_license",
    package_name = "xz/1.9",
    license_kinds = [
        "@rules_license//licenses/generic:permissive",
    ],
    license_text = "xz/LICENSE",
)

# To be used by the skylark example.
filegroup(
    name = "junit4-jars",
    srcs = [
        "hamcrest/hamcrest-core-1.3.jar",
        "junit/junit-4.13.2.jar",
    ],
)

load(":compiler_config_setting.bzl", "create_compiler_config_setting")

create_compiler_config_setting(
    name = "windows_mingw",
    value = "windows_mingw",
)

create_compiler_config_setting(
    name = "windows_msys64",
    value = "windows_msys64",
)

create_compiler_config_setting(
    name = "windows_msys64_mingw64",
    value = "windows_msys64_mingw64",
)

create_compiler_config_setting(
    name = "windows_clang",
    value = "windows_clang",
)

config_setting(
    name = "darwin",
    values = {"host_cpu": "darwin"},
)

config_setting(
    name = "k8",
    values = {"host_cpu": "k8"},
)

config_setting(
    name = "piii",
    values = {"host_cpu": "piii"},
)

config_setting(
    name = "arm",
    values = {"host_cpu": "arm"},
)

config_setting(
    name = "aarch64",
    values = {"host_cpu": "aarch64"},
)

config_setting(
    name = "freebsd",
    values = {"host_cpu": "freebsd"},
)

config_setting(
    name = "openbsd",
    values = {"host_cpu": "openbsd"},
)

config_setting(
    name = "s390x",
    values = {"host_cpu": "s390x"},
)

config_setting(
    name = "ppc",
    values = {"host_cpu": "ppc"},
)

test_suite(
    name = "all_windows_tests",
    tests = [
        "//third_party/def_parser:windows_tests",
    ],
    visibility = ["//src:__pkg__"],
)
