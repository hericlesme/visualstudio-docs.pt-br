---
title: "&lt;Assinatura&gt; elemento (implantação do ClickOnce) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: "13"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: ffcc04808916d8ef31fb77cab72f54c1e22e924c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Assinatura&gt; elemento (implantação do ClickOnce)
Contém as informações necessárias para assinar digitalmente o manifesto de implantação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Comentários  
 Um manifesto de implantação usando uma assinatura do envelope de assinatura é opcional, mas recomendado. Para obter mais informações sobre a assinatura XML arquivos Consulte World Wide Web Consortium recomendação, "Assinatura XML sintaxe e processamento," descrito em [http://www.w3.org/TR/xmldsig-core/](http://www.w3.org/TR/xmldsig-core/).  
  
 Se você deseja assinar o manifesto, hashes devem ser fornecidos para todos os arquivos. Um manifesto com arquivos que não são transformadas em hash não pode ser assinado, porque os usuários não é possível verificar o conteúdo dos arquivos sem hash.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir ilustra uma `Signature` elemento em um manifesto de implantação usado em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação.  
  
```  
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />  
    <SignatureMethod Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
      </Transforms>  
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>d2z5AE...</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>  
4PHj6SaopoLp...  
  </SignatureValue>  
  <KeyInfo>  
    <X509Data>  
      <X509Certificate>  
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...  
      </X509Certificate>  
    </X509Data>  
  </KeyInfo>  
</Signature>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)