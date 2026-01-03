## System Configuration

The **System Configuration** utility (`MSConfig`) is for advanced troubleshooting, and its main purpose is to help diagnose startup issues. 

Reference the following document [here](https://docs.microsoft.com/en-us/troubleshoot/windows-client/performance/system-configuration-utility-troubleshoot-configuration-errors) for more information on the System Configuration utility. 

There are several methods to launch System Configuration. One method is from the Start Menu.

![](https://assets.tryhackme.com/additional/win-fun2/msconfig-start.png)

**Note**: You need local administrator rights to open this utility. 

The utility has five tabs across the top. Below are the names for each tab. We will briefly cover each tab in this task. 

1. General
2. Boot
3. Services
4. Startup
5. Tools

![](https://assets.tryhackme.com/additional/win-fun2/msconfig1.png)

In the **General** tab, we can select what devices and services for Windows to load upon boot. The options are: **Normal**, **Diagnostic**, or **Selective**. 

In the **Boot** tab, we can define various boot options for the Operating System. 

![](https://assets.tryhackme.com/additional/win-fun2/msconfig2.png)

The **Services** tab lists all services configured for the system regardless of their state (running or stopped). A service is a special type of application that runs in the background.  

![](https://assets.tryhackme.com/additional/win-fun2/msconfig3.png)

In the **Startup** tab, you won't see anything interesting in the attached VM.  Below is a screenshot of the Startup tab for **MSConfig** from my local machine. 

![](https://assets.tryhackme.com/additional/win-fun2/msconfig4.png)

As you can see, Microsoft advises using **Task Manager (**`taskmgr`**)** to manage (enable/disable) startup items. The System Configuration utility is **NOT** a startup management program. 

If you open the Task Manager for the attached VM, you will notice that it doesn't display a Startup tab. You will also not see anything in the Startup tab inside the `msconfig` utility, as shown above. This is because the attached machine is a Windows server, and Windows servers handle startup applications differently than Windows client systems. Unlike Windows 10 or 11, you will not see startup programs in `Task Manager` or in the Startup tab of `msconfig`. On these Windows server machines, the only reliable way to view user-level startup items is through the Startup folder itself. You can access it by pressing `**Win + R**`, which opens the Run Dialog, typing **`shell:startup`**, and then pressing Enter. This will display all startup programs as shortcuts or executables that are configured to run automatically the next time a user logs in. This is where you can verify applications that are configured to launch at startup. Below is a screenshot of the startup folder from another Windows server (not from the attached VM):

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1764766867993.png)

Now coming back to the `msconfig`. There is a list of various utilities (tools) in the Tools tab here that we can run to configure the operating system further. There is a brief description of each tool to provide some insight into what the tool is for. 

![](https://assets.tryhackme.com/additional/win-fun2/msconfig5.png)

Notice the **Selected command** section. The information in this textbox will change per tool.

To run a tool, we can use the command to launch the tool via the run prompt, command prompt, or by clicking the `Launch` button. 

## Advanced System Settings

Windows gives you some additional configuration settings as well, which you can use to control the performance behavior and system recovery. To access this option, you can search for `View advanced system settings` in your search bar and open it. This will open a `System Properties` panel as shown below:

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1764846840046.png)

Windows uses a page file as an extra virtual memory space when the physical RAM becomes full. This helps to prevent slowdowns or application crashes when the system runs out of memory. You can view or modify the page file by navigating to the `Advanced` option at the top and clicking `Settings` under the `Performance` tab.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1764846840021.png)

So after clicking the Settings, you will get the Performance Options window, as can be seen below:

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1764846840008.png)

 In this Performance tab, the **Advanced** option can also tell you about the page file size configured for the drives. In this case, it's `1048 MB`. The other settings here can give you the following information:

- The drive where the page file is stored
- The initial size (MB)
- The maximum size
- Whether Windows manages the size automatically

There is another cool configuration that you can find in the Advanced System Settings. It is known as Startup and Recovery. Windows can create a crash dump file whenever it encounters a critical error, such as a Blue Screen of Death. This crash dump helps the administrators or analysts understand what went wrong during the crash. You can view or modify the crash dump settings by navigating to the `Advanced` option at the top and then clicking `Settings` under the `Startup and Recovery` section.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1764852718826.png)

So after clicking the settings, you will see the `Startup and Recovery` window, as shown below:

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1764852718742.png)

Here, you will find different settings for the startup and recovery. The `Write debugging information` dropdown tells you the type of crash dump configured for the system. Windows supports different dump types, such as:

- Automatic memory dump
- Kernel memory dump
- Small memory dump (256 KB)
- Complete memory dump
- None

This setting shows how much information Windows will save in the crash dump when a system crash occurs.