# vcmi-deps-windows-conan

Conan dependencies for windows

For generating:

- Use or install Ubuntu 22.04

- Install packages:
- - `sudo apt install mingw-w64 python3-pip git build-essential gcc nsis`

- Install selected packages from Ubuntu 22.*10*
- - `wget -c http://mirrors.kernel.org/ubuntu/pool/universe/m/mingw-w64/mingw-w64-common_10.0.0-2_all.deb && sudo dpkg -i mingw-w64-common_10.0.0-2_all.deb`
- - (x64) `wget -c http://mirrors.kernel.org/ubuntu/pool/universe/m/mingw-w64/mingw-w64-x86-64-dev_10.0.0-2_all.deb && sudo dpkg -i mingw-w64-x86-64-dev_10.0.0-2_all.deb`
- - (i686) `wget -c http://mirrors.kernel.org/ubuntu/pool/universe/m/mingw-w64/mingw-w64-i686-dev_10.0.0-2_all.deb && sudo dpkg -i mingw-w64-i686-dev_10.0.0-2_all.deb`

- Set correct cross-compiler
- - (x64) `sudo update-alternatives --set x86_64-w64-mingw32-g++ /usr/bin/x86_64-w64-mingw32-g++-posix`
- - (i686) `sudo update-alternatives --set i686-w64-mingw32-g++ /usr/bin/i686-w64-mingw32-g++-posix`

- Install conan
- - `sudo pip3 install conan`

- If necessary, clone vcmi repository
- - `git clone https://github.com/vcmi/vcmi.git vcmi`
- - `cd vcmi`

- Run conan: (this will take a while)
- - (x64) `conan install . --install-folder=conan-generated --no-imports --build=missing --profile:build=default --profile:host=CI/conan/mingw64-linux.jinja` 
- - (i686) `conan install . --install-folder=conan-generated --no-imports --build=missing --profile:build=default --profile:host=CI/conan/mingw32-linux.jinja`

- Remove temporary files that we won't need: 
- - `conan remove --builds --src --force '*'`

- Create output archive with dependencies:
- - `tar -czvf vcmi-deps-windows-conan-w64.tgz -C ~/.conan data`

