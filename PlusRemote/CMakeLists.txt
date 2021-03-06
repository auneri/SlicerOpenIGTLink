#-----------------------------------------------------------------------------
set(MODULE_NAME PlusRemote)
string(TOUPPER ${MODULE_NAME} MODULE_NAME_UPPER)

#-----------------------------------------------------------------------------
set(MODULE_PYTHON_SCRIPTS
  ${MODULE_NAME}.py
  )

set(MODULE_PYTHON_RESOURCES
  Resources/Icons/${MODULE_NAME}.png
  Resources/Icons/icon_Record.png
  Resources/Icons/icon_Stop.png
  Resources/Icons/icon_Wait.png
  Resources/Icons/VisibleOff.png
  Resources/Icons/VisibleOn.png
  )

add_subdirectory(MRML)
add_subdirectory(Widgets)

#-----------------------------------------------------------------------------
slicerMacroBuildScriptedModule(
  NAME ${MODULE_NAME}
  SCRIPTS ${MODULE_PYTHON_SCRIPTS}
  RESOURCES ${MODULE_PYTHON_RESOURCES}
  # WITH_GENERIC_TESTS # TODO: enable this when module directories are properly added in the slicerMacroBuildScriptedModule macro
  )

#-----------------------------------------------------------------------------
if(BUILD_TESTING)

  # Register the unittest subclass in the main script as a ctest.
  # Note that the test will also be available at runtime.
  #slicer_add_python_unittest(SCRIPT ${MODULE_NAME}ModuleTest.py)

  # Additional build-time testing
  add_subdirectory(Testing)
endif()
