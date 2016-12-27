if (ELECTROLINK)
  message (STATUS "INFO - Adding electrolink backend support")
  set (mraa_LIB_SRCS_NOAUTO ${mraa_LIB_SRCS_NOAUTO}
    ${PROJECT_SOURCE_DIR}/src/electrolink/electrolink.c
    ${PROJECT_SOURCE_DIR}/src/electrolink/electrolink_mraa.c
    PARENT_SCOPE
  )
endif ()
