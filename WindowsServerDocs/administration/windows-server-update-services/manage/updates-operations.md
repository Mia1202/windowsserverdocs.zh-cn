---
title: 更新操作
description: Windows Server Update Service （WSUS）主题-如何管理更新，包括审批过程
ms.prod: windows-server
ms.technology: manage-wsus
ms.topic: article
ms.assetid: 4cb7ff54-3014-4e91-842a-a7b831ea59ff
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 327bff2e678e278dcba05ce1df807dc3842a56cd
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80828490"
---
# <a name="updates-operations"></a>更新操作

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

更新已同步到 WSUS 服务器后，会自动扫描这些更新以与服务器的客户端计算机相关。 但是，必须在将更新部署到网络上的计算机之前批准更新。 批准更新时，你实质上是告诉 WSUS 要如何处理它（你的选择是为新更新**安装**或**拒绝**）。 你可以为 "**所有计算机**" 组或子组审批更新。 如果你未批准某个更新，则其审批状态将保持**未批准**状态，并且你的 WSUS 服务器允许客户端评估是否需要更新。

如果 WSUS 服务器在副本模式下运行，则将无法批准 WSUS 服务器上的更新。 有关副本模式的详细信息，请参阅[运行 WSUS 副本模式](running-wsus-replica-mode.md)。

## <a name="approving-updates"></a>批准更新
你可以为 WSUS 网络中的所有计算机或不同计算机组审批更新的安装。 批准更新后，可以执行下列一项或多项操作：

-   将此审批应用于子组（如果有）。

-   设置自动安装的截止时间。 如果选择此选项，则可以设置特定的时间和日期来安装更新，同时替代客户端计算机上的任何设置。 此外，如果想要立即批准更新（在下一次客户端计算机联系 WSUS 服务器时进行安装），则可以为截止时间指定过去的日期。

-   如果该更新支持删除，请删除安装的更新。

应牢记两个重要的注意事项：

-   首先，如果需要用户输入，则无法为更新设置自动安装的截止时间（例如，指定与更新相关的设置）。 若要确定更新是否需要用户输入，请查看**更新页面上显示的更新**的更新属性中的 "**可能请求用户输入**" 字段。 同时，在 "**批准更新**" 框中检查一条消息，指出，**所选更新需要用户输入，但不支持安装截止时间**。

-   如果 WSUS 服务器组件有更新，则在批准 WSUS 更新之前，你无法批准客户端系统的其他更新。 你将在 "批准更新" 对话框中看到此警告消息：存在尚未批准的 WSUS 更新。 在批准此更新之前，应批准 WSUS 更新。 在这种情况下，您应该单击 "WSUS 更新" 节点，并确保该视图中的所有更新都已获得批准，然后返回到 "常规" 更新。

#### <a name="to-approve-updates"></a>批准更新

1.  在 WSUS 管理控制台中，单击 "**更新**"，然后单击 "**所有更新**"。

2.  在更新列表中，选择要批准的更新，然后右键单击（或单击 "操作" 窗格），然后在 "批准更新" 对话框中，选择要为其批准更新的计算机组，然后单击其旁边的箭头。

3.  选择 "**批准安装**"，然后单击 "**批准**"。

4.  "**批准进度**" 窗口将显示完成审批的进度。 完成此过程后，将显示 "**关闭**" 按钮。 单击 **“关闭”** 。

5.  您可以选择一个截止时间，方法是右键单击该更新，选择相应的计算机组，单击其旁边的箭头，然后单击 "**截止时间**"。

    -   您可以选择标准截止时间（一周、两周、一个月），也可以单击 "**自定义**" 指定日期和时间。

    -   如果要在客户端计算机与服务器联系时立即安装更新，请单击 "**自定义**"，然后将日期和时间设置为当前日期和时间，或设置为过去的日期和时间。

#### <a name="to-approve-multiple-updates"></a>批准多个更新

1.  在 WSUS 管理控制台中，单击 "**更新**"，然后单击 "**所有更新**"。

2.  若要选择多个连续更新，请在选择 "更新" 时按**shift** 。 若要选择多个非连续更新，请在选择 "更新" 时按住**CTRL** 。

