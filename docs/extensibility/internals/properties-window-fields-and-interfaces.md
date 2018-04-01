---
title: Campos de janela de propriedades e Interfaces | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1f238cceb189723e3ec10fbf8db4abbd9675ae21
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="properties-window-fields-and-interfaces"></a>Interfaces e os campos da janela de propriedades
O modelo de seleção determinar quais informações são exibidas no **propriedades** janela baseia-se na janela que tem o foco no IDE. Cada janela e objeto dentro da janela selecionada, podem ter seu objeto de contexto de seleção enviada por push para o contexto da seleção global. O ambiente atualiza o contexto da seleção global com valores de um quadro de janela quando essa janela tem o foco. Quando o foco for alterado, portanto não o contexto da seleção.  
  
## <a name="tracking-selection-in-the-ide"></a>Controle de seleção no IDE  
 O quadro de janela ou um site, o IDE, de propriedade tem um serviço chamado <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. As etapas a seguir mostram como uma alteração em uma seleção, causada por que o usuário alterar o foco para outra janela aberta ou selecionando um item de projeto diferente em **Solution Explorer**, é implementado para alterar o conteúdo exibido no  **Propriedades** janela.  
  
1.  O objeto criado pelo seu VSPackage que é localizado em chamadas a janela selecionada <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> ter <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> invocar <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2.  O contêiner de seleção, fornecido pela janela selecionada, cria seu próprio <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objeto. Quando a seleção é alterada, o VSPackage chama <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> para notificar todos os ouvintes no ambiente, incluindo o **propriedades** janela da alteração. Ele também fornece acesso às informações de hierarquia e o item relacionados à nova seleção.  
  
3.  Chamando <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> e passando os itens da hierarquia selecionada no `VSHPROPID_BrowseObject` parâmetro preenche o <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objeto.  
  
4.  Um objeto derivado do [IDispatch Interface](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) é retornado para <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> para o item solicitado e o ambiente é quebrada em um <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (consulte a etapa a seguir). Se a chamada falhar, o ambiente faz uma segunda chamada para `IVsHierarchy::GetProperty`, passando o contêiner de seleção <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> fornecem o item de hierarquia ou itens.  
  
     Seu projeto não cria VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> como a janela fornecidos pelo ambiente VSPackage que implementa ele (por exemplo, **Solution Explorer**) constrói <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> em seu nome.  
  
