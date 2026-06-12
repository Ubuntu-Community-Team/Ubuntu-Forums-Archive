---
title: "FLTK on AMD64 just won't compile !!!!"
date: 2009-07-03
forum: x86 64-bit Users
---

### Post by marcus_ on 2009-07-03
Hi there, 

I hope this is the right place to post this message. If it is not, please show me the right place. Anyway, I need some help. I am trying to compile a huge program for work, but i cannot get rid of the following errors:

```

./release/avicam.o: In function `sensors::env::cam::cl_AviCam::cl_AviCam(char const*)':
avicam.cpp:(.text+0x12b6): undefined reference to `cvCaptureFromFile'
./release/avicam.o: In function `sensors::env::cam::cl_AviCam::cl_AviCam(char const*)':
avicam.cpp:(.text+0x1c06): undefined reference to `cvCaptureFromFile'
./release/linux_dcam_realcam.o: In function `sensors::env::cam::cl_LinuxDCAMCam::buildFeatureMap(bool, bool)':
linux_dcam_realcam.cpp:(.text+0x138a): undefined reference to `sensors::env::cam::cl_LinuxDCAMCam::cl_LinuxDCAMWhiteBalanceFeature::cl_LinuxDCAMWhiteBalanceFeature(sensors::env::cam::cl_LinuxDCAMCam const*)'
./release/linux_dcam_realcam.o: In function `sensors::env::cam::cl_LinuxDCAMCam::cl_LinuxDCAMSTOCModeFeature::setValue(unsigned int)':
linux_dcam_realcam.cpp:(.text+0x1a80): undefined reference to `sensors::env::cam::cl_CameraBuffer::setDecodeMode(sensors::env::cam::cl_CameraBuffer::e_DecodeMode)'
linux_dcam_realcam.cpp:(.text+0x1b79): undefined reference to `sensors::env::cam::cl_CameraBuffer::setDecodeMode(sensors::env::cam::cl_CameraBuffer::e_DecodeMode)'
linux_dcam_realcam.cpp:(.text+0x1ca2): undefined reference to `sensors::env::cam::cl_CameraBuffer::setDecodeMode(sensors::env::cam::cl_CameraBuffer::e_DecodeMode)'
linux_dcam_realcam.cpp:(.text+0x1cb8): undefined reference to `sensors::env::cam::cl_CameraBuffer::setDecodeMode(sensors::env::cam::cl_CameraBuffer::e_DecodeMode)'
./release/linux_dcam_realcam.o: In function `sensors::env::cam::cl_LinuxDCAMCam::~cl_LinuxDCAMCam()':
linux_dcam_realcam.cpp:(.text+0x3296): undefined reference to `sensors::env::cam::cl_CameraBuffer::removeCamera() const'
./release/linux_dcam_realcam.o: In function `sensors::env::cam::cl_LinuxDCAMCam::~cl_LinuxDCAMCam()':
linux_dcam_realcam.cpp:(.text+0x36f6): undefined reference to `sensors::env::cam::cl_CameraBuffer::removeCamera() const'
./release/linux_dcam_realcam.o: In function `sensors::env::cam::cl_LinuxDCAMCam::~cl_LinuxDCAMCam()':
linux_dcam_realcam.cpp:(.text+0x3b46): undefined reference to `sensors::env::cam::cl_CameraBuffer::removeCamera() const'
./release/linux_dcam_realcam.o: In function `sensors::env::cam::cl_LinuxDCAMCam::update()':
linux_dcam_realcam.cpp:(.text+0x4376): undefined reference to `sensors::env::cam::cl_CameraBuffer::getImageChannel(int)'
linux_dcam_realcam.cpp:(.text+0x445d): undefined reference to `sensors::env::cam::cl_CameraBuffer::unlockDataArray(unsigned char*)'
linux_dcam_realcam.cpp:(.text+0x4515): undefined reference to `sensors::env::cam::cl_CameraBuffer::getNumFreeDataArrays() const'
linux_dcam_realcam.cpp:(.text+0x4526): undefined reference to `sensors::env::cam::cl_CameraBuffer::hasNoIncompleteChannelReading() const'
linux_dcam_realcam.cpp:(.text+0x45fe): undefined reference to `sensors::env::cam::cl_CameraBuffer::getBufferSize() const'
linux_dcam_realcam.cpp:(.text+0x460d): undefined reference to `sensors::env::cam::cl_CameraBuffer::removeCamera() const'
linux_dcam_realcam.cpp:(.text+0x4619): undefined reference to `sensors::env::cam::cl_CameraBuffer::getNumOfDataArrays() const'
linux_dcam_realcam.cpp:(.text+0x4639): undefined reference to `sensors::env::cam::cl_CameraBuffer::cl_CameraBuffer(int, int, sensors::env::cam::cl_CameraBuffer::e_DecodeMode)'
linux_dcam_realcam.cpp:(.text+0x469b): undefined reference to `sensors::env::cam::cl_CameraBuffer::getDmaChannel() const'
linux_dcam_realcam.cpp:(.text+0x47c3): undefined reference to `typeinfo for dip::cl_16BitImage'
linux_dcam_realcam.cpp:(.text+0x47ed): undefined reference to `sensors::env::cam::cl_CameraBuffer::getImageChannel(int)'
linux_dcam_realcam.cpp:(.text+0x48b3): undefined reference to `dip::cl_16BitImage::setToImageData(int, int, dip::i_ImageData*, dip::i_ImageData*, util::times::cl_AbsoluteTime const&, sensors::env::cam::cl_CameraData const*, sensors::cl_NavData const*, dip::cl_GeoData const*)'
linux_dcam_realcam.cpp:(.text+0x49e8): undefined reference to `dip::cl_CamBufImageData::cl_CamBufImageData(unsigned char*, sensors::env::cam::cl_CameraBuffer&)'
./release/linux_dcam_realcam.o: In function `sensors::env::cam::cl_LinuxDCAMCam::cl_LinuxDCAMCam(int, sensors::env::cam::cl_CameraBuffer*, bool)':
linux_dcam_realcam.cpp:(.text+0x731e): undefined reference to `sensors::env::cam::cl_CameraBuffer::cl_CameraBuffer(int, int, sensors::env::cam::cl_CameraBuffer::e_DecodeMode)'
linux_dcam_realcam.cpp:(.text+0x732d): undefined reference to `sensors::env::cam::cl_CameraBuffer::getDmaChannel() const'
linux_dcam_realcam.cpp:(.text+0x83dd): undefined reference to `dip::cl_16BitImage::cl_16BitImage()'
linux_dcam_realcam.cpp:(.text+0x83e9): undefined reference to `dip::cl_16BitImage::setCameraData(sensors::env::cam::cl_CameraData const*)'
./release/linux_dcam_realcam.o: In function `sensors::env::cam::cl_LinuxDCAMCam::cl_LinuxDCAMCam(int, sensors::env::cam::cl_CameraBuffer*, bool)':
linux_dcam_realcam.cpp:(.text+0xb82e): undefined reference to `sensors::env::cam::cl_CameraBuffer::cl_CameraBuffer(int, int, sensors::env::cam::cl_CameraBuffer::e_DecodeMode)'
linux_dcam_realcam.cpp:(.text+0xb83d): undefined reference to `sensors::env::cam::cl_CameraBuffer::getDmaChannel() const'
linux_dcam_realcam.cpp:(.text+0xc8e4): undefined reference to `dip::cl_16BitImage::cl_16BitImage()'
linux_dcam_realcam.cpp:(.text+0xc8f0): undefined reference to `dip::cl_16BitImage::setCameraData(sensors::env::cam::cl_CameraData const*)'
./ext_libs/fltk/lib/libfltk.a(fl_font.o): In function `fl_draw(char const*, int, int, int)':
fl_font.cxx:(.text+0xd4): undefined reference to `XftDrawCreate'
fl_font.cxx:(.text+0xe9): undefined reference to `XftDrawChange'
fl_font.cxx:(.text+0x115): undefined reference to `XftDrawSetClip'
fl_font.cxx:(.text+0x19e): undefined reference to `XftDrawStringUtf8'
./ext_libs/fltk/lib/libfltk.a(fl_font.o): In function `fl_text_extents(char const*, int, int&, int&, int&, int&)':
fl_font.cxx:(.text+0x43c): undefined reference to `XftTextExtentsUtf8'
./ext_libs/fltk/lib/libfltk.a(fl_font.o): In function `fl_width(char const*, int)':
fl_font.cxx:(.text+0x4f4): undefined reference to `XftTextExtentsUtf8'
./ext_libs/fltk/lib/libfltk.a(fl_font.o): In function `fl_width(unsigned int*, int)':
fl_font.cxx:(.text+0x576): undefined reference to `XftTextExtents32'
./ext_libs/fltk/lib/libfltk.a(fl_font.o): In function `fl_rtl_draw(char const*, int, int, int)':
fl_font.cxx:(.text+0x676): undefined reference to `XftDrawCreate'
fl_font.cxx:(.text+0x68b): undefined reference to `XftDrawChange'
fl_font.cxx:(.text+0x6c9): undefined reference to `XftDrawSetClip'
fl_font.cxx:(.text+0x760): undefined reference to `XftDrawString32'
./ext_libs/fltk/lib/libfltk.a(fl_font.o): In function `fontopen(char const*, bool, int)':
fl_font.cxx:(.text+0x9fc): undefined reference to `XftFontMatch'
fl_font.cxx:(.text+0xa0b): undefined reference to `XftFontOpenPattern'
fl_font.cxx:(.text+0xa3d): undefined reference to `XftFontOpenXlfd'
./ext_libs/fltk/lib/libfltk.a(fl_font.o): In function `fl_destroy_xft_draw(unsigned long)':
fl_font.cxx:(.text+0x85): undefined reference to `XftDrawChange'
collect2: ld returned 1 exit status
gmake[2]: *** [main] Error 1
gmake[2]: Leaving directory `/home/marcus/DIP'
gmake[1]: *** [.build-conf] Error 2
gmake[1]: Leaving directory `/home/marcus/DIP'
gmake: *** [.build-impl] Error 2
BUILD FAILED (exit value 2, total time: 2m 17s)

