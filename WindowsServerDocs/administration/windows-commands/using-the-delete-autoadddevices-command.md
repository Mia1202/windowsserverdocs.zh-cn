---
title: 删除-AutoaddDevices
description: AutoaddDevices 的 Windows 命令主题，用于删除在自动添加数据库中挂起、拒绝或批准的计算机。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8dcaca6a-212e-4c36-98e3-00938eef6b9c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 29df0bd92859e9ee0b5b5bedfbd2e66173059cb5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831660"
---
# <a name="delete-autoadddevices"></a>删除-AutoaddDevices

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

从自动添加数据库中删除挂起、拒绝或批准的计算机。 此数据库将有关这些计算机的信息存储在服务器上。

## <a name="syntax"></a>语法
```
wdsutil /delete-AutoaddDevices [/Server:<Server name>] /Devicetype:{PendingDevices | RejectedDevices |ApprovedDevices}
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
|/Devicetype： {PendingDevices &#124; RejectedDevices &#124;ApprovedDevices}|指定要从数据库中删除的计算机的类型。 这可以是以下三种类型之一：<p>-   **PendingDevices**返回数据库中状态为 "挂起" 的所有计算机。<br />-   **RejectedDevices**返回数据库中状态为 "已拒绝" 的所有计算机。<br />-   **ApprovedDevices**将返回状态为 "已批准" 的所有计算机。|
## <a name="examples"></a><a name=BKMK_examples></a>示例
若要删除所有拒绝的计算机，请键入：
```
wdsutil /delete-AutoaddDevices /Devicetype:RejectedDevices
```
若要删除所有批准的计算机，请键入：
```
wdsutil /verbose /delete-AutoaddDevices /Server:MyWDSServer /Devicetype:ApprovedDevices
```
## <a name="additional-references"></a>其他参考
- 使用[AutoaddDevices 命令](using-the-approve-autoadddevices-command.md)的[命令行语法键](command-line-syntax-key.md)

使用[AutoaddDevices 命令](using-the-reject-autoadddevices-command.md)
使用[AutoaddDevices 命令](using-the-get-autoadddevices-command.md)
