---
title: Windows 桌面客户端中的新功能
description: 了解 Windows 桌面的远程桌面客户端的最新更改
ms.prod: windows-server
ms.technology: remote-desktop-services
ms.topic: article
author: heidilohr
manager: lizross
ms.author: helohr
ms.date: 04/14/2020
ms.localizationpriority: medium
ms.openlocfilehash: 016a88999b93d686faff73134a660014fd602765
ms.sourcegitcommit: 20d07170c7f3094c2fb4455f54b13ec4b102f2d7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81279693"
---
# <a name="whats-new-in-the-windows-desktop-client"></a>Windows 桌面客户端中的新功能

有关 Windows 桌面客户端的更多详细信息，可参阅 [Windows 桌面客户端入门](windowsdesktop.md)。 可在下面找到客户端的最新更新。

## <a name="latest-client-versions"></a>最新客户端版本

可以针对不同的[用户组](windowsdesktop-admin.md#configure-user-groups)来配置客户端。 下表列出了适用于每个用户组的当前版本：

|用户组 |版本  |
|-----------|---------|
|Public     |1.2.790  |
|预览体验成员    |1.2.940  |

## <a name="updates-for-version-12940"></a>针对版本 1.2.940 的更新

*发布日期：2020/04/14*

下载：[Windows 64 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4txZU)、[Windows 32 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4txZV)、[Windows ARM64](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4tM6I)

- 已为桌面连接添加了新的显示设置选项（右键单击“连接中心”上的桌面图标时提供）。
  - 现在有三个显示配置选项：  “所有显示器”、  “单个显示器”和“选择显示器”  。
  - 现在，仅当选择了某个显示配置时，才显示可用设置。
  - 在“选择显示器”模式下，有一个新的“最大化到当前显示器”  选项，可用于在不重新连接的情况下动态更改用于会话的显示器。 启用后，将会话最大化会导致在会话窗口所在的所有显示器上全屏显示该会话。
  - 对于“所有显示器”和“选择显示器”模式，我们已添加了一个新的“开窗时使用单个显示器”  选项。 此选项在你退出全屏模式时会自动将会话切换到单个显示器，并在你将窗口最大化时自动返回到多个显示器。
- 我们已将新的“显示设置”  组添加到系统菜单中，该菜单在你右键单击开窗桌面会话的标题栏时显示。 这将允许你在会话过程中动态更改某些设置。 例如，可以更改“在开窗时使用单个显示器模式”  和“最大化到当前显示器”  设置。
- 退出全屏模式时，会话窗口将返回到你首次进入全屏模式时它所在的原始位置。
- 从“关于”页重置用户数据现在会在完成后重定向到“连接中心”，而不是关闭客户端。
- 解决了选项卡导航和屏幕阅读器存在的某些辅助功能问题。
- 修复了在不同缩放系数的显示器之间拖动桌面会话窗口时的闪烁和收缩问题。
- 修复了重定向相机时出现的错误。
- 修复了多个崩溃问题以提高可靠性。

## <a name="updates-for-version-12790"></a>针对版本 1.2.790 的更新

*发布日期：2020/03/24*

下载：[Windows 64 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4siSh)、[Windows 32 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4siSi)、[Windows ARM64](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4sllb)

- 已将工作区的“更新”操作重命名为“刷新”，以与其他远程桌面客户端保持一致。
- 现在可以直接从工作区的上下文菜单刷新工作区。
- 手动刷新工作区现在可确保更新所有本地内容。
- 现在可以从“关于”页重置客户端的用户数据，无需卸载该应用。
- 还可以将 msrdcw.exe /reset 与可选参数 /f 配合使用来跳过提示，从而重置客户端的用户数据。
- 现在，导航到“关于”页时，我们会自动查找客户端更新。
- 更新了按钮的颜色以保持一致。

## <a name="updates-for-version-12675"></a>针对版本 1.2.675 的更新

*发布日期：2020/02/25*

下载：[Windows 64 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4qeak)、[Windows 32 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4qm7h)、[Windows ARM64](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4qm7g)

- 现在，如果 RDP 文件缺少签名或 signscope 属性之一已被修改，那么，连接到 Windows 虚拟桌面将被阻止。
- 当工作区为空或已删除时，连接中心将不再显示为空。
- 添加了针对断开连接消息的活动 ID 和错误代码，以改进故障排除。 可以使用 **Ctrl + C** 复制对话框消息。
- 修复了导致桌面连接设置无法检测到显示器的问题。
- 客户端更新不再自动重启电脑。
- 无窗口图标不应再出现在任务栏上。

## <a name="updates-for-version-12605"></a>针对版本 1.2.605 的更新

*发布日期：2020/01/29*

下载：[Windows 64 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4oHrD)、[Windows 32 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4oJZs)、[Windows ARM64](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4oXhD)

- 现在可以选择要用于桌面连接的显示器。 若要更改此设置，请右键单击桌面连接的图标，然后选择“设置”  。
- 修复了连接设置未显示正确的可用缩放系数的问题。
- 修复了“讲述人”无法读取在连接启动时显示的对话框的问题。
- 修复了在 Azure Active Directory 名称和 Active Directory 名称不匹配时显示错误用户名的问题。
- 修复了在未连接网络的情况下启动连接时客户端停止响应的问题。
- 修复了在附加耳机时导致客户端停止响应的问题。

## <a name="updates-for-version-12535"></a>针对版本 1.2.535 的更新

*发布日期：2019/12/04*

下载：[Windows 64 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4k7jH)、[Windows 32 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4k7jL)、[Windows ARM64](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4k27O)

- 你现在可以直接通过客户端顶部命令栏上的“更多选项”按钮访问有关更新的信息。
- 你现在可以从客户端的命令栏报告反馈。
- 现在，“反馈”选项仅在反馈中心可用的情况下显示。
- 确保在通过策略禁用通知的情况下不显示更新通知。
- 修复了妨碍某些 RDP 文件启动的问题。
- 修复了在启动客户端时发生崩溃的问题，该问题是某些持久性设置受损导致的。

## <a name="updates-for-version-12431"></a>针对版本 1.2.431 的更新

*发布日期：2019/11/12*

下载：[Windows 64 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE48kow)、[Windows 32 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE48koA)、[Windows ARM64](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE48zYj)

- 客户端的 32 位版和 ARM64 版现已提供！
- 客户端现在会保存你对连接栏所做的任何更改（例如，其位置、大小和固定状态），并跨会话应用这些更改。
- 更新的网关信息和连接状态对话框。
- 解决了已导致在 Azure Active Directory 令牌过期后尝试连接时两个凭据同时提示的问题。
- 现在，在 Windows 7 中，如果用户已保存凭据而服务器不接受该凭据时，系统会正确提示用户输入凭据。
- 重新连接时，Azure Active Directory 提示现在会显示在连接窗口的前面。
- 固定到任务栏的项现在会在源刷新过程中更新。
- 已改进在使用触控时连接中心上进行的滚动。
- 从“分辨率”下拉菜单中删除了空行。
- 在 Windows 凭据管理器中删除了不必要的条目。
- 现在，在退出全屏时，桌面会话的大小会正确调整。
- 现在，当进入睡眠模式后恢复会话时，“RemoteApp 断开连接”对话框会显示在前台。
- 解决了辅助功能问题，如键盘导航。

## <a name="updates-for-version-12247"></a>针对版本 1.2.247 的更新

*发布日期：2019/09/17*

下载：[Windows 64 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE3LkSa)

- 改进了本地化版本的回退语言。 （例如，FR-CA 将以法语正确显示，而不是以英语显示。）
- 删除订阅时，客户端现在会从凭据管理器中正确删除保存的凭据。
- 现在，客户端更新过程在启动后无人参与的情况下完成，并且将在完成后重新启动客户端。
- 现在可以在 Windows 10 上以 S 模式使用客户端。
- 修复了一个问题，对于用户名中有一个空格的用户，该问题会导致更新过程失败。
- 修复了在连接过程中进行身份验证时发生的崩溃问题。
- 修复了在关闭客户端时发生的崩溃问题。
