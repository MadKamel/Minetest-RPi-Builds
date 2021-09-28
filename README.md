# Minetest-RPi-Builds
This repository provides a build of Minetest 5.5.0-dev built on the Raspberry Pi 0.
The binary might work on a 3 or 4, but I'd have to test it out to be sure.
More builds coming soon, maybe?

*PLEASE NOTE: You may need to restart your computer after instruction 3 to finalize libgl1-mesa-dev.*

## The Process

	sudo apt update
	sudo apt install g++ make libc6-dev cmake libbz2-dev libpng-dev libjpeg-dev libxxf86vm-dev libgl1-mesa-dev libsqlite3-dev libogg-dev libvorbis-dev libopenal-dev libcurl4-gnutls-dev libfreetype6-dev zlib1g-dev libgmp-dev libjsoncpp-dev libzstd-dev
	cd
	git clone --depth=1 https://github.com/minetest/minetest.git
	cd minetest/lib
	git clone --depth=1 https://github.com/minetest/irrlicht.git
	mv irrlicht irrlichtmt
	cd ../
	cmake .
	make -j$(nproc)

## Explaination, Line-by-Line

1. This command updates packages already installed. Standard practice.
2. Install all the libraries, g++, make and cmake. These last three are used in compiling the repository.
3. Changes the directory to 'home/(username)/'
4. Clone the minetest codebase from Github. Basically downloads the source code.
5. Change directory to 'lib/', where you will notice other codebases. These are built alongside Minetest during compilation, ultimately ending up in the final binary file.
6. Clone Minetest's fork of Irrlicht.
7. Rename irrlicht to irrlichtmt, otherwise cmake won't even recognize it. This took me a good damn hour to fix.
8. Move back to minetest's root directory
9. Run cmake on the current directory, this creates a compilation configuration, checking to see if everything is in order.
10. Run make. This compiles the codebase. This will take a hell of a long time, so I recommend leaving it to do this overnight while you sleep.
