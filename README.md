# vcmi-deps-windows-conan

Conan dependencies for windows

For generating:

- Use or install Ubuntu 22.04

- Install packages:

`sudo apt install mingw-w64 python3-pip`

- Install selected packages from Ubuntu 22.*10*

`wget -c http://mirrors.kernel.org/ubuntu/pool/universe/m/mingw-w64/mingw-w64-common_10.0.0-2_all.deb && dpkg -i /mingw-w64-common_10.0.0-2_all.deb`

`wget -c http://mirrors.kernel.org/ubuntu/pool/universe/m/mingw-w64/mingw-w64-i686-dev_10.0.0-2_all.deb && dpkg -i mingw-w64-i686-dev_10.0.0-2_all.deb`

- Install conan

`pip install conan`

- If necessary, clone vcmi repository

`git clone https://github.com/vcmi/vcmi.git vcmi`

`cd vcmi`

- Run conan:

`conan install . --install-folder=conan-generated --no-imports --build=missing --profile:build=default --profile:host=CI/conan/mingw-linux`
(this will take a while)

- Remove temporary files that we won't need: 

`conan remove --builds --src --force '*'`

- Create output archive with dependencies:

`tar -czvf vcmi-deps-windows-conan-w64.tgz -C ~/.conan data`