3.  右键单击所选内容，然后单击 "**批准**"。 此时将打开 "**批准更新**" 对话框，其中的 "**审批状态**" 设置为 "**保留现有审批**"，禁用 "**确定"** 按钮。

4.  你可以更改单个组的审批，但这样做不会影响儿童批准。 选择要为其更改审批的组，然后单击其左侧的箭头。 在快捷菜单中，单击 "**批准安装**"。

5.  所选组的审批将更改为 "**安装**"。 如果有任何子组，则其审批仍保持**现有审批**状态。 若要更改子组的批准，请单击该组，然后单击其左侧的箭头。 在快捷菜单中，单击 "**应用到子级**"。

6.  若要设置特定的子，使其从父项继承其所有批准，请单击该子级，并单击其左侧的箭头。 在快捷菜单中，单击 "与**父项相同**"。 如果将某一子级设置为继承审批，但不更改父审批，则该子级将继承父级的现有批准。

7.  如果要更改所有子项的批准行为，请批准**所有计算机**，然后选择 "**应用到子项**"。

8.  设置所有审批后，请单击 **"确定"** 。 "**批准进度**" 窗口将显示完成审批的进度。 完成此过程后，"**关闭**" 按钮将可用。 单击 **“关闭”** 。

## <a name="declining-updates"></a>拒绝更新
如果选择此选项，将从可用更新的默认列表中删除更新，并且 WSUS 服务器将不会向客户端提供用于评估或安装的更新。 可以通过选择一组更新或一组更新来访问此选项，然后右键单击或转到 "操作" 窗格。 仅当在 "**查看**" 下指定了更新列表的筛选器时，"更新"**列表中才**会显示拒绝的更新。

#### <a name="to-decline-updates"></a>拒绝更新

1.  在 WSUS 管理控制台中，单击 "**更新**"，然后单击 "**所有更新**"。

2.  在更新列表中，选择要拒绝的一个或多个更新。

3.  选择 "**拒绝**"，然后在确认消息中单击 **"是"** 。

## <a name="cleaning-up-declined-updates"></a>清除拒绝的更新
拒绝的更新继续使用某些 WSUS 服务器资源。 你应运行 "服务器清理向导" 以从 WSUS 数据库中删除拒绝的更新。 有关更多详细信息，请参阅["服务器清理向导"](the-server-cleanup-wizard.md)。

## <a name="reinstating-declined-updates"></a>复原拒绝的更新
拒绝更新后，你仍然可以恢复它。

#### <a name="to-reinstate-declined-updates"></a>恢复拒绝的更新

1.  在 WSUS 管理控制台中，单击 "**更新**"，然后单击 "**所有更新**"。

2.  将**审批**更改为已**拒绝**，并单击 "**刷新**"。 拒绝的更新的列表已加载。

3.  在更新列表中，选择一个或多个要恢复的已拒绝更新。

4.  若要恢复特定的更新，请右键单击该更新，然后选择 "**批准**"。 在 "**批准更新**" 对话框中，单击 **"确定"** 以重新应用默认的 "未批准批准" 状态。 更新将在列表中显示为 "**未批准**"，而不是 "已拒绝"。

使用 WSUS 服务器清理向导清除拒绝的更新后，它将从 WSUS 服务器中删除，并且将不再显示在 "所有更新" 视图中。 你可以重新导入已拒绝的，并从 Microsoft 更新目录中清除更新。 有关其他信息，请参阅[WSUS 和目录站点](wsus-and-the-catalog-site.md)。

## <a name="change-an-approved-update-to-not-approved"></a>将批准的更新更改为未批准
如果更新已获得批准，此时你决定不安装它，而是想要将其保存一段时间，则可以将更新更改为 "未批准" 状态。 这意味着更新将保留在可用更新的默认列表中，并将报告客户端符合性，但不会安装在客户端上。

#### <a name="to-change-an-update-from-approved-to-not-approved"></a>将更新从已批准改为未批准

1.  在 WSUS 管理控制台中，单击 "**更新**"，然后单击 "**所有更新**"。

