SET(CXX_TEST_PATH ${EXECUTABLE_OUTPUT_PATH})
SET(TEST_DATA_ROOT ${PROJECT_SOURCE_DIR}/Testing/Data)
SET(TEMP ${PROJECT_BINARY_DIR}/Testing/Temporary)

SET(KIT lsqr)
CREATE_TEST_SOURCELIST(Tests ${KIT}CxxTests.cxx
  lsqrTest1.cxx
  lsqrTest2.cxx
  lsmrTest2.cxx
  )

SET (TestsToRun ${Tests})
REMOVE (TestsToRun ${KIT}CxxTests.cxx)

ADD_EXECUTABLE(${KIT}CxxTests ${Tests})
TARGET_LINK_LIBRARIES(${KIT}CxxTests lsqr)

SET( lsqr_TESTS ${CXX_TEST_PATH}/${KIT}CxxTests)

FUNCTION( SIMPLE_TEST  TESTNAME )
  ADD_TEST( ${TESTNAME} ${lsqr_TESTS} ${TESTNAME} )
ENDFUNCTION( SIMPLE_TEST  )


SIMPLE_TEST( lsqrTest1 )
SIMPLE_TEST( lsqrTest2 )
SIMPLE_TEST( lsmrTest2 )

