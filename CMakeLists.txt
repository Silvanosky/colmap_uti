cmake_minimum_required(VERSION 3.16)

project(ColmapPrj)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

find_package(Colmap REQUIRED)
find_package(OpenMP REQUIRED)
# or to require a specific version: find_package(COLMAP 3.4 REQUIRED)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fopenmp -std=c++17")

add_executable(colmap_sfm colmap_sfm.cpp)
add_executable(colmap_export_features colmap_export_features.cpp)
add_executable(colmap_import_features colmap_import_features.cpp)
add_executable(colmap_import_features_batch colmap_import_features_batch.cpp)
#add_executable(colmap_import_Rt colmap_import_Rt.cpp)
add_executable(colmap_transfer_features colmap_transfer_features.cpp)
add_executable(colmap_modify_intrinsics colmap_modify_intrinsics.cpp)
add_executable(colmap_add_camera colmap_add_camera.cpp)
add_executable(colmap_export_Rt colmap_export_Rt.cpp)
add_executable(colmap_init_poses colmap_init_poses.cpp)

target_link_libraries(colmap_sfm PUBLIC colmap::colmap)
target_link_libraries(colmap_export_features PUBLIC colmap::colmap)
target_link_libraries(colmap_import_features PUBLIC colmap::colmap)
target_link_libraries(colmap_import_features_batch PUBLIC colmap::colmap)
#target_link_libraries(colmap_import_Rt PUBLIC colmap::colmap)
target_link_libraries(colmap_transfer_features PUBLIC colmap::colmap)
target_link_libraries(colmap_modify_intrinsics PUBLIC colmap::colmap)
target_link_libraries(colmap_add_camera PUBLIC colmap::colmap)
target_link_libraries(colmap_export_Rt PUBLIC colmap::colmap)
target_link_libraries(colmap_init_poses PUBLIC colmap::colmap)

install(TARGETS
    colmap_sfm
    colmap_export_features
    colmap_import_features
    colmap_import_features_batch
    #    colmap_import_Rt
    colmap_transfer_features
    colmap_modify_intrinsics
    colmap_add_camera
    colmap_export_Rt
    colmap_init_poses
    DESTINATION "bin")
