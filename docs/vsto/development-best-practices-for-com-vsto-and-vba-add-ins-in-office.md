---
title: Práticas recomendadas de desenvolvimento de COM, o VSTO e o VBA suplementos do Office
ms.custom: ''
ms.date: 07/25/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 020faeb330348049dcf12431fadfa6ab099d1584
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Práticas recomendadas de desenvolvimento de COM, o VSTO e o VBA suplementos do Office
  Se você estiver desenvolvendo suplementos do VSTO, COM ou do VBA para o Office, siga as práticas recomendadas de desenvolvimento descritas neste artigo.   Isso ajuda a garantir:

-  Compatibilidade de suplementos em diferentes versões e implantações do Office.
-  Redução da complexidade da implantação do suplemento para seus usuários e administradores de TI.
-  Falhas de instalação ou em tempo de execução não intencionais de seu suplemento não ocorrer.

>Observação: Usando o [ponte de área de trabalho](/windows/uwp/porting/desktop-to-uwp-root) para preparar o COM, VSTO VBA suplemento ou para a Windows Store não é suportado. Suplementos COM, o VSTO e o VBA não podem ser distribuídos no repositório do Windows ou o Office. 
  
## <a name="do-not-check-for-office-during-installation"></a>Não verificar Office durante a instalação  
 Não é recomendável ter o suplemento detectar se o Office é instalado durante o processo de instalação do suplemento. Se o Office não estiver instalado, você pode instalar o suplemento e o usuário será capaz de acessá-lo após a instalação do Office. 
  
## <a name="use-embedded-interop-types-nopia"></a>Use os tipos de interoperabilidade inseridos (NoPIA)  
Se sua solução usa o .NET 4.0 ou posterior, use tipos de interoperabilidade inseridos (NoPIA) em vez de dependendo o escritório principal Interop Assemblies (PIA) redistribuível. Usando a incorporação de tipo reduz o tamanho da instalação da solução e garante a compatibilidade futura. Office 2010 foi a última versão do Office que acompanha o PIA redistribuível. Para obter mais informações, consulte [passo a passo: incorporação de informações de tipo de assemblies do Microsoft Office](https://msdn.microsoft.com/en-us/library/ee317478.aspx) e [equivalência de tipos e tipos de interoperabilidade inseridos](/windows/uwp/porting/desktop-to-uwp-root).

Se sua solução usar uma versão anterior do .NET, é recomendável que você atualize sua solução para usar o .NET 4.0 ou posterior. Usando o .NET 4.0 ou posterior reduz pré-requisitos de tempo de execução em versões mais recentes do Windows.
  
## <a name="avoid-depending-on-specific-office-versions"></a>Evite dependendo versões específicas do Office  
Se sua solução usa a funcionalidade que só está disponível nas versões mais recentes do Office, verifique se o recurso existe (se possível, no nível de recurso) em tempo de execução (por exemplo, usando a exceção manipulação ou verificando a versão). Validar versões mínimas, em vez de versões específicas, usando as APIs com suporte no modelo de objeto, como o [Application.Version propriedade](https://msdn.microsoft.com/en-us/library/office/microsoft.office.interop.excel._application.version.aspx). Não é recomendável que você confiar em metadados binário, caminhos de instalação ou chaves do registro do Office porque eles podem ser alteradas entre instalações, ambientes e versões.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Ativar o uso do Office de 32 bits e 64 bits   
O destino de compilação padrão deve dar suporte a (x86) 32 bits e 64 bits (x64), a menos que sua solução depende de bibliotecas que só estão disponíveis para um número de bits específico. A versão de 64 bits do Office está aumentando na adoção, especialmente em ambientes de grandes dados. Suporte de 32 bits e 64 bits torna mais fácil para seus usuários para fazer a transição entre as versões de 32 bits e 64 bits do Office.

Ao escrever o código do VBA, o uso seguro de 64 bits instruções declare e converter variáveis conforme apropriado. Além disso, certifique-se de que os documentos podem ser compartilhados entre usuários que executam versões de 32 bits ou 64 bits do Office, fornecendo um código para cada número de bits. Para obter mais informações, consulte [64 bits do Visual Basic for visão geral de aplicativos](https://msdn.microsoft.com/en-us/library/office/gg264421.aspx).

## <a name="support-restricted-environments"></a>Suporte a ambientes restritos   
Sua solução não deve exigir privilégios de elevação de conta de usuário ou administrador. Além disso, a solução não deve depender definindo ou alterando:

- O diretório de trabalho atual.
- Diretórios de carregamento DLL.
- A variável de caminho.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Alterar o salvamento local de dados compartilhadas e configurações
Se a solução consiste em um suplemento e um processo externo ao Office, não use pasta de dados de aplicativo do usuário ou o registro para trocar dados ou configurações entre o suplemento e o processo externo. Em vez disso, considere o uso de pasta temporária do usuário, a pasta documentos ou o diretório de instalação da solução.

## <a name="increment-the-version-number-with-each-update"></a>Aumente o número de versão com cada atualização
Definir o número de versão dos binários em sua solução e incrementá-lo com cada atualização. Isso tornará mais fácil para os usuários a identificar alterações entre as versões e avaliar a compatibilidade.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Fornecer instruções de suporte para as versões mais recentes do Office
Clientes que solicitam ISVs para fornecer instruções de suporte para o COM, o VSTO e o VBA suplementos que são executados no Office. Listando seu suporte explícito instruções ajuda os clientes usando o Office 365 ProPlus ferramentas de preparação para entender o suporte. 

Para fornecer instruções de suporte para aplicativos de cliente do Office (por exemplo, Word ou Excel), verifique primeiro se suplementos executado na versão atual do Office e, em seguida, confirme a fornecer atualizações se seu suplemento quebras em uma versão futura. Não é necessário que testar seus suplementos quando a Microsoft lança uma nova compilação, ou uma atualização do Office. Microsoft raramente altera a plataforma de extensibilidade COM, o VSTO e o VBA no Office, e essas alterações serão bem documentadas.

>Importante: A Microsoft mantém uma lista de suplementos com suporte para relatórios de preparação e informações de contato do ISV. Para obter o suplemento listado, consulte [ https://aka.ms/readyforwindows ](https://aka.ms/readyforwindows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Use o Monitor de processo para ajudar a depurar instalação ou problemas de carregamento
Se o suplemento tem problemas de compatibilidade durante a instalação ou carga, eles podem estar relacionados a problemas de acesso de arquivo ou do registro. Use [Process Monitor](/sysinternals/downloads/procmon) ou uma ferramenta semelhante de depuração para registrar e comparar o comportamento em um ambiente de trabalho para ajudar a identificar o problema.
