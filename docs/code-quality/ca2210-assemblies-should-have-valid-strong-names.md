---
title: "CA2210: Os Assemblies devem ter nomes fortes válidos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 066c78158b688db8164a5ebf23dbe957c7c324ba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: os assemblies devem ter nomes fortes válidos
|||  
|-|-|  
|NomeDoTipo|AssembliesShouldHaveValidStrongNames|  
|CheckId|CA2210|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Um assembly não está assinado com um nome forte, não foi possível verificar o nome forte, ou o nome forte não será válido sem as configurações do registro atual do computador.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Esta regra recupera e verifica o nome forte de um assembly. Ocorre uma violação se qualquer uma das seguintes opções for verdadeira:  
  
-   O assembly não tem um nome forte.  
  
-   O assembly foi alterado após a assinatura.  
  
-   O assembly é assinado com atraso.  
  
-   O assembly foi assinado incorretamente ou falha na assinatura.  
  
-   O assembly requer configurações de registro transmitir a verificação. Por exemplo, a ferramenta de nome forte (Sn.exe) foi usada para ignorar a verificação do assembly.  
  
 O nome forte protege clientes do carregamento desconhecido de um assembly adulterado. Os assemblies sem nomes fortes não devem ser implantados fora de cenários muito limitados. Se você compartilhar ou distribuir assemblies não assinados corretamente, o assembly poderá ser adulterado, o Common Language Runtime poderá não carregar o assembly ou o usuário talvez precise desabilitar a verificação em seu computador. Um assembly sem um nome forte tem das seguintes desvantagens:  
  
-   Sua origem não pode ser verificada.  
  
-   O common language runtime não é possível avisar os usuários se o conteúdo do assembly tiver sido alterado.  
  
-   Ele não pode ser carregado no cache de assembly global.  
  
 Observe que, para carregar e analisar um assembly assinado com atraso, você deve desabilitar verificação para o assembly.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 **Para criar um arquivo de chave**  
  
 Use um dos procedimentos a seguir:  
  
-   Use a ferramenta de Assembly Linker (Al.exe) fornecida pelo [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] SDK.  
  
-   Para o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] versão 1.0 ou 1.1, use o <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> ou <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> atributo.  
  
-   Para o [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], use o `/keyfile` ou `/keycontainer` opção de compilador [/KEYFILE (especificar chave ou par de chaves para assinar um Assembly)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly) ou [/KEYCONTAINER (especificar um contêiner de chave para assinar um Assembly)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) a opção de vinculador em C++).  
  
 **Para assinar o assembly com um nome forte no Visual Studio**  
  
1.  Em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], abra sua solução.  
  
2.  Em **Solution Explorer**, clique com o botão direito e, em seguida, clique em **propriedades.**  
  
3.  Clique o **assinatura** guia e selecione o **assinar o assembly** caixa de seleção.  
  
4.  De **escolher um arquivo de chave de nome forte**, selecione **novo**.  
  
     O **criar chave de nome forte** janela será exibida.  
  
5.  Em **nome do arquivo de chave**, digite um nome para a sua chave de nome forte.  
  
6.  Escolha se deseja proteger a chave com uma senha e, em seguida, clique em **Okey**.  
  
7.  Em **Solution Explorer**, clique com o botão direito e, em seguida, clique em **criar**.  
  
 **Para assinar o assembly com um nome forte fora do Visual Studio**  
  
-   Use a ferramenta de nome forte (Sn.exe) que é fornecida pelo [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] SDK. Para saber mais, veja [Sn.exe (Ferramenta de Nome Forte)](/dotnet/framework/tools/sn-exe-strong-name-tool).  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Suprimir um aviso dessa regra somente se o assembly é usado em um ambiente em que viole o conteúdo não for um problema.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>   
 <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>   
 [Como assinar um assembly com um nome forte](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)   
 [Sn.exe (Ferramenta Nome Forte)](/dotnet/framework/tools/sn-exe-strong-name-tool)