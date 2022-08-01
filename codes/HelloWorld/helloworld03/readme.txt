cmd.exe "/K" '"C:\Program Files (x86)\Intel\oneAPI\setvars.bat" && powershell'
cmake ..
cmake --build .
mpiexec -n 4 .\Debug\testprj.exe


