# gst-opengl-snap

This example shows how GStreamer 1.16.2 with `gstgtkgl` fails on some devices **only** in snap environment.
To build the following code you need to do the following:
1. Clone repo
2. `snapcraft` from the root project folder. Note: better to use at least snapcraft v4
3. `sudo snap install --dangerous gst-test_1.0_amd64.snap`
4. Run `gst-test videotestsrc ! glupload ! glfiltercube ! gtkglsink` to test if it's reproducible on your device. If it fails you should get the similar output:
```
Setting pipeline to PAUSED ...
ERROR: Pipeline doesn't want to pause.
ERROR: from element /GstPipeline:pipeline0/GstGtkGLSink:gtkglsink0: Failed to initialize OpenGL with Gtk
Additional debug info:
gstgtkglsink.c(187): gst_gtk_gl_sink_start (): /GstPipeline:pipeline0/GstGtkGLSink:gtkglsink0
Setting pipeline to NULL ...
Freeing pipeline ...
```
