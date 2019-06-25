CXXFLAGS = -std=c++11 -O3 -g -Wall -fmessage-length=0

# edit /usr/local/lib/pkgconfig/opencv.pc to get this right.
OPENCV_FLAGS = `pkg-config --cflags opencv`
OPENCV_LIBS = `pkg-config --libs opencv`
#LIBS = -I/usr/local/lib/opencv3.1.0/include/opencv -I/usr/local/lib/opencv3.1.0/include -L/usr/local/lib/opencv3.1.0/lib -lopencv_cudabgsegm -lopencv_cudaobjdetect -lopencv_cudastereo -lopencv_shape -lopencv_stitching -lopencv_cudafeatures2d -lopencv_superres -lopencv_cudacodec -lopencv_videostab -lopencv_cudaoptflow -lopencv_cudalegacy -lopencv_calib3d -lopencv_features2d -lopencv_objdetect -lopencv_highgui -lopencv_videoio -lopencv_photo -lopencv_imgcodecs -lopencv_cudawarping -lopencv_cudaimgproc -lopencv_cudafilters -lopencv_video -lopencv_ml -lopencv_imgproc -lopencv_flann -lopencv_cudaarithm -lopencv_core -lopencv_cudev -lopencv_highgui -lstdc++

# if it complained cannot find -lippicv, try to use this static lib.
OPENCV_FLAGS += -L/usr/local/share/OpenCV/3rdparty/lib


OBJS = main.o

SHOT_DETECTOR = shot_detector

all: $(SHOT_DETECTOR)

main.o: main.cc
	$(CXX) $(CXXFLAGS) $(OPENCV_FLAGS) -c main.cc \
	-o main.o

$(SHOT_DETECTOR): $(OBJS)
	echo $(OPENCV_LIBS)
	$(CXX) $(CXXFLAGS) $(OPENCV_FLAGS) $(OBJS) \
	-o $(SHOT_DETECTOR) $(OPENCV_LIBS)

clean:
	rm -f $(SHOT_DETECTOR) main.o
