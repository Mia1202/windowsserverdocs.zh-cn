---
title: bcdedit
description: 适用于**bcdedit**的 Windows 命令主题，用于创建新存储、修改现有存储以及添加启动菜单参数。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ab2da47d-3aac-44a0-b7fd-bd9561d61553
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/27/2018
ms.openlocfilehash: f5bd39fa29dc99bba0d3600fc8609a355ffe540c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851070"
---
# <a name="bcdedit"></a>bcdedit

引导配置数据（BCD）文件提供用于描述启动应用程序和启动应用程序设置的存储。 存储区中的对象和元素有效地取代了 Boot.ini。

BCDEdit 是用于管理 BCD 存储的命令行工具。 它可用于多种用途，包括创建新存储、修改现有存储、添加启动菜单参数等等。 BCDEdit 在较早版本的 Windows 上本质上与 Bootcfg 的作用相同，但有两个主要改进：

- 公开比 Bootcfg 更广泛的启动参数。

- 提高了脚本支持。

> [!NOTE]
> 需要管理权限才能使用 BCDEdit 来修改 BCD。

BCDEdit 是用于编辑 Windows Vista 和更高版本 Windows 的启动配置的主要工具。 它包含在%WINDIR%\System32 文件夹中的 Windows Vista 分发中。

BCDEdit 仅限标准数据类型，其设计用途主要是对 BCD 执行单一的常见更改。 对于更复杂的操作或非标准的数据类型，请考虑使用 BCD Windows Management Instrumentation （WMI）应用程序编程接口（API）来创建功能强大且灵活的自定义工具。

## <a name="syntax"></a>语法

```
BCDEdit /Command [<Argument1>] [<Argument2>] ...
```

### <a name="parameters"></a>参数

### <a name="general-bcdedit-command-line-option"></a>常规 BCDEdit 命令行选项

| 选项 | 说明 |
| ------ | ----------- |
| /? | 显示 BCDEdit 命令列表。 如果不使用参数运行此命令，则会显示可用命令的摘要。 若要显示特定命令的详细帮助，请运行**bcdedit/？** `<command>`，其中 `<command>` 是要搜索的命令的名称。 例如， **bcdedit/？ createstore**显示 createstore 命令的详细帮助。 |

#### <a name="parameters-that-operate-on-a-store"></a>在存储区上操作的参数

| 选项 | 说明 |
| ------ | ----------- |
| /createstore | 创建新的空引导配置数据存储。 创建的存储不是系统存储。 |
| /export | 将系统存储的内容导出到文件中。 稍后可以使用此文件来还原系统存储的状态。 此命令仅对系统存储有效。 |
| /import | 使用以前使用 **/export**选项生成的备份数据文件还原系统存储的状态。 此命令会在进行导入之前删除系统存储中的任何现有项。 此命令仅对系统存储有效。 |
| /store | 此选项可与大多数 BCDedit 命令配合使用来指定要使用的存储。 如果未指定此选项，则 BCDEdit 会对系统存储进行操作。 自行运行**bcdedit/store**命令等效于运行**bcdedit/enum active**命令。 |

#### <a name="parameters-that-operate-on-entries-in-a-store"></a>对存储中的项进行操作的参数

| 参数 | 说明 |
| ------ | ----------- |
| /copy | 在同一系统存储中创建指定引导项的副本。 |
| /create | 在引导配置数据存储中创建新项。 如果指定了众所周知的标识符，则不能指定 **/application**、 **/inherit**和 **/device**参数。 如果未指定标识符或未指定标识符，则必须指定 **/application**、 **/inherit**或 **/device**选项。 |
| /delete | 从指定的项中删除一个元素。 |

#### <a name="parameters-that-operate-on-entry-options"></a>操作项选项的参数

| 参数 | 说明 |
| ------ | ----------- |
| /deletevalue | 从引导项中删除指定的元素。 |
| /set | 设置项选项值。 |

#### <a name="parameters-that-control-output"></a>控制输出的参数

| 参数 | 说明 |
| ------ | ----------- |
| /enum | 列出存储中的项。 **/Enum**选项是 BCEdit 的默认值，因此，运行不带参数的**bcdedit**命令等效于运行**bcdedit/enum active**命令。 |
| /v | 详细模式。 通常，任何已知的项标识符均由其易记的速记形式表示。 将 **/v**指定为命令行选项，将全部标识符全部显示。 自行运行**bcdedit/v**命令等效于运行**bcdedit/enum active/v**命令。 |

#### <a name="parameters-that-control-the-boot-manager"></a>控制启动管理器的参数

| 参数 | 说明 |
| ------ | ----------- |
| /bootsequence | 指定用于下一次引导的一次性显示顺序。 此命令类似于 **/displayorder**选项，只不过它仅在计算机下次启动时使用。 之后，计算机会恢复为原始显示顺序。 |
| /default | 指定在超时过期时引导管理器选择的默认项。 |
| /displayorder | 指定启动管理器向用户显示启动参数时使用的显示顺序。 |
| /timeout | 指定在引导管理器选择默认项之前等待的时间（以秒为单位）。 |
| /toolsdisplayorder | 指定在显示 "**工具**" 菜单时要使用的启动管理器的显示顺序。 |

#### <a name="parameters-that-control-emergency-management-services"></a>控制紧急管理服务的参数

| 参数 | 说明 |
| ------ | ----------- |
| /bootems | 启用或禁用指定项的紧急管理服务 (EMS)。 |
| /ems | 启用或禁用指定操作系统引导项的 EMS。 |
| /emssettings | 设置计算机的全局 EMS 设置。 **/emssettings**不会为任何特定的启动条目启用或禁用 EMS。 |

#### <a name="parameters-that-control-debugging"></a>控制调试的参数

| 参数 | 说明 |
| ------ | ----------- |
| /bootdebug | 启用或禁用指定引导项的引导调试程序。 此命令适用于任何引导项，但仅对引导应用程序有效。 |
| /dbgsettings | 指定或显示系统的全局调试程序设置。 此命令不 enablepose。 若要设置单个全局调试器设置，请使用**bcdedit/set** `<dbgsettings> <type> <value>` 命令。 |
| /debug | 启用或禁用指定引导项的内核调试程序。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

有关如何使用 BCDEdit 的示例，请参阅[Bcdedit Options 参考](https://docs.microsoft.com/windows-hardware/drivers/devtest/bcd-boot-options-reference)文章。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
