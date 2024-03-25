# Using_openvino

cmake 하는 부분에서 나는  cmake -G "Visual Studio 17 2022" <path/to/openvino> 이게 

CMake Error: Error: generator : Visual Studio 16 2019
Does not match the generator used previously: Visual Studio 17 2022
Either remove the CMakeCache.txt file and CMakeFiles directory or choose a different binary directory.

이러한 오류가 발생했다. 물론 난 2019 버전이라 버전수정을 하였지만, 이전에 17 2022를 붙여서 했기때문에 이런 오류가 발생하는줄 알았다.
하지만 HINT 부분에서 발견할 수 있드시 , C make Build type을 적절히 바꿔줘야한다. 따라서 
-DCMAKE_BUILD_TYPE=RelWithDebInfo: This option generates PDB files with release information, making it suitable for debugging optimized builds.
이걸 치고 난 후 
 cmake -G "Visual Studio 17 2022" <path/to/openvino>  이 명령어를 적절히 (자신의 환경에맞게 수정하여) cmake를 진행하면 잘 처리된다.
 위에 저걸 치지 않아서 몇시간 동안 고생했다 ㅠㅠㅠ 

Create build directory:

mkdir build && cd build
In the build directory, run cmake to fetch project dependencies and generate a Visual Studio solution:

cmake -G "Visual Studio 17 2022" <path/to/openvino>
HINT: Generating PDB Files and Debugging Your Build
If you intend to generate PDB files and debug your build, it is essential to set the CMake build type appropriately. You should utilize one of the following CMake build type options:

-DCMAKE_BUILD_TYPE=RelWithDebInfo: This option generates PDB files with release information, making it suitable for debugging optimized builds.
-DCMAKE_BUILD_TYPE=Debug: This option generates PDB files optimized for debugging, providing comprehensive debugging information.
