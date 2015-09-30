CMAKE_ALT1 := /usr/local/bin/cmake
CMAKE_ALT2 := /Applications/CMake.app/Contents/bin/cmake
CMAKE := $(shell \
	which cmake 2>/dev/null || \
	([ -e ${CMAKE_ALT1} ] && echo "${CMAKE_ALT1}") || \
	([ -e ${CMAKE_ALT2} ] && echo "${CMAKE_ALT2}") \
	)

all: DebugFast


Debug: build
	(cd build && ${CMAKE} -DCMAKE_BUILD_TYPE=$@ .. && make)

DebugFast: build
	(cd build && ${CMAKE} -DCMAKE_BUILD_TYPE=$@ .. && make)

DebugNDEBUG: build
	(cd build && ${CMAKE} -DCMAKE_BUILD_TYPE=$@ .. && make)

Release: build
	(cd build && ${CMAKE} -DCMAKE_BUILD_TYPE=$@ .. && make)


run:
	build/cis565_rasterizer objs/tri.obj

build:
	mkdir -p build

clean:
	((cd build && make clean) 2>&- || true)

.PHONY: all Debug DebugFast DebugNDEBUG Release clean