# Platform-based flags are cached incorrectly

To reproduce the bug:

1.  Run `bazelisk build --platforms=//:platform :hello`. This will fail: so far
    so good!
1.  Comment out line 9 in `BUILD.bazel`, and try building again. This will
    succeed: also good!
1.  Now uncomment the line and build again. This should fail, since we're back
    to the state from point 1., but instead there's a cache hit and no rebuild!
    D:
