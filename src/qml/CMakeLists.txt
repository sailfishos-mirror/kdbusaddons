# SPDX-License-Identifier: BSD-2-Clause
# SPDX-FileCopyrightText: 2025 Harald Sitter <sitter@kde.org>

qt_add_dbus_interface(dbus_SRCS org.freedesktop.DBus.Properties.xml org.freedesktop.DBus.Properties)

ecm_add_qml_module(kdbusaddonsplugin URI org.kde.dbusaddons VERSION 1.0 GENERATE_PLUGIN_SOURCE INSTALLED_PLUGIN_TARGET KF6::kdbusaddonsplugin)
target_sources(kdbusaddonsplugin PRIVATE ${dbus_SRCS} dbusinterface.cpp dbusvariantwrapper.cpp kdbuserror.cpp pack.cpp unpack.cpp)
target_link_libraries(kdbusaddonsplugin PRIVATE Qt::DBus Qt::DBusPrivate Qt::Quick PkgConfig::dbus-1)
ecm_finalize_qml_module(kdbusaddonsplugin DESTINATION ${KDE_INSTALL_QMLDIR})
