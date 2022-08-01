cmd.exe "/K" '"C:\Program Files (x86)\Intel\oneAPI\setvars.bat" && powershell'
cmake -DCMAKE_C_COMPILER=icx -DCMAKE_CXX_COMPILER=icx -DCMAKE_BUILD_TYPE=Release -GNinja ..
cmake --build .
mpiexec -n 4 .\testprj.exe

cmake .. -D CMAKE_BUILD_TYPE=Debug
cmake --build . --config Debug
cmake .. -D CMAKE_BUILD_TYPE=Release
cmake --build . --config Release

mpiexec -n 4 .\Release\testprj.exe

cmake .. -D CMAKE_BUILD_TYPE=Release
cmake --build . --config Release

PS D:\work\mpi_work\ModernMPI\codes\pi\openmp\01\build>  .\Release\testprj.exe
 time elapsed : 1.22983 seconds
pi = 3.1415926557174387 +/- 0.0000000021276456
PS D:\work\mpi_work\ModernMPI\codes\pi\openmp\01\build>  .\Release\testprj.exe 1
 time elapsed : 1.24983 seconds
pi = 3.1415926557174387 +/- 0.0000000021276456
PS D:\work\mpi_work\ModernMPI\codes\pi\openmp\01\build>  .\Release\testprj.exe 2
 time elapsed : 0.613355 seconds
pi = 3.1415926557174001 +/- 0.0000000021276070
PS D:\work\mpi_work\ModernMPI\codes\pi\openmp\01\build>  .\Release\testprj.exe 4
 time elapsed : 0.440285 seconds
pi = 3.1415926557173690 +/- 0.0000000021275759
PS D:\work\mpi_work\ModernMPI\codes\pi\openmp\01\build>  .\Release\testprj.exe 8
 time elapsed : 0.28097 seconds
pi = 3.1415926557174503 +/- 0.0000000021276572
PS D:\work\mpi_work\ModernMPI\codes\pi\openmp\01\build>  .\Release\testprj.exe 16
 time elapsed : 0.17285 seconds
pi = 3.1415926557173792 +/- 0.0000000021275861
PS D:\work\mpi_work\ModernMPI\codes\pi\openmp\01\build>  .\Release\testprj.exe 32
 time elapsed : 0.196724 seconds
pi = 3.1415926557173148 +/- 0.0000000021275217