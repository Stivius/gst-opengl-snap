# gst-opengl-snap

This example shows how GStreamer 1.16.2 with `gstgtkgl` fails on some devices **only** in snap environment.
To build the following code you need to do the following:
1. Clone repo
2. Install snapcraft `sudo snap install snapcraft --classic`. Note: better to use at least snapcraft v4
3. `snapcraft` in `core18` or `core20` folder
4. `sudo snap install --dangerous gst-test_1.0_amd64.snap`
5. Run `gst-test-coreCORE_VERSION videotestsrc ! glupload ! glfiltercube ! gtkglsink` to test if it's reproducible on your device where `CORE_VERSION` is `18` or `20` depending on your build. If it fails you should get the similar output:
```
Setting pipeline to PAUSED ...
libGL error: MESA-LOADER: failed to open iris (search paths /snap/gst-test-core20/x2/gnome-platform/usr/lib/x86_64-linux-gnu/dri)
libGL error: failed to load driver: iris
libGL error: MESA-LOADER: failed to open iris (search paths /snap/gst-test-core20/x2/gnome-platform/usr/lib/x86_64-linux-gnu/dri)
libGL error: failed to load driver: iris
libGL error: MESA-LOADER: failed to open swrast (search paths /snap/gst-test-core20/x2/gnome-platform/usr/lib/x86_64-linux-gnu/dri)
libGL error: failed to load driver: swrast
ERROR: Pipeline doesn't want to pause.
ERROR: from element /GstPipeline:pipeline0/GstGtkGLSink:gtkglsink0: Failed to initialize OpenGL with Gtk
Additional debug info:
gstgtkglsink.c(187): gst_gtk_gl_sink_start (): /GstPipeline:pipeline0/GstGtkGLSink:gtkglsink0
Setting pipeline to NULL ...
Freeing pipeline ...
```
