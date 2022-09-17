Script to build easyhead aar
```bash
bash ./setup_android_sdk_and_ndk.sh
bazel build -c opt --strip=ALWAYS \
--host_crosstool_top=@bazel_tools//tools/cpp:toolchain \
--fat_apk_cpu=arm64-v8a,armeabi-v7a \
--legacy_whole_archive=0 \
--features=-legacy_whole_archive \
--copt=-fvisibility=hidden \
--copt=-ffunction-sections \
--copt=-fdata-sections \
--copt=-fstack-protector \
--copt=-Oz \
--copt=-fomit-frame-pointer \
--copt=-DABSL_MIN_LOG_LEVEL=2 \
--linkopt=-Wl,--gc-sections,--strip-all \
//mediapipe/examples/android/src/java/com/google/mediapipe/apps/aar_example:mediapipe_easyhead
```

Build face_mesh_with_geometry.binarypb graph
```bash
bazel build -c opt mediapipe/graphs/easyhead:face_mesh_with_geometry_binary_graph
```

Kopirovanie suborov
```bash
docker cp mediapipe:/mediapipe/bazel-bin/mediapipe/examples/android/src/java/com/google/mediapipe/apps/aar_example/mediapipe_easyhead.aar ./mediapipe/graphs/easyhead
docker cp mediapipe:/mediapipe/bazel-bin/mediapipe/graphs/easyhead/face_mesh_with_geometry.binarypb ./mediapipe/graphs/easyhead 
```
