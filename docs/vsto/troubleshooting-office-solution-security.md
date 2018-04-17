---
title: Solucionando problemas de segurança de solução do Office | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d7edb1826816ea4f20d66b91a7f9819ef394ce98
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-office-solution-security"></a>Solucionando problemas de segurança da solução do Office
  Este tópico contém dicas para resolver problemas comuns que você pode encontrar ao trabalhar com Protegendo soluções do Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Confiável não podem ser instaladas soluções de Sites restritos  
 Os usuários não é possível instalar uma solução de um local da web se o site da web estiver na zona de sites restritos do Internet Explorer. Isso é verdadeiro mesmo se a solução é assinada com um certificado confiável.  
  
 A URL do manifesto de implantação pode ser categorizada em um dos cinco zonas:  
  
-   Meu computador  
  
-   Internet  
  
-   Intranet local  
  
-   Sites confiáveis  
  
-   Sites restritos  
  
 Se o local do manifesto de implantação tiver sido atribuído à zona de sites restritos, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] não instala a solução. Se o local é conhecido e pode ser confiável, o usuário pode remover o local da zona de sites restritos e instale a solução. Para obter informações sobre como gerenciar as zonas, consulte [Configurar editores confiáveis do ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Soluções não podem ser instaladas de compartilhamentos de arquivos de rede ou locais da Web quando a configuração de segurança reforçada do Internet Explorer ou o Internet Explorer 7 está instalado  
 Internet Explorer Enhanced Security configuração (IEESC) no Windows Server 2003 e superior e o Internet Explorer 7 e superior, restringe consideravelmente a capacidade de usuários para navegar pela Internet. Quando os usuários tentam instalar soluções do Office de um local da web ou de compartilhamento do arquivo de rede, eles podem receber a seguinte mensagem de erro: "a funcionalidade personalizada neste aplicativo não funcionará porque o certificado usado para assinar o manifesto de implantação para *SolutionName* não é confiável. Contate o administrador para obter mais assistência."  
  
 Com IEESC e do Internet Explorer 7 e superior, se a URL do manifesto de implantação é categorizada na zona da Internet, o manifesto deve ter um certificado de um fornecedor confiável ou a solução não pode ser instalada. Sem IEESC, o comportamento padrão é solicitar ao usuário final para tomar uma decisão de confiança.  
  
 Para gerenciar o efeito de IEESC e o Internet Explorer 7 e superior, identificar sites e universal de nomenclatura caminhos UNC (convenção) que você confia e adicioná-los para uma das zonas de segurança confiável (sites confiáveis ou da intranet Local). Para obter informações sobre como gerenciar as zonas, consulte [Configurar editores confiáveis do ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="see-also"></a>Consulte também  
 [Protegendo soluções do Office](../vsto/securing-office-solutions.md)  
  
  