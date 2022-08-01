cmd.exe "/K" '"C:\Program Files (x86)\Intel\oneAPI\setvars.bat" && powershell'
cmake -DCMAKE_C_COMPILER=icx -DCMAKE_CXX_COMPILER=icx -DCMAKE_BUILD_TYPE=Release -GNinja ..
cmake --build .
mpiexec -n 4 .\testprj.exe

cmake .. -D CMAKE_BUILD_TYPE=Debug
cmake --build . --config Debug
cmake .. -D CMAKE_BUILD_TYPE=Release
cmake --build . --config Release


cmake .. -D CMAKE_BUILD_TYPE=Release
cmake --build . --config Release
PS D:\work\mpi_work\ModernMPI\codes\pi\mpi\01\build> mpiexec -n 1 .\Release\testprj.exe
 time elapsed : 1.23853 seconds
pi = 3.1415926557174387 +/- 0.0000000021276456
PS D:\work\mpi_work\ModernMPI\codes\pi\mpi\01\build> mpiexec -n 2 .\Release\testprj.exe
 time elapsed : 0.616899 seconds
pi = 3.1415926557176190 +/- 0.0000000021278259
PS D:\work\mpi_work\ModernMPI\codes\pi\mpi\01\build> mpiexec -n 4 .\Release\testprj.exe
 time elapsed : 0.387862 seconds
pi = 3.1415926557171856 +/- 0.0000000021273925
PS D:\work\mpi_work\ModernMPI\codes\pi\mpi\01\build> mpiexec -n 8 .\Release\testprj.exe
 time elapsed : 0.246694 seconds
pi = 3.1415926557174405 +/- 0.0000000021276474
PS D:\work\mpi_work\ModernMPI\codes\pi\mpi\01\build> mpiexec -n 16 .\Release\testprj.exe
 time elapsed : 0.157682 seconds
pi = 3.1415926557174023 +/- 0.0000000021276092
PS D:\work\mpi_work\ModernMPI\codes\pi\mpi\01\build> mpiexec -n 32 .\Release\testprj.exe
 time elapsed : 0.166042 seconds
pi = 3.1415926557173339 +/- 0.0000000021275408