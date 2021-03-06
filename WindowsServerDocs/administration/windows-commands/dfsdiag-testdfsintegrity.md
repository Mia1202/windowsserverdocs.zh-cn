---
title: dfsdiag TestDFSIntegrity
description: 适用于**Dfsdiag TestDFSIntegrity**的 Windows 命令主题，用于检查分布式文件系统（DFS）命名空间的完整性。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 173ee832-26e1-4ec8-a23a-38a7d6229ac3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 714b79369898338a4e4a6e4fad8487709ab4fc60
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846270"
---
# <a name="dfsdiag-testdfsintegrity"></a>dfsdiag TestDFSIntegrity

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

通过执行以下测试检查分布式文件系统（DFS）命名空间的完整性：

- 检查 DFS 元数据是否已损坏或域控制器之间存在不一致。

- 验证基于访问权限的枚举的配置，以确保 DFS 元数据和命名空间服务器共享之间的一致性。

- 检测与文件夹目标重叠的重叠 DFS 文件夹（链接）、重复文件夹和文件夹。

## <a name="syntax"></a>语法

```
dfsdiag /TestDFSIntegrity /DFSRoot: <DFS root path> [/Recurse] [/Full]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
|-------|--------|
| /DFSRoot： `<DFS root path>`| 要诊断的 DFS 命名空间。 |
| /Recurse | 执行包括命名空间 interlinks 的测试。 |
| /Full | 验证共享和 NTFS Acl 的一致性以及所有文件夹目标上的客户端配置。 它还会验证是否已设置联机属性。 |

## <a name="examples"></a><a name=BKMK_Examples></a>示例

```
dfsdiag /TestDFSIntegrity /DFSRoot:\\Contoso.com\MyNamespace /Recurse /Full
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)

-   [dfsdiag](dfsdiag.md)


