set(MOVEMENTDETECTOR_SOURCES
  movementdetector.c
  kmsmovementdetector.c kmsmovementdetector.h
)

add_library(movementdetector MODULE ${MOVEMENTDETECTOR_SOURCES})

target_link_libraries(movementdetector
  ${gstreamer-1.0_LIBRARIES}
  ${gstreamer-video-1.0_LIBRARIES}
  ${opencv_LIBRARIES}
)

set_property(TARGET movementdetector
  PROPERTY INCLUDE_DIRECTORIES
    ${CMAKE_CURRENT_BINARY_DIR}/../../..
    ${gstreamer-1.0_INCLUDE_DIRS}
    ${opencv_INCLUDE_DIRS}
)

install(
  TARGETS movementdetector
  RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
  LIBRARY DESTINATION ${CMAKE_INSTALL_GST_PLUGINS_DIR}
  ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
)
