cmake_minimum_required(VERSION 3.16)

project(6-InheritedTypes VERSION 0.1 LANGUAGES CXX)

set(CMAKE_AUTOMOC ON)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt6 6.2 COMPONENTS Quick REQUIRED)

qt_add_executable(app6-InheritedTypes
    main.cpp player.h player.cpp footballteam.h footballteam.cpp
        striker.h striker.cpp defender.h defender.cpp
)

qt_add_qml_module(app6-InheritedTypes
    URI 6-InheritedTypes
    VERSION 1.0
    QML_FILES main.qml 
)

set_target_properties(app6-InheritedTypes PROPERTIES
    MACOSX_BUNDLE_GUI_IDENTIFIER my.example.com
    MACOSX_BUNDLE_BUNDLE_VERSION ${PROJECT_VERSION}
    MACOSX_BUNDLE_SHORT_VERSION_STRING ${PROJECT_VERSION_MAJOR}.${PROJECT_VERSION_MINOR}
    MACOSX_BUNDLE TRUE
    WIN32_EXECUTABLE TRUE
)

target_compile_definitions(app6-InheritedTypes
    PRIVATE $<$<OR:$<CONFIG:Debug>,$<CONFIG:RelWithDebInfo>>:QT_QML_DEBUG>)
target_link_libraries(app6-InheritedTypes
    PRIVATE Qt6::Quick)
