---
title: AllImageGroups
description: 用于 AllImageGroups 的 Windows 命令主题，它检索有关服务器上所有映像组和这些映像组中的所有映像的信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2ca06533-bcf5-4590-ac8e-263d6c9874f8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 19285422612f8be34d39e6152fcf0300e1919b8a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831321"
---
# <a name="get-allimagegroups"></a>AllImageGroups

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

检索有关服务器上的所有映像组和这些映像组中的所有映像的信息。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Get-AllImageGroups [/Server:<Server name>] [/detailed]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
|[/detailed]|返回每个图像的图像元数据。 如果未使用此参数，则默认行为是只返回每个图像的映像名称、说明和文件名。|
## <a name="examples"></a><a name=BKMK_examples></a>示例
若要查看有关映像组的信息，请键入下列内容之一：
```
wdsutil /Get-AllImageGroups
wdsutil /verbose /Get-AllImageGroups /Server:MyWDSServer /detailed
```
## <a name="additional-references"></a>其他参考
- 使用[ImageGroup 命令](using-the-add-imagegroup-command.md)的[命令行语法
密钥](command-line-syntax-key.md)
使用[ImageGroup 命令](using-the-get-imagegroup-command.md)
使用[ImageGroup 命令](using-the-remove-imagegroup-command.md)
[子命令： set-ImageGroup](subcommand-set-imagegroup.md)
