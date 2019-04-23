---
title: at
description: Windows 命令主题**在**-计划命令和程序将在指定的时间和日期在一台计算机上运行。
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ff18fd16-9437-4c53-8794-bfc67f5256b3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 26ffa962541666e0e19b1c408bd6ab0b904296dd
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2019
ms.locfileid: "59832518"
---
# <a name="at"></a>at

>适用于：Windows 服务器 （半年频道），Windows Server 2016 中，Windows Server 2012 R2、 Windows Server 2012

计划在指定的时间和日期在一台计算机上运行的命令和程序。 可以使用**在**仅当计划服务运行。 使用不带参数，**在**列出了计划的命令。
## <a name="syntax"></a>语法
```
at [\\computername] [[id] [/delete] | /delete [/yes]]
at [\\computername] <time> [/interactive] [/every:date[,...] | /next:date[,...]] <command>
```
## <a name="parameters"></a>Parameters
|参数|描述|
|----------------------|--------|
|\\\\\<computerName\>|指定远程计算机。 如果省略此参数，**在**计划命令和在本地计算机上的程序。|
|\<id\>|指定分配给计划命令的标识号。|
|/delete|取消计划的命令。 如果省略*ID*，所有的计算机上的计划命令已取消。|
|/yes|回答是的所有查询从系统删除预定的事件时。|
|\<time\>|指定当您想要运行该命令的时间。 时间表示为小时： 分钟以 24 小时表示法 (即，从 00:00 [午夜] 到 23:59)。|
|/interactive|允许*命令*与登录时的用户的桌面进行交互*命令*运行。|
|/ 每个：|运行*命令*上每个指定的日期或数周或月 （例如，每个星期四或每月的第三天）。|
|\<date\>|指定当您想要运行该命令的日期。 可以指定一周中的一个或多个日期 (即，键入**M**，**T**，**W**，**Th**，**F**，**S**，**Su**) 或一个或多个月份中的天 （即，键入 1 到 31 之间）。 用逗号分隔多个日期项。 如果省略*日期*，**在**使用当前日期的月份。|
|/ 下一步：|运行*命令*上 （例如下, 一步星期四） 一天中的下一个匹配项。|
|\<command\>|指定 Windows 命令中，程序 （即，.exe 或.com 文件） 或你想要运行的批处理程序 （即，.bat 或.cmd 文件）。 当该命令需要路径作为参数时，使用绝对路径 （即，整个路径开头的驱动器号）。 如果该命令是在远程计算机上，指定通用命名约定 (UNC) 表示法，用于在服务器和共享名称，而不是远程的驱动器号。|
|/?|在命令提示符下显示帮助。|
## <a name="remarks"></a>备注
-   **schtasks**是另一个命令行计划工具，可用于创建和管理计划的任务。 有关详细信息**schtasks**，请参阅相关主题。
-   使用**在**  
    若要使用**在**，您必须是本地 Administrators 组的成员。
-   正在加载 Cmd.exe  
    **在**不会自动加载 Cmd.exe，命令解释器，然后再运行命令。 如果你不运行可执行文件 (.exe) 文件，您必须显式加载 Cmd.exe 命令开头，如下所示： **cmd /c dir > c:\test.out**
-   查看计划命令  
    当你使用**在**不带命令行选项，计划的任务将显示格式的表中如下所示：
    ```
    Status  ID   Day        time        Command Line
    OK      1    Each F     4:30 PM     net send group leads status due
    OK      2    Each M     12:00 AM    chkstor > check.file
    OK      3    Each F     11:59 PM    backup2.bat
    ```
-   包括识别号 (*ID*)  
    当包括识别号 (*ID*) 与**在**在命令提示符下，对单个条目的信息会显示在类似于以下格式：  
    ```
    Task ID:      1
    Status:       OK
    Schedule:     Each  F
    time of Day:  4:30 PM
    Command:      net send group leads status due
    ```
    您计划使用的命令后**处**，尤其是已检查的命令语法是否正确键入的命令行选项的命令**在**不带命令行选项。 如果命令行列中的信息不正确，请删除命令，然后重新键入。 如果仍然不正确，请重新键入具有较少的命令行选项的命令。
