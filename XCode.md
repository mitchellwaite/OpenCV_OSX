# OpenCV and XCode

I've copied most of this content from https://blogs.wcode.org/2014/11/howto-setup-xcode-6-1-to-work-with-opencv-libraries/. There are pictures there, but some of the content is out of date. I've updated it accordingly.

You will need to have completed the installation instructions for the Release version of OpenCV, and have installed XCode from the app store.

## Release only version of OpenCV

1. Open XCode
2. Create New Project
3. Under `macOS` `Application` > Choose `Command Line Tool`
4. Give your application a name, select C++ under Language, then Save
5. Click the XCode project file in your inspector (which is the blue icon in the furthest left hand tab). You should now have tabs in the centre window, one of them is `Build Settings`
6. Click `Build Settings`
7. Click `All` then click `Combined`
8. Scroll down until you find `Search Paths`
9. Double Click the `Header Search Paths` option, then Click the plus icon
10. Type in the following `/usr/local/include`
11. Scroll until you find `Linking`
12. Double Click `Other Linker Flags` and Click the plus icon
13. Copy and Paste the following, then press enter. You can determine what this value should be by running `pkg-config --libs opencv`.

`-lopencv_stitching -lopencv_superres -lopencv_videostab -lopencv_aruco -lopencv_bgsegm -lopencv_bioinspired -lopencv_ccalib -lopencv_dpm -lopencv_face -lopencv_photo -lopencv_fuzzy -lopencv_img_hash -lopencv_line_descriptor -lopencv_optflow -lopencv_reg -lopencv_rgbd -lopencv_saliency -lopencv_stereo -lopencv_structured_light -lopencv_phase_unwrapping -lopencv_surface_matching -lopencv_tracking -lopencv_datasets -lopencv_text -lopencv_dnn -lopencv_plot -lopencv_xfeatures2d -lopencv_shape -lopencv_video -lopencv_ml -lopencv_ximgproc -lopencv_calib3d -lopencv_features2d -lopencv_highgui -lopencv_videoio -lopencv_flann -lopencv_xobjdetect -lopencv_imgcodecs -lopencv_objdetect -lopencv_xphoto -lopencv_imgproc -lopencv_core`

14. Scroll back to `Search Paths`
15. Double Click the `Library Search Paths` option, then Click the plus icon
16. Type in the following `/usr/local/lib`

## Debug only version of OpenCV

You must follow the similar instructions for the release only version.

1. In step 16, replace `/usr/local/lib` with the location of the OpenCV debug libraries.

## Both debug and release versions of OpenCV

You must follow the similar instructions for the release only version.

1. In step 16, instead of double clicking on `Library Search Paths`, hover your cursor over it and click on the arrow.
2. Double Click the `Release` option, then Click the plus icon
3. Type in the following `/usr/local/lib`
4. Double Click the `Debug` option, then Click the plus icon
5. Type in the location of the OpenCV debug libraries

# Setting the Build Path (Optional)

XCode automatically stores the executable file in a derived data folder, we want to change it so that the executable is stored in your project directory.

1. Open XCode Preferences
2. Select Locations Tab
3. Click Advanced
4. Change the Location Button from Unique to Legacy

# Copying files to the output directory automatically (Optional)

Full disclosure, I don't know if this is necessarily the correct way to do this. You can always build the project, then manually copy data files to the output directory before starting the debugger. This just makes it easier so you don't need to manually copy things.

1. Add any files you wish to include to the XCode project, by dragging them to the folder in the sidebar containing your main.cpp
2. On the window that appears, ensure `Copy items if needed` is checked
3. Press `Finish`
4. Click the XCode project file in your inspector (which is the blue icon in the furthest left hand tab). You should now have tabs in the centre window, one of them is `Build Phases`
5. Click `Build Phases`
6. Scroll down to `Copy Files`, and click the arrow to its left
7. Under `Destination`, select `Products Directory`
8. For `Subpath`, you can enter a name of a directory you wish to contain your files. This directory will be placed in the same directory as the executable. Optionally, you may blank this out to have images reside in the same directory as the executable.
9. Ensure `Copy only when installing` is *not* checked.
10. Click the plus, and select any items you want to include. Select multiple items with the `Command` or `Windows` key.
11. Click the `Add` Button
