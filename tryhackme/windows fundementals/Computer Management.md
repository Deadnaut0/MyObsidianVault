The **Computer Management** (`compmgmt`) utility has three primary sections: System Tools, Storage, and Services and Applications.

![](https://assets.tryhackme.com/additional/win-fun2/compmgmt1.png)

**System Tools**

Let's start with **Task Scheduler**. Per Microsoft, with Task Scheduler, we can create and manage common tasks that our computer will carry out automatically at the times we specify.

A task can run an application, a script, etc., and tasks can be configured to run at any point. A task can run at log in or at log off. Tasks can also be configured to run on a specific schedule, for example, every five mins.

To view the scheduled tasks that are present on the system, click `Task Scheduler Library`. This will display all the scheduled tasks of the system. You can click on any of them to view their details. The screenshot below shows a scheduled task named `SystemInfoDailyLog` configured to run `every day at 10:00 AM`. Here, you will see the program or command that will run when the task is triggered.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1764761078608.png)

It is also important to note that some scheduled tasks are not recurring and are made to run just once at a specific time. In this case, we would see something like `At 2:50 PM on 6/15/2025` as the trigger.

To create a basic task, click on `Create Basic Task` under **Actions** (right pane).

![](https://assets.tryhackme.com/additional/win-fun2/create-task.png)

Next is **Event Viewer**.

Event Viewer allows us to view events that have occurred on the computer. These records of events can be seen as an audit trail that can be used to understand the activity of the computer system. This information is often used to diagnose problems and investigate actions executed on the system. 

![](https://assets.tryhackme.com/additional/win-fun2/event-viewer.png)

Event Viewer has three panes.

1. The pane on the left provides a hierarchical tree listing of the event log providers. (as shown in the image above)
2. The pane in the middle will display a general overview and summary of the events specific to a selected provider.
3. The pane on the right is the actions pane.

There are five types of events that can be logged. Below is a table from [docs.microsoft.com](https://docs.microsoft.com/en-us/windows/win32/eventlog/event-types) providing a brief description for each.

![](https://assets.tryhackme.com/additional/win-event-logs/five-event-types.png)

The standard logs are visible under Windows Logs. Below is a table from [docs.microsoft.com](https://docs.microsoft.com/en-us/windows/win32/eventlog/eventlog-key) providing a brief description for each.

![](https://assets.tryhackme.com/additional/win-event-logs/standard-event-logs.png)

For more information about Event Viewer and Event Logs, please refer to the Windows Event Log [room](https://tryhackme.com/room/windowseventlogs). 

**Shared Folders** is where you will see a complete list of shares and folders shared that others can connect to. 

![](https://assets.tryhackme.com/additional/win-fun2/shared-folders.png)

In the above image, under Shares, are the default share of Windows, C$, and default remote administration shares created by Windows, such as ADMIN$. 

As with any object in Windows, you can right-click on a folder to view its properties, such as Permissions (who can access the shared resource). 

Under **Sessions**, you will see a list of users who are currently connected to the shares. In this VM, you won't see anybody connected to the shares.

All the folders and/or files that the connected users access will list under **Open Files**.

The **Local Users and Groups** section you should be familiar with from [Windows Fundamentals 1](https://tryhackme.com/room/windowsfundamentals1xbx) because it's `lusrmgr.msc`.

In **Performance**, you'll see a utility called **Performance Monitor** (`perfmon`).

Perfmon is used to view performance data either in real-time or from a log file. This utility is useful for troubleshooting performance issues on a computer system, whether local or remote. 

![](https://assets.tryhackme.com/additional/win-fun2/perfmon.png)

**Device Manager** allows us to view and configure the hardware, such as disabling any hardware attached to the computer.

![](https://assets.tryhackme.com/additional/win-fun2/device-mgr.png)

**Storage**  

Under Storage is **Windows Server Backup** and **Disk Management**. We'll only look at Disk Management in this room.

**Note**: Since the virtual machine is a Windows Server operating system, there are utilities available that you will typically not see in Windows 10.  

![](https://assets.tryhackme.com/additional/win-fun2/disk-mgmt.png)

Disk Management is a system utility in Windows that enables you to perform advanced storage tasks.  Some tasks are:

- Set up a new drive
- Extend a partition
- Shrink a partition
- Assign or change a drive letter (ex. E:) 

**Services and Applications**

Recall from the previous task, a service is a special type of application that runs in the background. You can see all the services and their statuses by clicking the Services button given under the Services and Applications section, as shown below:

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1764762861185.png)

The services shown above have their display names, status, and other values. If you want to get more information about any service, right-click on the service and click `properties`. Here, you will see additional details, such as the service name (which differs from the display name), the path to its executable, its startup type, and other relevant information.

![](https://assets.tryhackme.com/additional/win-fun2/service.png)

There is a field known as Startup type in a service’s Properties window, as shown above. It determines how and when the service is configured to start. We can set a service to `Automatic`, which means it starts every time the system boots, or `Manual`, which means it only starts when another process or user triggers this service, or `Disabled`, which means it should not run at all. The service shown in the screenshot above is set to `Automatic`.

WMI Control configures and controls the **Windows Management Instrumentation** (WMI) service.

Per Wikipedia, "_WMI allows scripting languages (such as VBScript or Windows PowerShell) to manage Microsoft Windows personal computers and servers, both locally and remotely. Microsoft also provides a command-line interface to WMI called Windows Management Instrumentation Command-line (WMIC)._"

**Note**: The WMIC tool is deprecated in Windows 10, version 21H1. Windows PowerShell supersedes this tool for WMI.