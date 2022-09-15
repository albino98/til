## Build .exe file

To build the project as single .exe file you can use [PyInstaller](http://www.pyinstaller.org/). 

Intall it with: **pip install pyinstaller**
  
To start compiling the project in a single .exe file use the following command: **pyinstaller.exe --onefile --windowed main.py**

:warning: **Note:** If you get the following error: **"C:\Users\username>pyinstaller 'pyinstaller' is not recognized as an internal or external command, operable program or batch file."**:

- Find the path of pyinstaller.exe, in my case it's: **"C:\Users\<user>\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.9_qbz5n2kfra8p0\LocalCache\local-packages\Python39\Scripts\pyinstaller.exe"** (search it in all disk), copy pyinstaller.exe in the root directory of the project:

![image](https://user-images.githubusercontent.com/63566699/129062713-b24f92bc-5167-4c0e-9f53-3f9774a50064.png)

- Then in the terminal move to the root path of the project ( "C:\Users\<user>\Desktop\DeployHelper" ) and execute command: "**.\pyinstaller.exe --onefile --windowed main.py**". the characters "**.\\**" are used to make trusted the pyinstaller.exe.

Now you should have "build" and "dist" folder. In "dist" folder you have main.exe.