```my makefile reads:
```

CPP  = g++
WINDRES = windres
RES  = 
OBJDIR = ./release/
SRC = main math/geo2d/axisalignedrectangle math/math_vector math/math_svd math/math_operations math/math_matrix math/geo2d/vector2 math/geo2d/line2d math/geo3d/vector3 math/geo3d/quaternion math/geo3d/relativepositionestimator math/geo3d/onlinextrinsic math/kalman/kalman_interface math/kalman/kalman_ekf math/kalman/kalman_linear math/kalman/kalman_srukf math/kalman/kalman_ukf math/geo3d/matrix3x3 util/UpdateManager/updatemanager log/logmsgdistributer log/logmessage/txtmsg log/logmessage/boolmsg log/logmessage/cameradatamsg log/logmessage/vector2msg log/logmessage/unsignedintmsg log/logmessage/ucharmsg log/logmessage/pointvectormsg log/logmessage/sourceidmsg log/logmessage/relativetimemsg log/logmessage/vector3msg log/logmessage/multimsg log/logmessage/doublemsg log/logmessage/logmessage log/logmsggenerator/camextrinsiclogger log/logmsggenerator/posestilogger log/logmsgreceiver/logmsgreceiver log/logmsgreceiver/logmessagebox log/logmsgreceiver/simpletxtlogfile log/logmsgreceiver/logfile log/logmsgreceiver/tabletxtlogfile log/logmsgreceiver/stdoutputlog log/remotecontroller/fps_counter_rc log/remotecontroller/remotecontroller log/remotecontroller/realcam_rc log/remotedatareceiver/remotedatareceiver log/remotedatareceiver/fps_counter_rdr log/remotedatareceiver/realcam_rdr util/SingletonManager/SingletonManager util/time/time util/time/fps_counter util/time/slowdownprocess util/time/clock util/lettermap/lettermap util/pool/camerapool dip/filter/saveimagesequence dip/filter/filter dip/filter/canny dip/filter/colorfilter dip/filter/sobel dip/filter/wrapper dip/filter/2thresh dip/filter/bayer dip/filter/histogram dip/filter/copyimage dip/filter/compareimages dip/filter/thresh dip/filter/anaglyph dip/filter/mosaic dip/filter/hough dip/filter/filtermaster dip/filter/filterdebugshell dip/filter/chessboardcalibrate dip/filter/camextrinsic dip/filter/rectify dip/filter/orthorectify dip/filter/overlay dip/filter/thresh_background dip/filter/cam_calib dip/filter/manualfocusassistant dip/filter/meanluminance dip/filter/boxfilter dip/filter/timecodeimage dip/filter/timecodereader dip/filter/blobanal dip/blob/blob dip/blob/blobfilter/identifyer dip/blob/blobfilter/sizefilter dip/blob/blobfilter/localmovementfilter dip/blob/blobfilter/meanvaluefilter dip/blob/blobfilter/quadraticfilter dip/blob/blobfilter/positionfilter dip/blob/blobfilter/limitnumblobs dip/blob/collector/simpleblobcoll dip/blob/collector/binblobcoll dip/blob/similarityestimator/bypositionestimator dip/blob/similarityestimator/bysizeestimator dip/blob/similarityestimator/bysiderelestimator dip/blob/similarityestimator/byrelsizeestimator dip/mdp/trackedobject dip/mdp/editabletrackedobjectslist dip/mdp/trackedobjectslist dip/mdp/trackedobjectsfilter/trackedobjectsfiltermaster dip/mdp/trackedobjectsfilter/trackedobjectsfilterdebugshell  dip/mdp/trackedobjectsfilter/smoothlocalmoves dip/mdp/trackedobjectsfilter/limitnumtrackedobjects dip/mdp/trackedobjectslistobserver/positionestimator dip/mdp/trackedobjectslistobserver/trackedobjectslistobservergroup dip/mdp/trackedobjectslistobserver/trackedobjectslistobserver dip/mdp/trackedobjectslistobserver/object_loss_update_trigger dip/mdp/trackedobjectslistobserver/object_loss_triggered_image_sequence dip/mdp/movementestimator/eightpointestimator dip/mdp/movementestimator/kalman_vision_ekf dip/mdp/movementestimator/kalman_vision_only_ekf dip/mdp/movementestimator/kalman_vision_only_sub_filter dip/mdp/movementestimator/kalman_vision_only_ukf dip/mdp/movementestimator/kalman_vision_ukf dip/mdp/movementestimator/kalman_vision_sub_filter dip/mdp/movementestimator/kalmanmovementestimator dip/mdp/movementestimator/kalmanmovementestimator_vision_only dip/mdp/movementestimator/nonlinear_dynamic_system dip/mdp/movementestimator/optimizingmovementestimator dip/mdp/movementestimator/simplemovesestimator dip/mosaic/mosaicalgo dip/mosaic/feature dip/mosaic/navonly dip/mosaic/transformparam dip/mosaic/mosaicoutput_interface dip/mosaic/mosaicoutput dip/mosaic/mosaiccoloroutput dip/image/image dip/image/image_interface dip/image/geodata dip/image/depthimage dip/image/imagedata_interface dip/image/colorimagedata dip/image/colorimagedata_ipl dip/image/imagedata_array dip/image/imagedata_ipl dip/image/ipl_image dip/image/readonlyimage dip/image/readonlycolorimage dip/image/colorimage dip/image/colorimageconvertfunctions dip/image/colorimage_interface dip/image/wrapped/scaled_image dip/image/wrapped/cropped_image dip/image/wrapped/wrappedimage dip/image/wrapped/scaled_colorimage dip/image/wrapped/colorwrappedimage dip/image/wrapped/cropped_colorimage dip/image/wrapped/cleaned_image sensors/env/cam/cameradata sensors/env/cam/camera sensors/env/cam/avicam sensors/env/cam/bmpcam sensors/env/cam/simcam sensors/env/cam/realcam_interface sensors/env/cam/linux_dcam_realcam sensors/env/envsensorinfo sensors/navdata sensors/sensordata sensors/sensorsim sensors/navsim sensors/sensor_suite gui/gui_functions gui/fltk_updater/fltk_updater gui/window/monitorwindow gui/window/mainwindow gui/window/fullscreenwindow gui/window/caminfowindow gui/window/selectboxwin gui/window/cam_n_inifile_infowindow gui/window/logctrlwindow gui/window/udptargetpoolwindow gui/window/setcoordinateswindow gui/window/set2dvectorwindow gui/element/monitor gui/element/videobox gui/element/tab gui/element/tab_constants gui/element/interval_n_value_out gui/element/relativetimeinput gui/element/limited_slider gui/element/commanderdisplays/commanderdisplay gui/element/commanderdisplays/imagerecording_commanderdisplay gui/element/commanderdisplays/cameracalibration_commanderdisplay gui/element/commanderdisplays/doublerecording_commanderdisplay gui/element/commanderdisplays/experimental_commanderdisplay gui/element/commanderdisplays/doublestaticbackgroundtrackingcommanderdisplay gui/element/rdr_display/rdr_display gui/element/rdr_display/realcam_rdr_display gui/element/rdr_display/fps_counter_rdr_display gui/element/filtertabs/filtertab gui/element/filtertabs/filtermastertab gui/element/filtertabs/colorfiltertab gui/element/filtertabs/sobeltab gui/element/filtertabs/bayertab gui/element/filtertabs/2threshtab gui/element/filtertabs/cannytab gui/element/filtertabs/wrappertab gui/element/filtertabs/threshtab gui/element/filtertabs/compareimagestab gui/element/filtertabs/chessboardcalibratetab gui/element/filtertabs/cam_calibtab gui/element/filtertabs/camextrinsictab gui/element/filtertabs/meanluminancetab gui/element/filtertabs/rectifytab gui/element/filtertabs/blobanaltab gui/element/filtertabs/boxfiltertab gui/element/filtertabs/timecodeimagetab gui/element/filtertabs/timecodereadertab gui/element/filtertabs/anaglyphtab gui/element/filtertabs/houghtab gui/element/filtertabs/mosaictab gui/element/filtertabs/overlaytab gui/element/filtertabs/orthorectifytab gui/element/filtertabs/copyimagetab gui/element/filtertabs/histogramtab gui/element/filtertabs/thresh_backgroundtab gui/element/filtertabs/manualfocusassistantab gui/element/filtertabs/filtergroup gui/element/filtertabs/saveimagesequencetab gui/element/blobfiltertabs/blobfiltertab gui/element/blobfiltertabs/limitnumblobstab gui/element/blobfiltertabs/localmovementfiltertab gui/element/blobfiltertabs/meanvalfiltertab  gui/element/blobfiltertabs/positionfiltertab gui/element/blobfiltertabs/quadraticfiltertab gui/element/blobfiltertabs/sizefiltertab gui/element/blobfiltertabs/identifyertab gui/element/similarityestimatortabs/similarityestimatortab gui/element/similarityestimatortabs/bypositionestimatortab gui/element/similarityestimatortabs/bysizeestimatortab gui/element/similarityestimatortabs/bysiderelestimatortab gui/element/similarityestimatortabs/byrelsizeestimatortab gui/element/collectordisplays/simplecolldisp gui/element/trackedobjectslistobserverdisp/trackedobjectslistobservergroupdisplay gui/element/trackedobjectslistobserverdisp/trackedobjectslistobserverdisplay gui/element/trackedobjectslistobserverdisp/positionestimatordisplay gui/element/trackedobjectslistobserverdisp/objectlosstriggeredimagesequencedisplay gui/element/trackedobjectsfiltertabs/trackedobjectsfiltertab gui/element/trackedobjectsfiltertabs/trackedobjectsfiltergroup gui/element/trackedobjectsfiltertabs/smoothlocaltab gui/element/trackedobjectsfiltertabs/limitnumtrackedobjectstab gui/element/movementestimatordisplay/simplemovesestimatordisplay gui/element/movementestimatordisplay/optimizingmovementestimatordisplay gui/element/movementestimatordisplay/movementestimatordisplay gui/element/movementestimatordisplay/kalmanvisiononlymovementestimatordisplay gui/element/movementestimatordisplay/kalmanmovementestimatordisplay gui/element/movementestimatordisplay/eightpointestimatordisplay gui/element/mosaicalgotabs/mosaicalgotab gui/element/mosaicalgotabs/featuretab gui/element/mosaicalgotabs/navonlytab gui/element/wraptabs/cleanwraptab gui/element/wraptabs/cropwraptab gui/element/wraptabs/scalewraptab gui/element/wraptabs/wraptab gui/element/colorinterval_value_out gui/element/cam_ctrl/realcam_controller gui/element/cam_ctrl/cam_controller gui/element/cam_ctrl/cam_n_inifile_info gui/element/cam_ctrl/cam_info gui/element/cam_ctrl/cam_chooser gui/element/cam_ctrl/cam_ini_file_ctrl gui/element/cam_ctrl/cam_data_display gui/element/sensor_ctrl/sensor_info gui/element/sensor_ctrl/sensor_chooser gui/element/pool_displays/drawobjectpool_display gui/drobs/acczmovedisplay gui/drobs/pulsatingopencircle gui/drobs/anglefeature gui/drobs/draw2dvector gui/drobs/trackedobjectsdraw gui/drobs/draw_object gui/drobs/drawbox gui/drobs/mark_white_pixel gui/drobs/blobfeaturedraw gui/drobs/crosshair gui/drobs/drawlinevector gui/drobs/rackcalibdraw gui/drobs/drawvaluepoint coms/udp/udpmsgsender coms/udp/netfunction coms/doublestaticbackgroundtrackingcommander coms/doublerecordingcommander coms/cameracalibrationcommander coms/imagerecordingcommander coms/experimentalcommander coms/commander$(RES)
OBJ = $(SRC:%=$(OBJDIR)%.o)
LINKOBJ1  = $(notdir $(OBJ))
LINKOBJ  = $(LINKOBJ1:%=$(OBJDIR)%)
LIBS = -L./ext_libs/lib64 -lXft -lhighgui -lcv -lcxcore -L./ext_libs/fltk/lib -lfltk -lfltk_images -lfltk_forms -lfltk_gl
CXXINCS = -I ./ -I./ext_libs/1394 -I./ext_libs/opencv/cxcore/include -I./ext_libs/opencv/cv/include -I./ext_libs/opencv/otherlibs/highgui

BIN  = main
CXXFLAGS =  $(CXXINCS) $(fltk-config --cxxflags) -D SPICE -O2 -fno-strict-aliasing -Wall
    
.PHONY: all all-before all-after clean clean-custom

all: all-before main all-after

clean: clean-custom
    ${RM} $(LINKOBJ) $(BIN)

$(BIN): $(OBJ)
    $(CPP) $(LINKOBJ) -o "./executable/spice" $(LIBS)

$(OBJDIR)%.o:%.cpp
    $(CPP) -c $< -o $(OBJDIR)$(@F) $(CXXFLAGS)

$(OBJDIR)%.o:../%.cpp
    $(CPP) -c $< -o $(OBJDIR)$(@F) $(CXXFLAGS)

```I think this problem might be related to the 64-bit machine. Anyway, I tried loads of different libraries but it just won't compile. Seriously hoping for help. 

Cheers, Marcus

---

