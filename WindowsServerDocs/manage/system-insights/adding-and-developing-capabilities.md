---
title: 添加和开发功能
description: 系统见解使你可以向系统见解添加新的预测功能，而无需任何操作系统更新。 这使开发人员（包括 Microsoft 和第三方）能够创建和交付新功能，以解决你关注的方案。 新功能可以指定自定义数据来收集和分析，还可以与现有的系统见解管理平面集成。
ms.prod: windows-server
ms.technology: system-insights
ms.topic: article
author: gawatu
ms.author: gawatu
manager: mallikarjun.chadalapaka
ms.date: 7/31/2018
ms.openlocfilehash: 0dd4e24197d5a8c438d70a849e435ce28792dfce
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858430"
---
# <a name="adding-and-developing-new-capabilities"></a>添加和开发新功能

>适用于：Windows Server 2019

系统见解使你可以向系统见解添加新的预测功能，而无需任何操作系统更新。 这使开发人员（包括 Microsoft 和第三方）能够创建和交付新功能，以解决你关注的方案。 

任何新功能都可与现有的 System Insights 基础结构集成并扩展该基础结构：

- 新功能可以**指定任何性能计数器或系统事件**，这些事件将被收集、在本地保留，并在被调用时返回到该功能进行分析。  
- 新功能可以**利用现有的 Windows 管理中心和 PowerShell 管理平面**。 不仅可在系统见解中发现新功能，还可以从自定义计划和更正操作中受益。 

## <a name="manage-new-capabilities"></a>管理新功能
- [了解](add-remove-update-capabilities.md)如何使用 PowerShell 添加、删除和更新功能。 

## <a name="develop-a-capability"></a>开发功能
使用以下资源来帮助你开始编写自己的自定义功能：
- [了解](data-sources.md)可以收集的数据源。
- [下载](https://www.nuget.org/packages/Microsoft.WindowsServer.SystemInsights/)System Insights NuGet 包，其中包含编写功能所需的类和接口。
- [请访问](https://aka.ms/systeminsights-api)API 文档来了解系统见解类和接口。 
- [使用](https://aka.ms/systeminsights-samplecapability)系统见解示例功能帮助您入门。 这说明了如何注册功能，如何指定要收集的数据源，以及如何开始分析系统数据。

>[!NOTE]
>这是预发布功能。 由于我们添加了新功能并合并了反馈，因此可能会发生更改。

## <a name="see-also"></a>另请参阅
若要了解有关系统见解的详细信息，请使用以下资源：

- [系统见解概述](overview.md)
- [了解功能](understanding-capabilities.md)
- [管理功能](managing-capabilities.md)
- [添加、删除和更新功能](add-remove-update-capabilities.md)
- [系统见解常见问题解答](faq.md)