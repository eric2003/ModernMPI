cmd.exe "/K" '"C:\Program Files (x86)\Intel\oneAPI\setvars.bat" && powershell'
cmake -DCMAKE_C_COMPILER=icx -DCMAKE_CXX_COMPILER=icx -DCMAKE_BUILD_TYPE=Release -GNinja ..
cmake --build .
mpiexec -n 4 .\testprj.exe

cmake .. -D CMAKE_BUILD_TYPE=Debug
cmake --build . --config Debug
cmake .. -D CMAKE_BUILD_TYPE=Release
cmake --build . --config Release

PS D:\work\mpi_work\ModernMPI\codes\pi\serial\01\build>  .\Release\testprj.exe
 time elapsed : 1.23406 seconds
pi = 3.1415926557174387 +/- 0.0000000021276456
