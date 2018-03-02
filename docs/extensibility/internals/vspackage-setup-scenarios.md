---
title: "Cenários de instalação VSPackage | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, deployment considerations
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 452a5cfee55bd314bb062d2d1ddd8496593190fa
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="vspackage-setup-scenarios"></a>Cenários de instalação VSPackage

É importante para o instalador de seu VSPackage flexibilidade de design. Por exemplo, talvez seja necessário liberar um patch de segurança no futuro, ou você pode alterar uma estratégia de negócios que exige suporte a controle de versão completo lado a lado.

Em [dando suporte a várias versões do Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), você pode ler sobre as vantagens e problemas de oferecer suporte a instalações lado a lado do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] com instalações lado a lado ou compartilhadas do seu VSPackage. Em resumo, lado a lado VSPackages oferecem mais flexibilidade para dar suporte a novos recursos do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

Os cenários discutidos neste tópico não são as opções somente, mas são apresentados como práticas recomendadas sugeridas.

## <a name="components-privacy-and-sharing"></a>Componentes, privacidade e compartilhamento

### <a name="make-your-components-independent"></a>Verifique os componentes independentes

Depois de identificar e popular um componente, atribua um `GUID`e implantar o componente, você não pode alterar sua composição. Se você alterar a composição de um componente, o componente resultante deve ser um novo componente com um novo `GUID`. Considerando esses fatos, a maior flexibilidade de controle de versão é permitida, tornando cada unidade auto-suficiente, independente do componente. Para obter mais informações sobre as regras que regem os componentes, consulte [alterar o código do componente](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) e [o que acontece se o componente de regras são divididos?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Não misture recursos compartilhados e privados em um componente

Contagem de referência ocorre no nível do componente. Consequentemente, a combinação de recursos compartilhados e privados em um componente torna impossível atualizar recursos particulares, como um arquivo executável, sem substituir também recursos compartilhados. Este cenário cria problemas de compatibilidade com versões anteriores e impede a criação de recurso lado a lado.

Por exemplo, os valores do registro usada para registrar o VSPackage com o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] devem ser mantidos em um componente separado de um usado para registrar o VSPackage com o Visual Studio. Arquivos compartilhados ou valores do registro, vá em outro componente.

## <a name="scenario-1-shared-vspackage"></a>Cenário 1: Compartilhado VSPackage