2.  在更新列表中，选择要更改为 "未批准" 的一个或多个已批准的更新。

3.  在快捷菜单或 "**操作**" 窗格中，选择 "**未批准**"，然后在确认消息中单击 **"是"** 。

## <a name="approving-updates-for-removal"></a>批准要删除的更新
你可以批准要删除的更新（即卸载已安装的更新）。 仅当已安装更新并支持删除时，此选项才可用。 你可以指定要卸载更新的截止时间，或者，如果你想要立即删除更新（下一次客户端计算机与 WSUS 服务器联系），则指定截止日期。

必须指出的是，并非所有更新都支持删除。 可以通过选择单个更新并查看**详细信息**窗格来查看更新是否支持删除。 在 "**其他详细信息**" 下，会看到 "**可移动**" 类别。 如果无法通过 WSUS 删除更新，则在某些情况下，可以使用控制面板中的 **"** **添加或删除程序**" 将其删除。

#### <a name="to-approve-updates-for-removal"></a>批准要删除的更新

1.  在 WSUS 管理控制台中，单击 "**更新**"，然后单击 "**所有更新**"。

2.  在更新列表中，选择一个或多个要为删除批准的更新，然后右键单击它们（或中转到 "**操作**" 窗格）。

3.  在 "**批准更新**" 对话框中，选择要从中删除更新的计算机组，然后单击其旁边的箭头。

4.  选择 "**已批准删除**"，然后单击 "**删除**" 按钮。

5.  完成删除审批后，可以选择一个截止时间，方法是右键单击 "更新"，选择相应的计算机组，然后单击它旁边的箭头。 然后选择 "**截止时间**"。 您可以选择标准截止时间（一周、两周、一个月），也可以单击 "**自定义**" 选择特定日期和时间。

6.  如果要在客户端计算机与服务器联系时立即删除更新，请单击 "**自定义**"，并设置过去的日期。

## <a name="approving-updates-automatically"></a>自动批准更新
你可以将 WSUS 服务器配置为自动批准某些更新。 你还可以指定在现有更新可用时自动批准对现有更新的修订。 默认情况下，此选项处于选中状态。 修订版本是已对其进行更改（例如，它可能已过期或其适用性规则可能已更改）的更新版本。 如果未选择自动批准修改后的更新版本，WSUS 将使用较旧的版本，并且你必须手动批准更新修订版本。

你可以创建在同步过程中 WSUS 服务器将自动应用的规则。 通过更新分类、产品和计算机组来指定你想要自动批准的更新。 这仅适用于新的更新，而不是经过修改的更新。 你还可以指定更新批准截止时间，这会在已批准的更新截止时间安装之前设置天数和特定的时间。 这些设置在 "**选项**" 窗格中的 "**自动批准**" 下提供。

#### <a name="to-automatically-approve-updates"></a>自动批准更新

1.  在 WSUS 管理控制台中，单击 "**选项**"，然后单击 "**自动批准**"。

2.  在“更新规则”中，单击“新规则”。

3.  在 "**添加规则**" 对话框中，在 "**步骤1：选择属性**" 下，选择是**在更新属于特定分类时**，还是**在特定产品**（或两者）中作为条件使用更新。 还可以选择是否为审批**设置截止时间**。

4.  在 "**步骤2：编辑属性**" 中，单击带下划线的属性，选择需要自动批准的分类、产品和计算机组（如果适用）。 还可以选择 "更新审批截止日期" 和 "时间"。

5.  在 "**步骤3：指定名称" 框**中，键入规则的唯一名称。

6.  单击“确定”。

自动批准规则不适用于需要在服务器上尚未接受最终用户许可协议（EULA）的更新。 如果你发现应用自动批准规则不会导致所有相关更新获得批准，你应手动批准这些更新。

## <a name="automatically-approving-revisions-to-updates-and-declining-expired-updates"></a>自动批准更新修订并拒绝过期更新
"选项" 窗格的 "自动审批" 部分包含一个默认选项，可自动批准批准的更新的修订。 你还可以将 WSUS 服务器设置为自动拒绝过期的更新。 如果选择不自动批准修改后的更新版本，WSUS 服务器将使用较旧的版本，你必须手动批准更新修订版本。

