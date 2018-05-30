include_directories(${BOOST_INCLUDE_DIR})
include_directories(${TBB_ROOT_DIR}/include)

SET(SOURCE
    src/ImageCapture.cpp
	src/RecorderCSV.cpp
    src/RecorderHOG.cpp
	src/RecorderOpenFace.cpp
    src/RecorderOpenFaceParameters.cpp
	src/SequenceCapture.cpp
	src/VisualizationUtils.cpp
	src/Visualizer.cpp
)

SET(HEADERS
    include/ImageCapture.h
    include/RecorderCSV.h
	include/RecorderHOG.h
    include/RecorderOpenFace.h
	include/RecorderOpenFaceParameters.h
	include/SequenceCapture.h
	include/VisualizationUtils.h
	include/Visualizer.h
)

include_directories(./include)
include_directories(${UTILITIES_SOURCE_DIR}/include)

add_library( Utilities ${SOURCE} ${HEADERS})
target_link_libraries( Utilities ${OpenCV_LIBS} Threads::Threads Boost::system Boost::filesystem dlib::dlib )

install (TARGETS Utilities DESTINATION lib)
install (FILES ${HEADERS} DESTINATION include/OpenFace/Utilities)
