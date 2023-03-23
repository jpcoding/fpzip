add_executable(fpzipcmd fpzip.cpp)
if(NOT MSVC)
  set_property(TARGET fpzipcmd PROPERTY OUTPUT_NAME fpzip)
endif()
target_link_libraries(fpzipcmd fpzip)
if(HAVE_LIBM_MATH)
  target_link_libraries(fpzipcmd m)
endif()

# Install the fpzipcmd target
install(TARGETS fpzipcmd
        RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})

# Set the rpath on non-Windows platforms
if(NOT MSVC)
  set_target_properties(fpzipcmd PROPERTIES INSTALL_RPATH "${CMAKE_INSTALL_FULL_LIBDIR}")
endif()