---
ms.assetid: 8f954004-40d5-4c5e-8e0d-e8700c8ec7b1
title: 清单-设置联合服务器
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: f035baaccc5aae7218c5c524ed876e2b45eba252
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80854960"
---
# <a name="checklist-setting-up-a-federation-server"></a>清单：设置联合服务器

此清单包括为 Active Directory 联合身份验证服务 \(AD FS\)中的联合服务器角色准备运行 Windows Server&reg; 2012 的服务器所必需的部署任务。  
  
> [!NOTE]  
> 按顺序完成此清单中的任务。 当某个参考连接将你转至某个过程时，应在完成该过程中的步骤之后返回此主题，以便你可以继续执行此清单中的其他任务。  
  
![设置联合服务器](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**清单：设置联合服务器**  
  
||任务|参考|  
|-|--------|-------------|  
|![设置联合服务器](media/icon_checkboxo.gif)|在开始部署 AD FS 联合服务器之前，请查看;1. 选择 "Windows 内部数据库" \(WID\) 或 SQL Server 以存储 AD FS 配置数据库 2\) 优点和缺点。AD FS 部署拓扑类型及其关联的服务器布局和网络布局建议\)。|设置联合服务器 ![](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[确定 AD FS 部署拓扑](https://technet.microsoft.com/library/gg982491.aspx)<p>![设置联合服务器](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[AD FS 部署拓扑注意事项](https://technet.microsoft.com/library/gg982489.aspx)|  
|![设置联合服务器](media/icon_checkboxo.gif)|查看 AD FS 容量规划指南，确定应该在生产环境中使用的适当数量的联合服务器。|](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[为联合服务器容量](https://technet.microsoft.com/library/gg749917.aspx)设置联合服务器 ![|  
|![设置联合服务器](media/icon_checkboxo.gif)|查看有关组织中的联合服务器位置的 AD FS 设计指南中的信息|![设置联合服务器](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[规划联合服务器的位置](https://technet.microsoft.com/library/dd807069.aspx)<p>![设置联合服务器](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[，以便放置联合服务器](https://technet.microsoft.com/library/dd807127.aspx)|  
|![设置联合服务器](media/icon_checkboxo.gif)|确定备用\-单机联合服务器还是联合服务器场是否更适合你的部署。|![](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[在创建联合服务器时](https://technet.microsoft.com/library/dd807101.aspx)设置联合服务器<p>![](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[在创建联合服务器场时](https://technet.microsoft.com/library/dd807062.aspx)设置联合服务器|  
|![设置联合服务器](media/icon_checkboxo.gif)|确定是否将在帐户伙伴组织或资源伙伴组织中创建此新的联合服务器。|![设置联合服务器](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[检查帐户伙伴中联合服务器的角色](https://technet.microsoft.com/library/dd807117.aspx)<p>![设置联合服务器](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[检查资源伙伴中联合服务器的角色](https://technet.microsoft.com/library/dd807065.aspx)|  
|![设置联合服务器](media/icon_checkboxo.gif)|查看有关联合服务器如何使用服务通信证书和令牌\-签名证书来安全地验证客户端和联合服务器代理请求的信息。 **警告：** 尽管使用具有非限定主机名（如 https：\/\/myserver）的证书通常很常见，但这些证书没有安全价值，并且可以使攻击者向企业客户端模拟 AD FS 联合身份验证服务。 因此，建议你使用完全限定的域名 \(FQDN\) 例如 https：\/\/myserver.contoso.com，并仅使用颁发给联合身份验证服务的 FQDN 的 SSL 证书。|![](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[为联合服务器](https://technet.microsoft.com/library/dd807040.aspx)设置联合服务器证书要求|  
|![设置联合服务器](media/icon_checkboxo.gif)|查看有关如何更新企业网络域名系统 \(DNS\) 的信息，以便可以成功地进行联合服务器的名称解析。|为联合服务器设置联合服务器](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[名称解析要求](https://technet.microsoft.com/library/dd807041.aspx)![|  
|![设置联合服务器](media/icon_checkboxo.gif)|将成为联合服务器的计算机加入帐户伙伴林或资源伙伴林中的域，将使用该计算机对该林的用户进行身份验证或从信任林进行身份验证。 **注意：** 如果要在帐户伙伴组织中设置联合服务器，则必须先将该计算机加入到林中的任何域中，联合服务器将使用联合服务器对该林的用户进行身份验证或从信任林进行身份验证。|![设置联合服务器将](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[计算机加入域](Join-a-Computer-to-a-Domain.md)|  
|![设置联合服务器](media/icon_checkboxo.gif)|在公司网络 DNS 中创建一条新的资源记录，将联合服务器的 DNS 主机名指向联合服务器的 IP 地址。|![设置联合服务器，请](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[向联合服务器&#40;的&#41;企业 DNS 添加主机 a 资源记录](Add-a-Host--A--Resource-Record-to-Corporate-DNS-for-a-Federation-Server.md)|  
|![设置联合服务器](media/icon_checkboxo.gif)|\(可选\) 如果要将联合服务器添加到联合服务器场中，则可能必须先将现有令牌\-签名 \(证书的私钥导出到场中的第一个联合服务器\)，以便在其他联合服务器必须导入相同证书时，可以使用证书的文件格式。<p>如果你颁发的服务器身份验证证书可供多 \(台计算机重复使用，而无需导出\)，或者你将为场中的每个联合服务器获取唯一的服务器身份验证证书，则不需要导出私钥。 **注意：** 中的 AD FS 管理 "管理单元\-是指作为服务通信证书的联合服务器的服务器身份验证证书。|设置联合服务器 ![](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[导出服务器身份验证证书的私钥部分](Export-the-Private-Key-Portion-of-a-Server-Authentication-Certificate.md)|  
|![设置联合服务器](media/icon_checkboxo.gif)|从证书颁发机构 \(CA\)获取服务器身份验证证书 \(或私钥\) 之后，必须将证书文件导入到每个联合服务器的默认网站。 **注意：** 必须先在默认网站上安装此证书，然后才能使用 AD FS 联合服务器配置向导。|![设置联合服务器会将](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[服务器身份验证证书导入到默认](Import-a-Server-Authentication-Certificate-to-the-Default-Web-Site.md)网站|  
|![设置联合服务器](media/icon_checkboxo.gif)|\(可选\) 作为从 CA 获取服务器身份验证证书的替代方法，可以使用 Internet Information Services \(IIS\) 来创建联合服务器的示例证书。 **警告：** 在生产环境中使用自\-签名服务器身份验证证书部署联合服务器不是最佳安全方案。|![设置联合服务器](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[IIS：创建自\-签名服务器证书](https://go.microsoft.com/fwlink/?LinkID=108271)，然后完成过程将[服务器身份验证证书导入到默认](Import-a-Server-Authentication-Certificate-to-the-Default-Web-Site.md)网站|  
|![设置联合服务器](media/icon_checkboxo.gif)|如果要在帐户伙伴组织中配置联合服务器场环境，则必须在服务器场将驻留的 Active Directory 域服务 \(AD DS\) 中创建和配置专用服务帐户，并将场中的每台联合服务器配置为使用此帐户。 通过执行此过程，您将允许企业网络上的客户端使用 Windows 集成身份验证对服务器场中的任何联合服务器进行身份验证。|![设置联合服务器](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[手动配置联合服务器场的服务帐户](Manually-Configure-a-Service-Account-for-a-Federation-Server-Farm.md)|  
|![设置联合服务器](media/icon_checkboxo.gif)|在将成为联合服务器的计算机上安装联合身份验证服务角色服务。|![设置联合服务器](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[的安装联合身份验证服务角色服务](Install-the-Federation-Service-Role-Service.md)|  
|![设置联合服务器](media/icon_checkboxo.gif)|使用 AD FS 联合服务器配置向导，将计算机上的 AD FS 软件配置为充当联合服务器角色。<p>如果要设置独立\-的联合服务器、在新场中创建第一个联合服务器或将计算机加入现有的联合服务器场，请执行以下过程。 **注意：** 对于 \(SSO\) 设计上的联合 Web 单一登录\-，帐户伙伴组织和资源伙伴组织中必须至少有一个联合服务器。|![设置联合服务器](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[创建独立联合服务器](Create-a-Stand-Alone-Federation-Server.md)<p>![设置联合服务器，请](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[在联合服务器场中创建第一个联合服务器](Create-the-First-Federation-Server-in-a-Federation-Server-Farm.md)<p>![设置联合服务器](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[将联合服务器添加到联合服务器场](Add-a-Federation-Server-to-a-Federation-Server-Farm.md)|  
|![设置联合服务器](media/icon_checkboxo.gif)|\(可选\) 使用中的 AD FS 管理\-snap 来添加和配置部署设计所需的 AD FS 证书。 有关使用中的 snap\-添加或更改证书的详细信息，请参阅[联合服务器的证书要求](https://technet.microsoft.com/library/dd807040.aspx)。|![设置联合服务器](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[添加令牌签名证书](Add-a-Token-Signing-Certificate.md)<p>![设置联合服务器时](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[添加令牌解密证书](Add-a-Token-Decrypting-Certificate.md)<p>![设置联合服务器](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[设置服务通信证书](Set-a-Service-Communications-Certificate.md)|  
|![设置联合服务器](media/icon_checkboxo.gif)|如果这是你的组织中的第一台联合服务器，则配置联合身份验证服务以便符合 AD FS 设计。|![设置联合服务器](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[清单：配置帐户伙伴组织](Checklist--Configuring-the-Account-Partner-Organization.md)<p>![设置联合服务器](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[清单：配置资源伙伴组织](Checklist--Configuring-the-Resource-Partner-Organization.md)|  
|![设置联合服务器](media/icon_checkboxo.gif)|在客户端计算机上，验证联合服务器是否正常运行。|设置联合服务器 ![](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[验证联合服务器是否正常运行](Verify-That-a-Federation-Server-Is-Operational.md)| 
