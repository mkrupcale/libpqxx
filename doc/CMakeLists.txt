################################################################################
# AUTOMATICALLY GENERATED FILE -- DO NOT EDIT.
#
# This file is generated automatically by libpqxx's template2mak.py script, and
# will be rewritten from time to time.
#
# If you modify this file, chances are your modifications will be lost.
#
# The template2mak.py script should be available in the tools directory of the
# libpqxx source archive.
#
# Generated from template './doc/CMakeLists.txt.template'.
################################################################################
find_program(HAVE_DOXYGEN doxygen)

if(NOT HAVE_DOXYGEN)
    message(FATAL_ERROR "*****************************************************
Doxygen not found.
Install it, or configure with -DBUILD_DOC=OFF
*****************************************************")
endif()

find_program(HAVE_XMLTO xmlto)

if(NOT HAVE_XMLTO)
    message(FATAL_ERROR "*****************************************************
xmlto not found.
Install it, or configure with -DBUILD_DOC=OFF
*****************************************************")
endif()

set(PQXXVERSION "${CMAKE_PROJECT_VERSION}")
set(top_srcdir "${CMAKE_SOURCE_DIR}")
set(PQXX_ABI "${PROJECT_VERSION_MAJOR}.${PROJECT_VERSION_MINOR}")
set(PQXX_MAJOR "${PROJECT_VERSION_MAJOR}")
set(PQXX_MINOR "${PROJECT_VERSION_MINOR}")

find_program(HAVE_DOT dot)
if(HAVE_DOT)
    set(HAVE_DOT YES)
else()
    set(HAVE_DOT NO)
endif()

configure_file(Doxyfile.in Doxyfile)

if(HAVE_DOXYGEN)
    set(DOXYGEN_SOURCES
    	"${CMAKE_SOURCE_DIR}/include/pqxx/array.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/binarystring.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/compiler-public.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/connection.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/cursor.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/dbtransaction.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/errorhandler.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/except.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/field.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/isolation.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/largeobject.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/nontransaction.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/notification.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/pipeline.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/prepared_statement.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/result.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/result_iterator.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/robusttransaction.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/row.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/separated_list.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/strconv.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/stream_from.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/stream_to.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/subtransaction.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/transaction.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/transaction_base.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/transactor.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/types.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/util.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/version.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/zview.hxx"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/doc/README.md"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/doc/accessing-results.md"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/doc/escaping.md"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/doc/getting-started.md"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/doc/mainpage.md"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/doc/performance.md"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/doc/prepared-statement.md"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/doc/streams.md"
    	"${CMAKE_SOURCE_DIR}/include/pqxx/doc/thread-safety.md"
    	"${CMAKE_SOURCE_DIR}/src/array.cxx"
    	"${CMAKE_SOURCE_DIR}/src/binarystring.cxx"
    	"${CMAKE_SOURCE_DIR}/src/connection.cxx"
    	"${CMAKE_SOURCE_DIR}/src/cursor.cxx"
    	"${CMAKE_SOURCE_DIR}/src/encodings.cxx"
    	"${CMAKE_SOURCE_DIR}/src/errorhandler.cxx"
    	"${CMAKE_SOURCE_DIR}/src/except.cxx"
    	"${CMAKE_SOURCE_DIR}/src/field.cxx"
    	"${CMAKE_SOURCE_DIR}/src/largeobject.cxx"
    	"${CMAKE_SOURCE_DIR}/src/notification.cxx"
    	"${CMAKE_SOURCE_DIR}/src/pipeline.cxx"
    	"${CMAKE_SOURCE_DIR}/src/result.cxx"
    	"${CMAKE_SOURCE_DIR}/src/robusttransaction.cxx"
    	"${CMAKE_SOURCE_DIR}/src/row.cxx"
    	"${CMAKE_SOURCE_DIR}/src/sql_cursor.cxx"
    	"${CMAKE_SOURCE_DIR}/src/statement_parameters.cxx"
    	"${CMAKE_SOURCE_DIR}/src/strconv.cxx"
    	"${CMAKE_SOURCE_DIR}/src/stream_from.cxx"
    	"${CMAKE_SOURCE_DIR}/src/stream_to.cxx"
    	"${CMAKE_SOURCE_DIR}/src/subtransaction.cxx"
    	"${CMAKE_SOURCE_DIR}/src/transaction.cxx"
    	"${CMAKE_SOURCE_DIR}/src/transaction_base.cxx"
    	"${CMAKE_SOURCE_DIR}/src/util.cxx"
    	"${CMAKE_SOURCE_DIR}/src/version.cxx"
    )
    set(DOXYGEN_STAMP_FILE "${CMAKE_CURRENT_BINARY_DIR}/doxygen.stamp")
    add_custom_command(VERBATIM
    	OUTPUT ${DOXYGEN_STAMP_FILE}
    	COMMAND ${CMAKE_COMMAND} -E make_directory ${CMAKE_CURRENT_BINARY_DIR}/html/Reference
    	COMMAND doxygen Doxyfile
    	COMMAND ${CMAKE_COMMAND} -E touch ${DOXYGEN_STAMP_FILE}
    	DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/Doxyfile ${DOXYGEN_SOURCES}
    	COMMENT "Generate API documentation"
    )
    add_custom_target(doxygen ALL
    	DEPENDS ${DOXYGEN_STAMP_FILE}
    	SOURCES ${DOXYGEN_SOURCES}
    )
    install(
    	DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/html/Reference
    	DESTINATION ${CMAKE_INSTALL_DOCDIR}/html
    )
endif()

if(HAVE_XMLTO)
    set(XMLTO_SOURCES
    	"${CMAKE_CURRENT_SOURCE_DIR}/libpqxx.xml"
    )
    set(XMLTO_STAMP_FILE "${CMAKE_CURRENT_BINARY_DIR}/xmlto.stamp")
    add_custom_command(VERBATIM
    	OUTPUT ${XMLTO_STAMP_FILE}
    	COMMAND ${CMAKE_COMMAND} -E make_directory ${CMAKE_CURRENT_BINARY_DIR}/html/Tutorial
    	COMMAND xmlto -o html/Tutorial xhtml "${CMAKE_CURRENT_SOURCE_DIR}/libpqxx.xml"
    	COMMAND ${CMAKE_COMMAND} -E touch ${XMLTO_STAMP_FILE}
    	DEPENDS ${XMLTO_SOURCES}
    	COMMENT "Generate tutorial"
    )
    add_custom_target(tutorial ALL
    	DEPENDS ${XMLTO_STAMP_FILE}
    	SOURCES ${XMLTO_SOURCES}
    )
    install(
    	DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/html/Tutorial
    	DESTINATION ${CMAKE_INSTALL_DOCDIR}/html
    )
endif()
