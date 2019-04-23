---
title: 了解功能
description: 本主题定义系统 Insights 中的功能的概念并引入了 Windows Server 2019 中提供的默认功能。
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: system-insights
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ''
author: gawatu
ms.author: gawatu
manager: mallikarjun.chadalapaka
ms.date: 6/05/2018
ms.openlocfilehash: 21932a3e45d7fc6711400eb30c63c3412bbc116e
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2019
ms.locfileid: "59830968"
---
# <a name="understanding-capabilities"></a>了解功能

>适用于：Windows Server 2019

本主题定义系统 Insights 中的功能的概念并引入了 Windows Server 2019 中提供的默认功能。 

本主题还介绍数据源、 预测时间线和预测状态用于默认功能。 

## <a name="capability-overview"></a>功能概述
系统 Insights 功能是机器学习或分析系统数据，以有助于为你提供的统计信息模型增加深入部署的运行状况。 系统 Insights 引入了一组初始的默认功能，并可动态地添加新功能，而无需将操作系统更新。 

>[!NOTE]
>详细的文档说明如何创建、 添加和更新功能是可用[此处](adding-and-developing-capabilities.md)，并[管理的功能文档](managing-capabilities.md)提供相关信息的更多高级信息功能。

此外，每个功能在本地运行在 Windows Server 实例，并且可以分别管理每个功能。

### <a name="capability-outputs"></a>功能输出
当调用一项功能时，它提供了帮助说明其分析或预测的结果的输出。 每个输出必须包含**状态**和一个**状态说明**来描述该预测和每个结果可以根据需要包含特定于功能的数据与预测关联。 **状态说明**可帮助提供有关上下文解释**状态**，并功能报告或者**确定**，**警告**，或**严重**状态。 此外，可以使用一种功能**错误**或**None**如果不进行任何预测的状态。 在一起，下面是功能状态和及其基本含义： 

- **确定**-一切看上去正常。
- **警告**-没有立即关注必需的但您应该看。 
- **关键**-应该很快就请参阅。 
- **错误**-未知的问题导致失败的功能。 
- **无**-不进行任何预测的。 这可能是由于缺乏数据或任何其他特定于功能的原因不进行预测。 

此外，在结果中包含的任何特定于功能的数据将放在用户可访问的 JSON 文件和文件路径[可以使用 PowerShell 查找](https://docs.microsoft.com/windows-server/manage/system-insights/managing-capabilities#retrieving-capability-results)。 

## <a name="default-capabilities"></a>默认功能
在 Windows Server 2019 系统 Insights 引入侧重于容量预测的四个默认功能：

- **CPU 容量预测**-预测 CPU 使用情况。 
- **网络容量预测**-预测网络为每个网络适配器的使用情况。 
- **总存储空间使用量预测**-预测在所有本地驱动器的总存储消耗。 
- **卷消耗预测**-预测每个卷的存储消耗情况。

每个功能分析过去的历史数据来预测将来的使用情况，并**所有的预测功能旨在预测长期趋势而不是短期行为**，正确帮助管理员预配硬件并调整其工作负荷以避免将来资源争用。 因为这些功能的重点放在长期使用情况，这些功能将分析每日数据。 

### <a name="forecasting-model"></a>预测模型
默认功能使用预测模型来预测将来的使用情况，并针对每个预测模型训练，则本地计算机的数据。 此模型旨在帮助检测更长的术语趋势，并重新训练每个 Windows Server 实例上启用的功能，以适应特定的行为和每台计算机的使用情况的细微差别。

>[!NOTE]
>确定哪种类型的使用模型，需要使用包含成千上万的计算机的数据集的多个模型的测试。 分析和调整这些模型之后, 我们决定使用自动回归的预测模型，因为它不需要太多时间来训练时生成非常准确且直观地直观的预测。 此模型中，不过，需要三周的定型数据，因此每个功能使用基本的线性趋势，直到三周的数据都可用。

### <a name="forecasting-timelines"></a>预测时间线
默认功能预测特定天数将来基于为其收集数据的天数。 下表显示了这些功能的预测时间线：

| 输入的数据大小 | 预测长度 |
| --------------- | --------------- |
| 0-5 天 | 不进行任何预测。 |
| 6-180 天 | 1/3 * 输入数据的大小 |
| 180-365 天 | 60 天 | 

### <a name="forecasting-data"></a>预测数据
每个功能分析每日数据来预测将来的使用情况。 CPU、 网络、 甚至存储使用情况，但是，可以频繁地更改在一天，动态调整到在计算机上的工作负荷。 因为使用情况不是全天常量，务必正确表示单个数据点中的每日使用情况。 下表详细说明特定数据点以及如何处理数据：


| 功能名称 | 数据源 | 筛选逻辑 |
| --------------- | -------------- | ---------------- |
 卷消耗预测          | 卷的大小                    | 最大每日使用情况              
 总存储空间使用量预测   | 卷大小，磁盘大小的总和的总和              | 最大每日使用情况             
 CPU 容量预测                | % Processor Time  | 每日最大值长达 2 小时平均值   
 网络容量预测         | 字节总数/秒         | 每日最大值长达 2 小时平均值  

当评估筛选逻辑，其上方的特别注意每个功能设法将通知管理员时将来使用有意义的方式将超过可用容量 – 即使 CPU 暂时达到 100%利用率，不能 CPU 使用情况导致有意义的性能下降或资源争用。 有关 CPU 和网络，然后，应该有持续的高使用率而不是瞬间达到峰值。 平均 CPU 和网络的全天的使用情况，但是，如高 CPU 或网络使用情况的几个小时有意义的方式可能会影响关键工作负荷的性能会丢失重要使用情况信息。 每一天内的最大长达 2 小时平均可避免这些极端并仍会生成有意义的数据来分析每个功能。

有关卷和总存储使用情况，但是，存储使用情况不能超过可用容量，甚至暂时不可用，因此最大每日使用情况使用这些功能。 

### <a name="forecasting-statuses"></a>预测的状态
所有系统 Insights 功能必须都输出与每个预测相关联的状态。 每个默认功能使用以下逻辑来定义每个预测状态：
- **确定**:预测不超过可用容量。
- **警告**：预测接下来的 30 天内超出了可用容量。 
- **严重**：预测接下来 7 天内超出了可用容量。 
- **错误**：功能遇到意外错误。 
- **无**：没有足够的数据进行预测。 这可能是由于缺少数据或由于最近已不报告了任何数据。

>[!NOTE]
>如果在多个实例-例如，多个卷或网络适配器的功能预测该状态将反映所有实例之间的最严重状态。 在 Windows Admin Center 或中的每个功能的输出中包含的数据，为每个卷或网络适配器的单个状态是可见的。 有关如何分析 JSON 输出的默认功能的说明，请访问[此博客](https://aka.ms/systeminsights-mitigationscripts)。 


## <a name="see-also"></a>请参阅
若要了解有关系统 Insights 的详细信息，请参阅以下资源：

- [系统 Insights 概述](overview.md)
- [管理功能](managing-capabilities.md)
- [添加和开发功能](adding-and-developing-capabilities.md)
- [系统 Insights 常见问题](faq.md)