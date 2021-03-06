---
title: 导出-映像
description: 用于导出的 Windows 命令主题，该主题将现有映像从映像存储导出到另一个 Windows 映像（.wim）文件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a9b8b467-0f2d-4754-8998-55503a262778
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f3e45c254cc6782a61828fa12e479110836e5de5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831420"
---
# <a name="export-image"></a>导出-映像

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

将映像存储中的现有映像导出到另一个 Windows 映像（.wim）文件。

## <a name="syntax"></a>语法
对于启动映像：
```
wdsutil [Options] /Export-Imagmedia:<Image name> [/Server:<Server name>]
   mediatype:Boot /Architecture:{x86 | ia64 | x64} [/Filename:<File name>]
     /DestinationImage
         /Filepath:<File path and name>
         [/Name:<Name>]
         [/Description:<Description>]
     [/Overwrite:{Yes | No}]
```
对于安装映像：
```
wdsutil [Options] /Export-Imagmedia:<Image name> [/Server:<Server name>]
   mediatype:InstallmediaGroup:<Image group name>]
     [/Filename:<File name>]
     /DestinationImage
         /Filepath:<File path and name>
         [/Name:<Name>]
         [/Description:<Description>]
     [/Overwrite:{Yes | No | append}]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
媒体：<Image name>|指定要导出的映像的名称。|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
媒体： {Boot &#124; Install}|指定要导出的图像的类型。|
|\mediaGroup：<Image group name>]|指定包含要导出的映像的映像组。 如果未指定映像组名称，并且服务器上只存在一个映像组，则默认情况下将使用该映像组。 如果服务器上存在多个映像组，则必须指定映像组。|
|/Architecture： {x86 &#124; ia64 &#124; x64}|指定要导出的映像的体系结构。 由于不同体系结构中的启动映像可能具有相同的映像名称，因此指定体系结构值可确保返回正确的映像。|
|[/Filename：<Filename>]|如果无法按名称唯一地标识图像，则必须指定文件名。|
|/DestinationImage|指定目标映像的设置。 可以使用以下选项指定这些设置：<p>-/Filepath：<File path and name>-指定新映像的完整文件路径。<br />-[/Name：<Name>]-设置图像的显示名称。 如果未指定名称，则使用源映像的显示名称。<br />-[/Description： <Description>]-设置映像的说明。|
|[/Overwrite： {Yes &#124; No &#124; append}]|确定当/Filepath. 中已存在具有该名称的现有文件时，是否将覆盖在 **/DestinationImage**选项中指定的文件<p>-    **"是"** 将导致覆盖现有文件。<br />-   **no** （默认选项），如果已存在同名的文件，则会出现错误。<br />-   **追加**导致生成的映像作为新映像追加到现有 .wim 文件中。|
## <a name="examples"></a><a name=BKMK_examples></a>示例
若要导出启动映像，请键入下列内容之一：
```
wdsutil /Export-Imagmedia:WinPE boot imagemediatype:Boot /Architecture:x86 /DestinationImage /Filepath:C:\temp\boot.wim
wdsutil /verbose /Progress /Export-Imagmedia:WinPE boot image /Server:MyWDSServemediatype:Boot /Architecture:x64 /Filename:boot.wim 
/DestinationImage /Filepath:\\Server\Share\ExportImage.wim /Name:Exported WinPE image /Description:WinPE Image from WDS server /Overwrite:Yes
```
若要导出安装映像，请键入下列内容之一：
```
wdsutil /Export-Imagmedia:Windows Vista with Officemediatype:Install /DestinationImage /Filepath:C:\Temp\Install.wim
wdsutil /verbose /Progress /Export-Imagmedia:Windows Vista with Office /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 
/Filename:install.wim /DestinationImage /Filepath:\\server\share\export.wim /Name:Exported Windows image /Description:Windows Vista image from WDS server /Overwrite:append
```
## <a name="additional-references"></a>其他参考
- [命令行语法键](command-line-syntax-key.md)
[使用 "添加图像"](using-the-add-image-command.md)命令
使用 "[复制映像"](using-the-copy-image-command.md)命令
使用 " [" 命令的](using-the-remove-image-command.md)"获取
[映像](using-the-get-image-command.md)" 命令，
[使用 "替换图像" 命令](using-the-replace-image-command.md)
子命令[：设置-图像](subcommand-set-image.md)
