---
title: "Passo a passo: Adicionando XAML personalizado para a página inicial | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 924a6e2640002bc47eb75c903c46b5a170a9c308
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>Passo a passo: Adicionando XAML personalizado para a página inicial
Este passo a passo mostra como criar um Visual Studio página inicial personalizada que contém um navegador da Web.  
  
## <a name="adding-custom-xaml"></a>Adicionando XAML personalizada  
  
1.  Criar uma página inicial, seguindo as instruções em [criando uma página de início personalizado](../extensibility/creating-a-custom-start-page.md).  
  
2.  No arquivo MainWindow. XAML, localize o \<grade > seção.  
  
3.  Adicionar um \<TabControl > elemento e um \<TabItem > dentro do \< grade > elemento, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4.  Adicionar um segundo \<TabItem >, com um \<botão > elemento que abre um novo projeto:  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="MyButton" Height="Auto">  
                <Button Name="btnNewProj" Content="New Project"   
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
                    CommandParameter="File.NewProject" >  
                </Button>  
            </TabItem>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
## <a name="testing-the-custom-start-page"></a>Testando a página de início personalizado  
  
1.  Pressione F5.  
  
     A instância experimental do Visual Studio é aberto com a página inicial personalizada instalado, mas não selecionada.  
  
2.  Na instância experimental do Visual Studio, abra o **/opções de ferramentas / ambiente** página.  
  
3.  Selecione **inicialização**. Sobre o **Personalizar página inicial** lista, selecione o arquivo. XAML e clique em **Okey**.  
  
4.  Sobre o **exibição** menu, clique em **página inicial**.  
  
5.  Clique o **Bing** guia.  
  
     Você deve ver uma página da web de Bing.  
  
6.  Clique o **MyButton** guia.  
  
     Você deve ver uma **MyProject** botão que abre o **novo projeto** caixa de diálogo.  
  
7.  Feche a instância experimental.  
  
## <a name="applying-the-custom-start-page"></a>Aplicando a página de início personalizado  
  
#### <a name="to-test-the-custom-start-page"></a>Para testar a página de início personalizado  
  
1.  Em **Ferramentas / opções / ambiente**, selecione **inicialização**. Sobre o **Personalizar página inicial** lista, selecione o arquivo. XAML e clique em **Okey**.  
  
## <a name="next-steps"></a>Próximas etapas  
 A página do Visual Studio iniciar agora contém uma guia que exibe uma guia de MyButton e uma guia do navegador da Web. Você pode criar páginas iniciar personalizadas que têm outra funcionalidade usando o *por trás do código* modelo para adicionar um arquivo. dll personalizado, como mostrado na [adicionando o controle de usuário para a página de início](../extensibility/adding-user-control-to-the-start-page.md). Você pode compartilhar páginas personalizadas iniciar com outros usuários, publicando o arquivo resultante .vsix o [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) site da Web ou para outro site da Web ou de rede compartilhar. Para obter mais informações, consulte [implantação de páginas de inicialização personalizada](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando a página inicial](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Controles de contêiner WPF](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)