---
title: <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
ms.openlocfilehash: 2910f47b85ee67694cae0c3a725c3c7c7b3803c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701718"
---
# <a name="authorizationpolicies"></a>\<authorizationPolicies>
本配置节包含可使用 `add` 关键字添加的授权策略类型的集合。 每个授权类型都包含一个所需的 `policyType` 属性，此属性是一个字符串。 该属性指定一个授权策略，可以将一组输入声明转换为另一组声明。 可以根据该授权策略来授予或拒绝访问控制。 授权策略的工作原理的详细信息，请参阅<xref:System.IdentityModel.Policy.IAuthorizationPolicy>并[授权策略](../../../../../docs/framework/wcf/samples/authorization-policy.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [授予对服务操作的权限](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [如何：创建自定义授权管理器服务](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)
- [授权策略](../../../../../docs/framework/wcf/samples/authorization-policy.md)