> [!NOTE]
> 修订版本是已更改的更新版本（例如，它可能已过期或已更新适用性规则）。

#### <a name="to-automatically-approve-revisions-to-updates-and-decline-expired-updates"></a>自动批准更新修订并拒绝过期更新

1.  在 WSUS 管理控制台中，单击 "**选项**"，然后单击 "**自动批准**"。

2.  在 "**高级**" 选项卡上，确保选择了 "**自动批准更新的新修订版本**"，并在**新修订版导致用户过期时自动拒绝更新**。

3.  单击“确定”。

    > [!NOTE]
    > 保留这些选项的默认值，可在 WSUS 网络上保持良好的性能。 如果你不希望自动拒绝过期的更新，则应确保定期拒绝这些更新。

## <a name="automatically-declining-superseded-updates"></a>自动拒绝被取代的更新
如果批准的新更新取代了自动批准的现有更新，则在安装更新的更新后，被取代的更新将不适用于计算机或设备。 可以在 WSUS 控制台中验证更新不适用于所有计算机。 如果是这种情况，则可以安全地拒绝更新。 此外，在运行 WSUS 服务器清理向导时，可能会自动拒绝更新。

若要搜索被取代的更新，你可以在 "所有更新" 视图中选择被取代标志列，然后对该列进行排序。 将有四个组：

-   从未取代的更新（空白图标）。

-   已被取代，但从未取代的更新（底部有一个蓝色方块的图标）。

-   已被取代并被取代的更新（中间有一个蓝色正方形的图标）。

-   已取代其他更新的更新（顶部有蓝色方块的图标）。

Windows Server Update Services 中没有功能可在更新更新时自动拒绝被取代的更新。 建议先将审批设置为 "未批准"，然后在满足所有相关条件后，使用 "服务器清理向导" 自动拒绝更新。 有关详细信息，请参阅：[服务器清理向导](the-server-cleanup-wizard.md)。

## <a name="approving-superseding-or-superseded-updates"></a>批准取代或取代更新
通常，取代其他更新的更新会执行以下一项或多项操作：

-   增强、改进或添加到由以前发布的一个或多个更新提供的修补程序。

-   提高了更新文件包的效率，如果更新已获批准，则会在客户端计算机上安装该更新。 例如，被取代的更新可能包含不再与修补程序或新更新支持的操作系统相关的文件，因此这些文件未包含在取代更新的文件包中。

-   更新操作系统的较新版本。 另外，请务必注意，取代更新可能不支持早期版本的操作系统。

相反，另一个更新取代的更新会执行以下操作：

-   修复了类似于取代它的更新的问题。 但是，取代该更新的更新可能会增强被取代更新提供的修补程序。

-   更新早期版本的操作系统。 在某些情况下，取代更新将不再更新这些版本的操作系统。

在单个更新的详细信息窗格中，信息图标和顶部的消息表示它将取代或被另一个更新取代。 此外，还可以通过在 "**属性**" 的 "**其他详细信息**" 部分中查看此**更新和**此更新条目所**取代**的更新，来确定哪些更新取代或被更新取代。 更新的详细信息窗格将显示在更新列表下。

WSUS 不会自动拒绝被取代的更新，建议您不要假设应该拒绝被取代的更新，以支持新的取代更新。 在拒绝被取代的更新之前，请确保你的任何客户端计算机不再需要此更新。 下面是可能需要安装被取代更新的方案示例：

-   如果取代更新仅支持较新版本的操作系统，而某些客户端计算机运行的是早期版本的操作系统。

-   如果取代更新的适用性比它取代的更新具有更多的受限制，这将使其不适合于某些客户端计算机。

-   如果因新更改而导致更新不再取代以前发布的更新，则为。 可以通过每个版本的更改，更新不再取代以前在早期版本中所取代的更新。 在这种情况下，你仍会看到一条有关被取代的更新的消息，即使取代此更新的更新已被不是的更新所取代。