-   查看结果  
    与命令安排**在**作为后台进程运行。 输出不会显示在屏幕上。 若要将输出重定向到文件中，使用重定向符号 (>)。 如果将输出重定向到文件，则需要转义前使用符号 (^) 重定向符号，无论您使用**在**在命令行或批处理文件中。 例如，若要将输出重定向到 Output.text，键入：  
    `at 14:45 c:\test.bat ^>c:\output.txt`  
    正在执行的命令的当前目录是 systemroot 文件夹。
-   更改系统时间  
    如果您计划要运行与的命令后发生更改时计算机的系统时间**处**，同步**处**计划程序，并通过键入的修改后的系统时间**在**而无需命令行选项。
-   存储命令  
    已计划的命令存储在注册表中。 因此，不丢失重新启动的计划服务的计划的任务。
-   连接到网络驱动器  
    请不要用于访问网络的计划作业的重定向的驱动器。 计划服务可能无法再访问重定向的驱动器，或重定向的驱动器可能不会出现，如果在计划的任务运行的时登录不同的用户。 相反，对于计划作业中使用 UNC 路径。 例如：  
    `at 1:00pm my_backup \\\server\share`  
    不使用以下语法，其中**x:** 是由用户建立的连接：  
    `at 1:00pm my_backup x:`  
    如果您计划**处**使用驱动器号来连接到共享目录的命令包括**在**命令完成后使用驱动器断开连接的驱动器。 如果驱动器未断开连接，分配的驱动器号不在命令提示符下可用。
-   停止在 72 小时后的任务  
    默认情况下，任务使用调度**在**72 小时后的命令停止。 可以修改注册表来更改此默认值。
    1.  启动注册表编辑器 (regedit.exe)。
    2.  找到并单击注册表中的以下项：**HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Schedule**
    3.  在编辑菜单上单击添加值，并添加以下注册表值：值名称： atTaskMaxHours 数据类型： reg_DWOrd 基数：十进制值数据：0. 值的数据字段中的 0 值表示没有限制，不会停止。 从 1 到 99 之间的值表示小时的数。
**警告**
-   不正确地编辑注册表可能会对系统造成严重损坏。 在更改注册表之前，应备份计算机上任何有价值的数据。
-   任务计划程序和**在**命令  
    可以使用任务计划程序文件夹以查看或修改已通过使用任务的设置**在**命令。 当你安排任务使用**处**命令，该任务列出在计划的任务文件夹中，使用如下所示的名称：**at3478**。 但是，如果您修改在通过计划的任务文件夹的任务，它将升级到普通的计划任务。 任务已不再对可见**在**命令，并在帐户设置不再适用于它。 显式必须为任务输入用户帐户和密码。
## <a name="examples"></a>示例
若要显示的市场营销服务器中计划的命令的列表，请键入：

`at \\marketing`

若要了解有关具有标识数字 3 Corp 服务器上的命令的详细信息，请键入：

`at \\corp 3`

若要计划在上午 8:00 Corp 服务器上运行 net share 命令 并重定向到中的报表的共享的目录，并 Corp.txt 文件类型的维护服务器的列表：

`at \\corp 08:00 cmd /c "net share reports=d:\marketing\reports >> \\maintenance\reports\corp.txt"`

要备份到磁带驱动器在午夜每隔五天的市场营销服务器的硬盘驱动器，创建的批处理程序，名为 Archive.cmd，其中包含备份命令，然后计划要运行的批处理程序，请键入：

`at \\marketing 00:00 /every:5,10,15,20,25,30 archive`

若要取消计划的当前服务器上的所有命令，请清除**在**计划信息，如下所示：

`at /delete`

若要运行不是可执行文件 (即，.exe) 文件的命令，位于与命令**cmd /c**加载 Cmd.exe，如下所示：

`cmd /c dir > c:\test.out`