Nesse cenário, um VSPackage compartilhado (um binário único que dá suporte a várias versões do Visual Studio é fornecido em um pacote do Windows Installer. Registrar com cada versão do Visual Studio é controlado por recursos selecionáveis pelo usuário. Isso também significa que quando atribuído para separar os recursos, cada componente pode ser selecionada individualmente para instalação ou desinstalação, colocando o usuário no controle de integrar o VSPackage versões diferentes do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. (Consulte [recursos do Windows Installer](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) para obter mais informações sobre o uso de recursos em pacotes do Windows Installer.)

![Instalador de VSPackage compartilhado do VS](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Conforme mostrado na ilustração, os componentes compartilhados são feitos parte do recurso Feat_Common, que sempre é instalado. Tornando os recursos Feat_VS2002 e Feat_VS2003 visível, os usuários podem escolher no tempo de instalação em quais versões do Visual Studio que desejam integrar o VSPackage. Os usuários também podem usar o modo de manutenção do Windows Installer para adicionar ou remover recursos, que nesse caso adiciona ou remove as informações de registro VSPackage de diferentes versões do Visual Studio.

> [!NOTE]
> A definição de coluna de exibição do recurso como 0 oculta. Um valor de coluna de nível baixo, como 1, garante que ele sempre será instalado. Para obter mais informações, consulte [INSTALLLEVEL propriedade](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) e [tabela de recursos](http://msdn.microsoft.com/library/aa368585.aspx).

## <a name="scenario-2-shared-vspackage-update"></a>Cenário 2: Atualização de VSPackage compartilhado

Nesse cenário, uma versão atualizada do instalador VSPackage no cenário 1 é enviada. Para fins de discussão, a atualização adiciona suporte para o Visual Studio, mas ele pode também ser um patch de segurança mais simples ou o pacote de serviço de correção de bug. Regras do Windows Installer para instalar os componentes mais recentes exigem inalterados componentes já está no sistema não são copiados novamente. Nesse caso, um sistema com a versão 1.0 já está presente irá substituir o componente atualizado Comp_MyVSPackage.dll e permitem que os usuários optar por adicionar o novo recurso Feat_VS2005 com seu componente Comp_VS2005_Reg.

> [!CAUTION]
> Sempre que um VSPackage é compartilhado entre várias versões do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], é essencial que as versões posteriores do VSPackage mantenham compatibilidade com versões anteriores do Visual Studio. Quando você não pode manter a compatibilidade com versões anteriores, você deve usar VSPackages lado a lado, privados. Para obter mais informações, consulte [dando suporte a várias versões do Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![Instalador de atualização de pacote VS compartilhados VS](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Este cenário apresenta um novo instalador VSPackage, tirando proveito do suporte do Windows Installer para atualizações secundárias. Os usuários simplesmente instalar a versão 1.1 e atualizar a versão 1.0. No entanto, não é necessário ter a versão 1.0 do sistema. O mesmo instalador instalará a versão 1.1 em um sistema sem versão 1.0. A vantagem para fornecer atualizações secundárias dessa maneira é que não é necessário executar o trabalho de desenvolvimento de um instalador de atualização e uma instalação completa do produto. Um instalador faz ambos os trabalhos. Uma correção de segurança ou service pack pode em vez disso, tirar proveito de patches do Windows Installer. Para obter mais informações, consulte [atualizações e a aplicação de patch](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).

## <a name="scenario-3-side-by-side-vspackage"></a>Cenário 3: Lado a lado VSPackage

Este cenário apresenta dois instaladores VSPackage — um para cada versão do Visual Studio .NET 2003 e o Visual Studio. Cada instalador instala um lado a lado ou privado, VSPackage (aquela que é criada e instalada para uma determinada versão do Visual Studio especificamente). Cada VSPackage está em seu próprio componente. Consequentemente, cada um pode individualmente atendida com manutenção ou patches de versões. Como a DLL VSPackage agora é específico da versão, é seguro incluir suas informações de registro no mesmo componente como a DLL.

![Instalador de pacote do VS lado a lado do VS](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Cada instalador também inclui o código que é compartilhado entre os dois instaladores. Se o código compartilhado é instalado em um local comum, instalar os dois arquivos. msi instalará o código compartilhado somente uma vez. O instalador segundo incrementa apenas uma contagem de referência no componente. A contagem de referência garante que, se uma dos VSPackages for desinstalada, o código compartilhado permanecerá para o outros VSPackage. Se o segundo VSPackage é desinstalado, o código compartilhado será removido.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Cenário 4: Atualização de VSPackage de lado a lado

Nesse cenário, o VSPackage para Visual Studio sofreu uma vulnerabilidade de segurança e é necessário executar uma atualização. Como no cenário 2, você pode criar um novo arquivo. msi que atualiza uma instalação existente para incluir a correção de segurança, bem como implantar novas instalações com a correção de segurança já em vigor.

Nesse caso, o VSPackage é um VSPackage gerenciado instalado no cache de assembly global (GAC). Quando você recriá-lo para incluir a correção de segurança, você deve alterar a parte de número de revisão do número de versão do assembly. As informações de registro para o novo número de versão do assembly substitui a versão anterior, causando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para carregar o assembly fixado.

![Instalador de atualização de VSPackage lado a lado do VS](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Para obter mais informações sobre a implantação dos assemblies lado a lado, consulte [simplificando a implantação e resolvendo inferno com o .NET Framework](http://msdn.microsoft.com/library/ms973843.aspx).

## <a name="see-also"></a>Consulte também

[O Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)  
[Fornecer suporte à várias versões do Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)