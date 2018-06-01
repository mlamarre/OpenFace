#TBB library
include_directories(${TBB_ROOT_DIR}/include)
include_directories(${BLAS_ROOT_DIR})

include_directories(${BOOST_INCLUDE_DIR})

#OpenBlas library
include_directories(../../3rdParty/OpenBLAS/include)

#Utilities library
include_directories(../../local/LandmarkDetector/include)
include_directories(../../local/Utilities/include)

SET(SOURCE
    src/GazeEstimation.cpp
)

SET(HEADERS
    include/GazeEstimation.h
)

include_directories(./include)
include_directories(${GAZEANALYSER_SOURCE_DIR}/include)

add_library( GazeAnalyser ${SOURCE} ${HEADERS})
target_link_libraries( GazeAnalyser ${OpenCV_LIBS} LandmarkDetector dlib::dlib )

install (FILES ${HEADERS} DESTINATION include/OpenFace/GazeAnalyser)
if (MSVC)
	install (TARGETS GazeAnalyser DESTINATION lib/$<CONFIG>)
else (MSVC)
	install (TARGETS GazeAnalyser DESTINATION lib)
endif (MSVC)

