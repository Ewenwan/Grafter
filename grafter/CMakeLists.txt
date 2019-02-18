set(LLVM_LINK_COMPONENTS support)

add_clang_executable(grafter
 DependenceGraph.cpp
 TraversalSynthesizer.cpp
 AccessPath.cpp
 FunctionAnalyzer.cpp
 Logger.cpp
 FunctionsFinder.cpp
 RecordAnalyzer.cpp
 Annotations.cpp
 ToolMain.cpp
 DependenceAnalyzer.cpp
 FuseTransformation.cpp
 FSMUtility.cpp
 StatementInfo.cpp

 DEPENDS
 intrinsics_gen
 )

include_directories(${LLVM_MAIN_SRC_DIR}/tools/clang/include)
include_directories(${LLVM_BINARY_DIR}/tools/clang/include)

target_link_libraries(grafter
  PRIVATE
  clangAST
  clangBasic
  clangDriver
  clangFrontend
  clangRewriteFrontend
  clangStaticAnalyzerFrontend
  clangTooling
  /usr/local/lib/libfst.13.dylib
  # /usr/local/lib/libfst.so.13
  )