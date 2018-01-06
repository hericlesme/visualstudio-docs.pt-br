---
title: Criar tabela de comando XML (. Arquivos VSCT) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e007ffe8cf3cc893bc9575a3e7c083090b523467
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="designing-xml-command-table-vsct-files"></a>Criar tabela de comando XML (. Arquivos de VSCT)
Um arquivo de tabela (. VSCT) do comando XML descreve o layout e a aparência de itens de comando para um VSPackage. Itens de comando incluem botões, caixas de combinação, menus, barras de ferramentas e grupos de itens de comando. Este tópico descreve arquivos de comando de tabela XML, como eles afetam os menus e itens de comando e como criá-los.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>Comandos, Menus, grupos e o arquivo. VSCT  
 arquivos. VSCT são organizados em torno de comandos, menus e grupos de comando. Marcas XML no arquivo. VSCT representam cada um desses itens, juntamente com outros itens associados, como botões de comando, posicionamento de comando e bitmaps.  
  
 Quando você cria um novo VSPackage executando o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modelo de pacote, o modelo gera um arquivo. VSCT com os elementos necessários para um comando de menu, a janela de ferramenta ou o editor personalizado, dependendo de suas seleções. Esse arquivo. VSCT, em seguida, pode ser modificado para atender aos requisitos de um VSPackage específico. Para obter exemplos de como modificar um arquivo. VSCT, consulte os exemplos [estendendo Menus e comandos](../../extensibility/extending-menus-and-commands.md).  
  
 Para criar um arquivo. VSCT em branco, consulte [como: criar um. Arquivo VSCT](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Depois de criado, adicione elementos, atributos e valores XML para o arquivo para descrever o layout do item de comando. Para um esquema XML detalhado, consulte o [referência de esquema XML VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>Diferenças entre arquivos .ctc e. VSCT  
 Enquanto o significado por trás de marcas XML em um arquivo. VSCT forem iguais, como aqueles no agora substituído .ctc formato de arquivo, a implementação é um pouco diferente.  
  
-   O novo  **\<extern >** marca é onde você fazer referência a outros arquivos. h para ser compilado, como aquelas para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] barra de ferramentas.  
  
-   Enquanto o suporte a arquivos. VSCT o **/ incluem** instrução, como arquivos de .ctc, ele também apresenta um novo \< **Importar >** elemento. A diferença é, **/ incluem** coloca **todos os** das informações, mas \< **Importar >** exibe somente os nomes.  
  
-   Enquanto .ctc arquivos exigem que um arquivo de cabeçalho no qual você definir diretivas de pré-processador, um não é necessário para arquivos. VSCT. Em vez disso, colocar suas diretivas na tabela de símbolos, localizada no  **\<símbolo >** elementos, localizados na parte inferior do arquivo. VSCT.  
  
-   o recurso de arquivos. VSCT um  **\<anotação >** marca, que permite que você insira as informações que desejar, como anotações ou até mesmo as imagens.  
  
-   Os valores são armazenados como atributos do item.  
  
-   Sinalizadores de comando podem ser armazenados individualmente ou empilhadas.  IntelliSense, no entanto, não funciona em sinalizadores de comando empilhadas. Para obter mais informações sobre sinalizadores de comando, consulte o [comando sinalizador elemento](../../extensibility/command-flag-element.md).  
  
-   Você pode especificar vários tipos, como listas suspensas de divisão, combinações, etc.  
  
-   GUIDs não validar.  
  
-   Cada elemento de interface do usuário tem uma cadeia de caracteres que representa o texto que é exibido com ele.  
  
-   Pai é opcional. Se omitido, o valor "Desconhecido" grupo"é usado.  
  
-   O argumento de ícone é opcional.  
  
-   A seção de bitmap – o mesmo que um .ctc de arquivo, exceto que agora você pode especificar um nome de arquivo por meio de href que será recebido pelo compilador vsct.exe em tempo de compilação.  
  
-   ResID – a ID de recurso de bitmap antigo pode ser usada e ainda funciona da mesma forma .ctc arquivos.  
  
-   HRef – um novo método que permite que você especifique um nome de arquivo para o recurso de bitmap. Ele pressupõe que são usados, assim você pode omitir a seção usada. O compilador primeiro procurar recursos locais para o arquivo, em seguida, em qualquer compartilhamento de rede e todos os recursos definidos pelo switch/i.  
  
-   KeyBinding – Você não precisa especificar um emulador. Se você especificar um, o compilador presumirá que o editor e o emulador são os mesmos.  
  
-   Keychord – foi descartada. O novo formato é Key1, Mod1, chave2, Mod2.  Você pode especificar um caractere, hexadecimal ou constante VK.  
  
 O novo compilador, vsct.exe, compila arquivos .ctc e. VSCT. O compilador ctc.exe antigo, no entanto, não reconhece nem compilar os arquivos. VSCT.  
  
 Você pode usar o compilador vsct.exe para converter um arquivo .cto existente em um arquivo. VSCT. Para obter mais informações sobre isso, consulte [como: criar um. Arquivo VSCT de uma já existente. Arquivo CTO](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).  
  
## <a name="the-vsct-file-elements"></a>Os elementos do arquivo. VSCT  
 A tabela de comando tem a hierarquia e os elementos a seguir:  
  
 [Elemento CommandTable](../../extensibility/commandtable-element.md) — representa todos os comandos, os grupos de menu e os menus associados com o VSPackage.  
  
 [Elemento extern](../../extensibility/extern-element.md) — faz referência a todos os arquivos. h externo para mesclar com o arquivo. VSCT.  
  
 [Incluir elemento](../../extensibility/include-element.md) — faz referência a todos os arquivos adicionais de cabeçalho (. h) você deseja compilar juntamente com o arquivo your.vsct. Um arquivo. VSCT pode incluir arquivos. h que contém constantes que definem os comandos de menu e grupos menus que fornece o IDE ou outro VSPackage.  
  
 [Comandos do elemento](../../extensibility/commands-element.md) — representa todos os comandos individuais que podem ser executados. Cada comando tem os seguintes elementos quatro filho:  
  
 [Elemento menus](../../extensibility/menus-element.md) — representa todos os menus e barras de ferramentas no VSPackage. Menus são contêineres de grupos de comandos.  
  
 [Elemento Groups](../../extensibility/groups-element.md) — representa todos os grupos no VSPackage. Grupos são coleções de comandos individuais.  
  
 [Botões elemento](../../extensibility/buttons-element.md) — representa todos os botões de comando e itens de menu no VSPackage. Botões são os controles visuais que podem ser associados a comandos.  
  
 [Elemento de bitmaps](../../extensibility/bitmaps-element.md) — representa todos os bitmaps para todos os botões no VSPackage. Os bitmaps são imagens que são exibidas ao lado ou nos botões de comando, dependendo do contexto.  
  
 [Elemento CommandPlacements](../../extensibility/commandplacements-element.md) — indica outros locais onde os comandos individuais devem ser colocados nos menus do seu VSPackage.  
  
 [Elemento VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) — Especifica se ou não um comando exibe em todos os horários ou somente em determinados contextos, como quando uma caixa de diálogo específica ou a janela é exibida. Menus e comandos que têm um valor para este elemento serão exibido apenas quando o contexto especificado está ativo. O comportamento padrão é exibir o comando em todos os momentos.  
  
 [Elemento de associações](../../extensibility/keybindings-element.md) — Especifica quaisquer associações de chave para os comandos. Ou seja, um ou mais combinações de teclas que devem ser pressionadas para executar o comando, como **CTRL + S**.  
  
 [Elemento UsedCommands](../../extensibility/usedcommands-element.md) — Informs o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente que, embora o comando especificado é implementado por outro código, quando o VSPackage atual está ativo, ele fornece a implementação do comando.  
  
 `Symbols Element`– Contém os nomes de símbolos e as IDs de GUID para todos os seus comandos no pacote.  
  
## <a name="vsct-file-design-guidelines"></a>. Diretrizes de Design do arquivo VSCT  
 Para criar com êxito um arquivo. VSCT, siga estas diretrizes.  
  
-   Comandos podem ser colocados apenas em grupos, grupos podem ser colocados apenas em menus e menus podem ser colocados apenas em grupos. Menus só são exibidos no IDE, grupos e comandos não são.  
  
-   Submenus não podem ser atribuídos diretamente a um menu, mas devem ser atribuídos a um grupo, que por sua vez é atribuído a um menu.  
  
-   Comandos, submenus e grupos podem ser atribuídos a um grupo paternidade ou menu usando o campo pai de sua diretiva de definição.  
  
-   Organização de uma tabela de comando apenas por meio de campos pai nas diretivas tem uma limitação significativa. As diretivas que definem objetos podem levar um argumento de apenas um pai.  
  
-   Reutilizar comandos, grupos ou submenus requer o uso de uma diretiva de novo para criar uma nova instância do objeto com seu próprio `GUID:ID` par.  
  
-   Cada `GUID:ID` par deve ser exclusivo. Reutilizar um comando que, por exemplo, foi colocado em um menu, uma barra de ferramentas, ou em um menu de contexto, é tratada pelo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface.  
  
-   Comandos e submenus também podem ser atribuídos a vários grupos e grupos podem ser atribuídos a vários menus usando o [comandos elemento](../../extensibility/commands-element.md).  
  
## <a name="vsct-file-notes"></a>. Notas do arquivo VSCT  
 Se você fizer alterações em um arquivo. VSCT depois tanto compilá-lo e colocá-lo em uma DLL de satélite nativo, você deve executar **devenv.exe /setup /nosetupvstemplates**. Isso força os recursos de VSPackage especificados no registro experimental para ser reler e o banco de dados interno que descreve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] devem ser recriados.  
  
 Durante o desenvolvimento, é possível para vários projetos VSPackage seja criado e registrado no hive do registro experimental que pode levar a desordem confuso no IDE. Para corrigir isso, você pode redefinir o hive experimental para as configurações padrão para remover todos os VSPackages e as alterações que fez o IDE. Para redefinir o hive experimental, use a ferramenta de CreateExpInstance.exe que vem com o SDK do Visual Studio. Você pode encontrar em  
  
 **% PROGRAMFILES (x86) %\Visual Studio \<versão > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Execute a ferramenta usando a linha de comando **CreateExpInstance /Reset**. Lembre-se de que essa ferramenta remove o hive experimental todas os VSPackages registrados normalmente não é instalados com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Ampliar menus e comandos](../../extensibility/extending-menus-and-commands.md)