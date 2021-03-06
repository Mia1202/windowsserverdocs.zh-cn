---
title: 获取-命名空间
description: 用于获取命名空间的 Windows 命令主题，其中显示了有关自定义命名空间的信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ea641bab-e97b-4909-918e-447730027dc1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 58e84ec5c82ea3c2663b38bd2e53f65f2cf47519
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830880"
---
# <a name="get-namespace"></a>获取-命名空间

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

显示有关自定义命名空间的信息。

## <a name="syntax"></a>语法
Windows Server 2008 R2
```
wdsutil /Get-Namespace /Namespace:<Namespace name> [/Server:<Server name>] [/Show:Clients]
```
Windows Server 2008 R2
```
wdsutil /Get-Namespace /Namespace:<Namespace name> [/Server:<Server name>] [/details:Clients]
```
### <a name="parameters"></a>参数

|               参数               |                                                                                                                                                                                         说明                                                                                                                                                                                          |
|---------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      /Namespace：<Namespace name>      | 指定命名空间的名称。 请注意，这不是友好名称，并且必须是唯一的。<p>-Deployment Server：命名空间名称的语法为/Namspace： WDS：<ImageGroup>/<ImageName>/<Index>。 例如： **WDS： ImageGroup1/install/1**<br />-传输服务器：此值应与在服务器上创建命名空间时提供的名称匹配。 |
|        [/Server：<Server name>]        |                                                                                                             指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，则使用本地服务器。                                                                                                              |
| [/Show： Clients] 或 [/details： Clients] |                                                                                                                                                  显示有关连接到指定命名空间的客户端计算机的信息。                                                                                                                                                  |

## <a name="examples"></a><a name=BKMK_examples></a>示例
若要查看有关命名空间的信息，请键入：
```
wdsutil /Get-Namespace /Namespace:Custom Auto 1
```
若要查看有关命名空间和连接的客户端的信息，请键入下列内容之一：
- Windows Server 2008： `wdsutil /Get-Namespace /Server:MyWDSServer /Namespace:Custom Auto 1 /Show:Clients`
- Windows Server 2008 R2： `wdsutil /Get-Namespace /Server:MyWDSServer /Namespace:Custom Auto 1 /details:Clients`
  ## <a name="additional-references"></a>其他参考
  - [命令行语法键](command-line-syntax-key.md)
  [使用 AllNamespaces 命令](using-the-get-allnamespaces-command.md)
  使用[新的命名空间](using-the-new-namespace-command.md)命令
  [使用删除命名空间](using-the-remove-namespace-command.md)命令
  [子](subcommand-start-namespace.md)命名空间
