---
title: help
description: 'Windows 命令主题 * * *- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75dbf94f-d79c-45b2-9463-c06648218f4a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 29ec2da9d383985d62931ce1cee9bd4a83a0fb1d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2019
ms.locfileid: "59869588"
---
# <a name="help"></a>help

>适用于：Windows 服务器 （半年频道），Windows Server 2016 中，Windows Server 2012 R2、 Windows Server 2012

在指定的命令显示可用的命令或详细的帮助信息的列表。  
  
  
  
## <a name="syntax"></a>语法  
  
```  
help [<command>]  
```  
  
## <a name="parameters"></a>Parameters  
  
|参数|描述|  
|-------|--------|  
|<command>|指定要显示其详细的帮助信息的命令。|  
  
## <a name="remarks"></a>备注  
  
-   如果未不指定任何命令，**帮助**将显示所有可能的命令。  
  
## <a name="BKMK_examples"></a>示例  
若要显示的 DiskPart 中可用的所有命令列表，请键入：  
  
```  
help  
```  
  
若要显示有关如何使用详细的帮助信息**创建主分区**类型 DiskPart 命令：  
  
```  
help create partition primary  
```  
  
#### <a name="additional-references"></a>其他参考  
[命令行语法解答](command-line-syntax-key.md)  
  

  
