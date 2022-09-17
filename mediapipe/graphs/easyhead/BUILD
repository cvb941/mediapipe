load(
    "//mediapipe/framework/tool:mediapipe_graph.bzl",
    "mediapipe_binary_graph",
)

licenses(["notice"])

package(default_visibility = ["//visibility:public"])

cc_library(
    name = "easyhead_calculators",
    deps = [
        "//mediapipe/graphs/face_mesh:mobile_calculators",
        "//mediapipe/modules/face_geometry:geometry_pipeline_calculator",
        "//mediapipe/modules/face_geometry:face_geometry_from_landmarks",
    ],
)

mediapipe_binary_graph(
    name = "face_mesh_with_geometry_binary_graph",
    graph = "face_mesh_with_geometry.pbtxt",
    output_name = "face_mesh_with_geometry.binarypb",
    deps = [":easyhead_calculators"],
)
