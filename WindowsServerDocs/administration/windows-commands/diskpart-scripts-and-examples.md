---
title: Diskpart 脚本和示例
description: Windows 命令主题，适用于 Diskpart 脚本和示例，用于自动执行与磁盘相关的任务，例如创建卷或将磁盘转换为动态磁盘。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 319c0795-11df-47c8-b203-eadb0577ee0d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bdfa35e8597479f32bc9bd854549cb3f74e4c0d3
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80845490"
---
# <a name="diskpart-scripts-and-examples"></a>Diskpart 脚本和示例

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

使用 Diskpart `/s` 运行自动执行与磁盘相关的任务的脚本，例如创建卷或将磁盘转换为动态磁盘。 如果是使用无人参与安装或 Sysprep（它们不支持创建除启动卷以外的卷）部署 Windows，则创建执行这些任务的脚本非常有用。  
  
-   若要创建一个 Diskpart 脚本，请创建一个包含要运行的 Diskpart 命令的文本文件，其中每行一个命令，而不是空行。 您可以使用 `rem` 启动一行，使该行成为注释。  
  
    例如，下面的脚本将擦除磁盘，然后为 Windows 恢复环境创建 300 MB 的分区：  
  
    ```  
    select disk 0  
    clean  
    convert gpt  
    create partition primary size=300  
    format quick fs=ntfs label=Windows RE tools  
    assign letter=T  
    ```  
  
-   若要运行 DiskPart 脚本，请在命令提示符下键入以下命令，其中*scriptname*是包含脚本的文本文件的名称。  
  
    ```  
    diskpart /s scriptname.txt  
    ```  
  
-   若要将 DiskPart 的脚本输出重定向到文件，请键入以下命令，其中*logfile*是 DiskPart 写入其输出的文本文件的名称。  
  
    ```  
    diskpart /s scriptname.txt > logfile.txt  
    ```  
  
> [!IMPORTANT]  
> 将**diskpart**命令用作脚本的一部分时，建议你将所有 DiskPart 操作一起作为一个 diskpart 脚本的一部分来完成。 您可以运行连续的 DiskPart 脚本，但必须在每个脚本之间至少使用15秒，才能完全关闭以前的执行，然后在后续脚本中再次运行**DiskPart**命令。 否则，连续脚本可能会运行失败。 可以通过将 `timeout /t 15` 命令添加到批处理文件中，并将其添加到你的 DiskPart 脚本，在连续的 DiskPart 脚本之间添加暂停。  
  
启动 DiskPart 时，DiskPart 版本和计算机名称将在命令提示符中显示。 默认情况下，如果在尝试执行脚本任务时，DiskPart 遇到错误，则 DiskPart 将停止处理脚本并 \(显示错误代码，除非你已指定**noerr**参数\)。 但是，无论使用的是**noerr**参数，DiskPart 始终会在遇到语法错误时返回错误。 通过**noerr**参数，你可以执行一些有用的任务，例如，使用单个脚本删除所有磁盘上的所有分区，而不考虑磁盘的总数量。  
  
## <a name="additional-references"></a>其他参考
  
- [示例：使用 Windows PE 和 DiskPart 配置 UEFI\/gpt 基于\-硬盘驱动器分区](https://technet.microsoft.com/library/hh825686.aspx)  
- [示例：使用 Windows PE 和 DiskPart 配置 BIOS\/基于 MBR\-硬盘分区](https://technet.microsoft.com/library/hh825677.aspx)  
- [Windows PowerShell 中的存储 Cmdlet](https://technet.microsoft.com/library/hh848705.aspx)  
  

