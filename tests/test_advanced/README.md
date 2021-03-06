# libretro_test_advanced
An advanced test core written in C for libretro.

This core has a group of tests which you can cycle between by pressing the
buttons on the gamepad.

Up and Down will cycle between the test groups. Left and Right will cycle
between the tests in each group.

1. Video output
   * 1a. Tearing test, horizontal: Vertical lines moving horizontally. In pixel format XRGB8888, the Xs will be 00.
   * 1b. Tearing test, vertical:   Horizontal lines moving vertically. In pixel format XRGB8888, the Xs will be FF.
   * 1c. vsync test:               Flickers between white and black each frame.
   * 1d. Stretching test:          A checkerboard of black and white, to test if each square looks smooth.
   * 1e. Border test:              A white screen, with red and yellow borders.
2. Latency and synchronization
   * 2a. A/V sync test. Will switch between white and silent, and black and noisy, every two seconds.
   * 2b. Latency test. If any of ABXYLRStSe are held, it's black and noisy; if not, it's white and silent.
3. Input
   * 3a. Press any key to check how fast input_state_cb can be called. The background color will vary between pixel formats.
4. Netplay
   * 4a. Input sync. All button presses are sent to the screen; a hash of that is used as background color, for easy comparison.

## Programming language
C

## Building
To compile, you will need a C compiler and associated toolchain installed.

	make

or

	gcc libretro-test.c -shared -fPIC -lm -o advanced_tests_libretro.so (for Windows, use .dll instead)
