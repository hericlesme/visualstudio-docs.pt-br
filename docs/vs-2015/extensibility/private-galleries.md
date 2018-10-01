---
title: Galerias privadas | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0875ffc87e7b1161f08a0fdec77de52250f209a6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47463254"
---
# <a name="private-galleries"></a>Galerias privadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [galerias privadas](https://docs.microsoft.com/visualstudio/extensibility/private-galleries).  
  
Você pode compartilhar os controles, modelos e ferramentas que você desenvolve postando-as para um *Galeria privada* na intranet de sua organização, da seguinte maneira:  
  
-   Crie um Atom (RSS) para um local central (repositório) adequadamente configurado na sua intranet. Para obter mais informações, consulte [como: criar um Feed Atom para uma galeria privada](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
-   Distribua um arquivo. pkgdef que descreve a Galeria privada. Recomendamos essa configuração para os administradores que desejam se conectar a uma galeria privada em vários computadores ao mesmo tempo.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Adicionando uma galeria privada para extensões e atualizações no Visual Studio  
 Quando uma galeria privada está disponível, você pode adicioná-lo para **extensões e atualizações** no Visual Studio.  
  
 ![Caixa de diálogo de adicionar Gerenciador de extensões](../extensibility/media/em-adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Para adicionar uma galeria privada para extensões e atualizações  
  
1.  Na barra de menus, escolha **Ferramentas**, **Opções**.  
  
2.  No **ambiente** nó, selecione **extensões e atualizações**.  
  
3.  Escolha o botão **Adicionar**.  
  
4.  No **nome** , insira um nome para a Galeria privada, por exemplo, `My Gallery`.  
  
5.  No **URL** , insira a URL do feed Atom ou site do SharePoint que está hospedando a Galeria privada.  
  
    1.  Se o host é um feed Atom que se conecta à Galeria privada, a URL seria semelhante a este: http://www.mywebsite/mygallery/atom.xml.  Essa URL pode se referir a um arquivo ou um caminho de rede.  
  
    2.  Se o host for um site do SharePoint, a URL seria semelhante a este: http://mysharepoint/sites/mygallery/forms/AllItems.aspx.  
  
### <a name="managing-private-galleries"></a>Gerenciar galerias privadas  
 Um administrador pode disponibilizar uma galeria privada em vários computadores ao mesmo tempo, modificando o registro do sistema em cada computador. Para fazer isso, crie um arquivo. pkgdef que descreve as novas chaves de registro e seus valores.  O formato desse arquivo é da seguinte maneira.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Para obter mais informações, consulte [como: gerenciar um privados da galeria usando configurações do registro](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Instalando extensões de uma galeria privada  
 Você pode procurar e instalar extensões do Visual Studio de uma galeria privada em **extensões e atualizações**. As etapas a seguir usam uma galeria privada chamada `My Gallery`.  
  
 ![Gerenciador de extensões instalando Galeria privada](../extensibility/media/em.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Para procurar e instalar as extensões de uma galeria privada  
  
1.  Na barra de menus, escolha **Ferramentas**, **Extensões e Atualizações**.  
  
2.  No painel esquerdo, selecione **extensões Online**e, em seguida, selecione **minha galeria**.  
  
3.  No painel direito, selecione uma extensão e, em seguida, escolha o **baixar** botão.  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Atualizar extensões de uma galeria privada  
 Conforme novas versões de extensões do Visual Studio são lançadas na Galeria privada, você pode atualizar as extensões que você instalou. As etapas a seguir usam uma galeria privada chamada `My Repository`.  
  
 ![Atualização de galeria privada do Gerenciador de extensão](../extensibility/media/em-update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Para atualizar uma extensão instalada de uma galeria privada  
  
1.  Na barra de menus, escolha **Ferramentas**, **Extensões e Atualizações**.  
  
2.  No painel esquerdo, selecione **atualizações**e, em seguida, selecione **meu repositório**.  
  
3.  No painel direito, selecione uma extensão e, em seguida, escolha o **atualização** botão.  
  
## <a name="see-also"></a>Consulte também  
 [Localizando e usando extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)   
 [Enviar extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md)

