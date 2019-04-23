---
Title: 存储迁移服务概述
description: 搜索引擎结果的主题的简短说明
author: jasongerend
ms.author: jgerend
manager: elizapo
ms.date: 09/24/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: storage
ms.openlocfilehash: edc82c996f6877f770454fc6e27ccf5205a7d540
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2019
ms.locfileid: "59843858"
---
# <a name="storage-migration-service-overview"></a>存储迁移服务概述

存储迁移服务，可以更轻松地迁移到较新版本的 Windows Server 的服务器。 它提供了一个图形工具，列出服务器上的数据的清单，然后将数据和配置传输至较新的服务器，同时应用程序或用户无需更改任何内容。

本主题讨论为什么你想要使用存储迁移服务，迁移过程的工作原理，以及源和目标服务器的要求是什么。

## <a name="why-use-storage-migration-service"></a>为什么要使用存储迁移服务

使用存储迁移服务，因为您有一台服务器 （或多个服务器），你想要迁移到较新硬件或虚拟机。 存储迁移服务可帮助通过执行以下操作：

- 列出多个服务器和其数据的清单
- 快速从源服务器中传输文件、 文件共享和安全配置
- 因此，用户和应用无需任何更改即可访问的现有数据，可以选择接管 （也称为剪切转移） 的源服务器的标识
- 从 Windows Admin Center 用户界面管理一个或多个迁移

![显示存储迁移服务迁移文件和源服务器中的配置应用到目标服务器、 Azure Vm 或 Azure 文件同步关系图。](media\overview\storage-migration-service-diagram.png)

**图 1：存储迁移服务源和目标**

## <a name="how-the-migration-process-works"></a>迁移过程的工作原理

迁移是一个三步骤过程：

1. **列出服务器的清单**来收集有关其文件和配置 （如图 2 所示） 的信息。
2. **传输中的数据 （复制）** 到目标服务器的源服务器中。
3. **转换到新服务器**（可选）。<br>目标服务器假定源服务器的前一个标识，以便应用和用户无需更改任何内容。 <br>源服务器进入维护状态，它们仍包含相同文件，它们始终具有 （我们永远不会从删除文件的源服务器），但没有为用户和应用。 然后可以在方便时停止服务器。

![显示服务器准备好进行扫描的屏幕截图](media/migrate/inventory.png)
**图 2:清点服务器的存储迁移服务**

## <a name="requirements"></a>要求

若要使用存储迁移服务，你需要：

- 一个**源服务器**迁移文件和数据从
- 一个**目标服务器**运行 Windows Server 2019 迁移到-Windows Server 2016 和 Windows Server 2012 R2 正常运行，但具有大约 50%的速度较慢
- **业务流程协调程序 server**运行 Windows Server 2019 来管理迁移  <br>如果要迁移仅几个服务器和一台服务器正在运行 Windows Server 2019，则可以使用该作为业务流程协调程序。 如果要迁移更多的服务器，我们建议使用单独的业务流程协调程序服务器。
- 一个**PC 或服务器运行[Windows Admin Center](../../manage/windows-admin-center/understand/windows-admin-center.md)** 运行存储迁移服务用户界面，除非想要使用 PowerShell 来管理迁移。 Windows Admin Center 和 Windows Server 2019 版本都必须至少版本 1809年。 

### <a name="security-requirements"></a>安全要求

- 迁移帐户，源计算机上的管理员。
- 迁移帐户，目标计算机上的管理员。
- Orchestrator 计算机必须具有启用文件和打印机共享 (Smb-in) 防火墙规则*入站*。
- 源和目标计算机必须具有启用以下防火墙规则*入站*（尽管你可能已经有启用了它们）：
  - 文件和打印机共享 (SMB-In)
  - Netlogon 服务 (Np-in)
  - Windows 管理规范 (Dcom-in)
  - Windows Management Instrumentation (WMI-In)
  
  > [!TIP]
  > 存储迁移服务代理服务安装在 Windows Server 2019 计算机上会自动打开该计算机上的所需防火墙端口。
- 如果计算机属于 Active Directory 域服务域，它们应该全部属于同一个林中。 如果你想要通过剪切，然后传输到目标源的域名时，目标服务器还必须是与源服务器位于同一域中。 直接转换而言这种跨域，但目标的完全限定域名将不同于源...

### <a name="requirements-for-source-servers"></a>源服务器的要求

源服务器必须运行以下操作系统之一：

- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2012
- Windows Server 2008 R2
- Windows Server 2008
- Windows Server 2003 R2
- Windows Server 2003

### <a name="requirements-for-destination-servers"></a>目标服务器的要求

目标服务器必须运行以下操作系统之一：

- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2

> [!TIP]
> 运行 Windows Server 2019 的目标服务器具有双传输的早期版本的 Windows Server 的性能。 此性能提升是由于包含的一个内置的存储迁移服务代理服务，它还将打开必要的防火墙端口，如果它们尚不打开。

## <a name="see-also"></a>请参阅

- [使用存储迁移服务迁移文件服务器](migrate-data.md)
- [存储迁移服务方面的常见问题 (FAQ)](faq.md)
- [存储迁移服务的已知问题](known-issues.md)