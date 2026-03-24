```
██╗ ██████╗ ███████╗ █████╗ ███╗   ███╗ █████╗ 
██║██╔═══██╗██╔════╝██╔══██╗████╗ ████║██╔══██╗
██║██║   ██║███████╗███████║██╔████╔██║███████║
╚═╝██║   ██║╚════██║██╔══██║██║╚██╔╝██║██╔══██║
██╗╚██████╔╝███████║██║  ██║██║ ╚═╝ ██║██║  ██║
╚═╝ ╚═════╝ ╚══════╝╚═╝  ╚═╝╚═╝     ╚═╝╚═╝  ╚═╝
============================================================
           INTEGRATION AND DISTRIBUTION GUIDE
============================================================

This document summarizes the steps to create a single, standalone executable (EXE) that runs with administrator rights.

1. DLL INTEGRATION (Costura.Fody)
--------------------------------------
- Install the NuGet package "Costura.Fody".  
- Create a file named "FodyWeavers.xml" at the root of the project.  
- Add the following content to the file:
    <Weavers>
      <Costura />
    </Weavers>
- The DLLs will be automatically compressed and included in the EXE during the build.

2. ADMINISTRATOR MODE (app.manifest)
--------------------------------------
- Add an "Application Manifest File (Windows only)" named "app.manifest".  
- Modify the following line:
    <requestedExecutionLevel level="asInvoker" uiAccess="false" />
- Replace "asInvoker" with "requireAdministrator":
    <requestedExecutionLevel level="requireAdministrator" uiAccess="false" />
- Note: Remember to check "Allow unsafe code" in the build properties if needed.

3. BUILD
----------------------
- Set the Solution Configuration to "Release" (at the top of Visual Studio).  
- Go to the menu: Build > Build Solution.  
- Your single EXE will be located at: \bin\Release\ConsolPanel.exe
```