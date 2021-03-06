---
ms.assetid: 1ca6f87f-7272-4767-b609-3e295ac7d32f
title: 添加隐私链接
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: cf111fbfc14665d489201f7d88419bdeffb737f9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859390"
---
# <a name="add-privacy-link"></a>添加隐私链接 


若要添加在 "签名\-页面中显示的隐私链接，请使用以下 Windows PowerShell cmdlet 和语法。  

![添加隐私链接](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png) 
  
 
`Set-AdfsGlobalWebContent -PrivacyLink https://fs1.contoso.com/privacy/ -PrivacyLinkText Privacy`  
 
  
> [!IMPORTANT]  
> 此 cmdlet 中的 `linkText` 参数并不是必需的，除非使用另一个值而不是默认值 *Privacy*。 使用默认值的优点是页面将本地化为所有客户端区域设置。 自定义页面中的 "符号\-" 后，将优先使用自定义;因此，你应该为你想要支持的所有语言进行自定义。 所有自定义的内容都使用区域设置参数。 在配置本地化内容时，你应该先使用国家/地区\-较小的区域设置，例如 "en"，然后再将国家和地区配置\-特定的区域设置，例如 "en\-us"。  

## <a name="additional-references"></a>其他参考 
[AD FS 用户登录自定义](AD-FS-user-sign-in-customization.md)  
