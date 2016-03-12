# Copyright 2016, The libsigc++ Development Team
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA

set (SOURCE_FILES
	connection.cc
	signal_base.cc
	signal.cc
	trackable.cc
	functors/slot_base.cc
	functors/slot.cc
)

set (SIGCPP_LIB_NAME ${PROJECT_NAME}-${SIGCXX_API_VERSION})

add_library(${SIGCPP_LIB_NAME} SHARED ${SOURCE_FILES})

set_property (TARGET ${SIGCPP_LIB_NAME} PROPERTY VERSION ${PACKAGE_VERSION})
set_property(TARGET ${SIGCPP_LIB_NAME}  PROPERTY SOVERSION ${LIBSIGCPP_SOVERSION})

install (
	TARGETS
		${SIGCPP_LIB_NAME}
	DESTINATION
		lib
)


install (
	DIRECTORY	
		"${PROJECT_SOURCE_DIR}"
	DESTINATION
		"include/sigc++-${SIGCXX_API_VERSION}"
			FILES_MATCHING PATTERN
		"*.h"
)