5.  O ambiente chama os métodos do <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> para obter os objetos com base no `IDispatch` interface para preencher o **propriedades** janela.  
  
 Quando um valor na **propriedades** janela é alterada, implementar VSPackages `IVsTrackSelectionEx::OnElementValueChangeEx` e `IVsTrackSelectionEx::OnSelectionChangeEx` para relatar a alteração para o valor do elemento. Em seguida, invoca o ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> ou <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> para manter as informações exibidas no **propriedades** janela sincronizados com os valores de propriedade. Para obter mais informações, consulte [atualizar valores de propriedade na janela propriedades](#updating-property-values-in-the-properties-window).  
  
 Além de selecionar outro item de projeto no **Solution Explorer** para exibir as propriedades relacionadas a esse item, você também pode escolher um objeto diferente de dentro de uma janela de formulário ou documento usando a lista suspensa disponível do **Propriedades** janela. Para obter mais informações, consulte [lista de objetos de janela de propriedades](../../extensibility/internals/properties-window-object-list.md).  
  
 Você pode alterar o modo de exibição de informações de **propriedades** grade da janela de em ordem alfabética em categórica, e, se disponível, você também pode abrir uma página de propriedades de um objeto selecionado clicando nos botões apropriados no  **Propriedades** janela. Para obter mais informações, consulte [botões de janela de propriedades](../../extensibility/internals/properties-window-buttons.md) e [páginas de propriedade](../../extensibility/internals/property-pages.md).  
  
 Por fim, a parte inferior da **propriedades** janela também contém uma descrição do campo selecionado no **propriedades** grade da janela. Para obter mais informações, consulte [obter descrições dos campos na janela de propriedades](#getting-field-descriptions-from-the-properties-window).  
  
## <a name="updating-property-values-in-the-properties-window"></a>Atualizando valores de propriedade na janela Propriedades
Há duas maneiras para manter o **propriedades** janela em sincronia com as alterações de valor de propriedade. A primeira é para chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface, que fornece acesso à funcionalidade básica de janelas, incluindo o acesso e criação de janelas de ferramenta e documento fornecidos pelo ambiente de. As etapas a seguir descrevem esse processo de sincronização.  
  
### <a name="updating-property-values-using-ivsuishell"></a>Atualizando valores de propriedade usando IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Para atualizar valores de propriedade usando a interface de IVsUIShell  
  
1.  Chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (por meio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> service) sempre que VSPackages, projetos, ou editores precisam criar ou enumerar as janelas de ferramenta ou documento.  
  
2.  Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> para manter o **propriedades** em sincronia com as alterações de propriedade para um projeto de janela (ou qualquer outro objeto selecionado que está sendo procurado pelo **propriedades** janela) sem implementar <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> e acionar <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> eventos.  
  
3.  Implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> métodos <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> para estabelecer e desativar, respectivamente, a notificação de cliente de eventos de hierarquia sem a necessidade de hierarquia para implementar <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
### <a name="updating-property-values-using-iconnection"></a>Atualizando valores de propriedade usando IConnection  
 A segunda maneira de manter o **propriedades** janela em sincronia com as alterações de valor de propriedade é implementar `IConnection` no objeto conectável para indicar a existência de interfaces de saída. Se você deseja localizar o nome da propriedade, derivar seu objeto de <xref:System.ComponentModel.ICustomTypeDescriptor>. O <xref:System.ComponentModel.ICustomTypeDescriptor> implementação pode modificar os descritores de propriedade retorna e altere o nome de uma propriedade. Para localizar a descrição, criar um atributo que deriva de <xref:System.ComponentModel.DescriptionAttribute> e substituir a propriedade de descrição.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Considerações na implementação da interface IConnection  
  
1.  `IConnection`fornece acesso a um objeto de enumerador subdiretório com o <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interface. Ele também fornece acesso a conexão ponto sub objetos, cada um dos que implementa o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface.  
  
2.  Qualquer objeto de procura é responsável por implementar um <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> eventos. O **propriedades** janela informará para o conjunto de eventos por meio de `IConnection`.  
  
3.  Um ponto de conexão controla quantas conexões (um ou mais) permite em sua implementação de <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Um ponto de conexão que permite apenas uma interface pode retornar <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> do <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> método.  
  
4.  Um cliente pode chamar o `IConnection` interface para obter acesso a um objeto de enumerador subdiretório com o <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interface. O <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interface poderá então ser chamada para enumerar os pontos de conexão para cada interface IID (ID) de saída.  
  
5.  `IConnection`também pode ser chamado para obter acesso a objetos de subdiretório de ponto de conexão com o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface para cada saída IID. Por meio de <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface, um cliente inicia ou Finaliza um loop de consultoria com o objeto conectável e a sincronização do cliente. O cliente também pode chamar o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface para obter um objeto de enumerador com o <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> interface para enumerar as conexões que ele conhece.  
  
## <a name="getting-field-descriptions-from-the-properties-window"></a>Obter descrições dos campos na janela de propriedades
Na parte inferior do **propriedades** janela, uma área de descrição exibe informações relacionadas ao campo de propriedade selecionada. Esse recurso é ativado por padrão. Se você deseja ocultar o campo de descrição, com o botão direito do **propriedades** janela e clique em **descrição**. Isso também remove a marca de seleção ao lado de **descrição** título na janela do menu. Você pode exibir o campo novamente, seguindo as mesmas etapas para alternar **descrição** novamente.  
  
 As informações no campo de descrição vêm de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Cada método, interface, coclass e assim por diante podem ter um não localizado `helpstring` atributo na biblioteca de tipos. O **propriedades** janela recupera a cadeia de caracteres de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### <a name="to-specify-localized-help-strings"></a>Para especificar cadeias de caracteres de ajuda traduzido  
  
1.  Adicionar o `helpstringdll` atributo à instrução biblioteca na biblioteca de tipos (`typelib`).  
  
    > [!NOTE]
    >  Esta etapa é opcional se a biblioteca de tipo estiver em um arquivo de biblioteca (. olb) do objeto.  
  
2.  Especifique `helpstringcontext` atributos para as cadeias de caracteres. Você também pode especificar `helpstring` atributos.  
  
     Esses atributos são diferentes de `helpfile` e `helpcontext` atributos, que estão contidos nos tópicos de Ajuda do arquivo. chm real.  
  
 Para recuperar as informações de descrição a ser exibida para o nome da propriedade realçada, o **propriedades** janela chamadas <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> para a propriedade selecionada, especificando o desejado `lcid` atributo para o cadeia de caracteres de saída. Internamente, <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> localiza o arquivo. dll especificado no `helpstringdll` atributo e chamadas `DLLGetDocumentation` nesse arquivo. dll com o contexto especificado e `lcid` atributo.  
  
 A assinatura e implementação de `DLLGetDocumentation` são:  
  
```cpp  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 O `DLLGetDocumentation` função deve ser uma exportação definida no arquivo. def para a DLL.  
  
 Internamente, é criado um arquivo olb que é realmente uma DLL. Essa DLL contém um recurso, o arquivo de biblioteca (. tlb) de tipo e uma função exportada, `DLLGetDocumentation`.  
  
 No caso de arquivos olb, o `helpstringdll` atributo é opcional, pois ele é o mesmo arquivo que contém o próprio arquivo. tlb.  
  
 Para obter as cadeias de caracteres para aparecer no **descrições** painel, portanto, o mínimo que você precisa fazer é especificar o `helpstring` atributo na biblioteca de tipos. Se você quiser que essas cadeias de caracteres a ser localizada, você precisa especificar o `helpstringdll` atributo (opcional) e o `helpstringcontext` atributo (obrigatório) e implementam `DLLGetDocumentation`.  
  
 Não existem interfaces adicionais que precisam ser implementados quando obtendo localizado informações por meio do idl `helpstringcontext` atributo e `DLLGetDocumentation`.  
  
 Outra maneira de obter o nome localizado e a descrição de uma propriedade está implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Para obter mais informações relacionadas à implementação desse método, consulte [campos da janela de propriedades e Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md).  

## <a name="see-also"></a>Consulte também  
 [Estender as propriedades](../../extensibility/internals/extending-properties.md)