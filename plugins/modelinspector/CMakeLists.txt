# probe part
set(gammaray_models_srcs
  modelinspector.cpp
  modelinspectorinterface.cpp
  modeltester.cpp
  modelmodel.cpp
  modelcellmodel.cpp
  modelcontentproxymodel.cpp
  selectionmodelmodel.cpp
)
qt4_wrap_cpp(gammaray_models_srcs ${CMAKE_SOURCE_DIR}/3rdparty/qt/modeltest.h)

gammaray_add_plugin(gammaray_modelinspector
  DESKTOP gammaray_modelinspector.desktop
  JSON gammaray_modelinspector.json
  SOURCES ${gammaray_models_srcs}
)

target_link_libraries(gammaray_modelinspector
  ${QT_QTCORE_LIBRARIES}
  gammaray_core
  gammaray_kitemmodels
)

# ui part
if(GAMMARAY_BUILD_UI)

  set(gammaray_models_ui_srcs
    modelinspectorwidget.cpp
    modelinspectorinterface.cpp
    modelinspectorclient.cpp
    modelcontentdelegate.cpp
  )

  qt4_wrap_ui(gammaray_models_ui_srcs
    modelinspectorwidget.ui
  )

  gammaray_add_plugin(gammaray_modelinspector_ui
    DESKTOP gammaray_modelinspector_ui.desktop
    JSON gammaray_modelinspector.json
    SOURCES ${gammaray_models_ui_srcs}
  )

  target_link_libraries(gammaray_modelinspector_ui
    ${QT_QTCORE_LIBRARIES}
    ${QT_QTGUI_LIBRARIES}
    gammaray_ui
  )

endif()
