---
title: 'CA3147: Manipuladores de verbo marca com ValidateAntiForgeryToken'
ms.date: 08/08/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 4b4369cfd310be9322d17b8bdbfe79880f2aa579
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008688"
---
# <a name="ca3147-mark-verb-handlers-with-validateantiforgerytoken"></a>CA3147: Manipuladores de verbo marca com ValidateAntiForgeryToken

|||
|-|-|
|NomeDoTipo|MarkVerbHandlersWithValidateAntiForgeryToken|
|CheckId|CA3147|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Um método de ação do controlador MVC do ASP.NET não está marcado com <xref:Microsoft.AspNetCore.Mvc.ValidateAntiForgeryTokenAttribute?displayProperty=fullName>, ou um atributo que especifica o verbo HTTP, como <xref:Microsoft.AspNetCore.Mvc.HttpGetAttribute?displayProperty=fullName> ou <xref:Microsoft.AspNetCore.Mvc.AcceptVerbsAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da regra

Durante a criação de um controlador ASP.NET MVC, lembre-se de ataques de falsificação de solicitação entre sites. Um ataque de falsificação de solicitação entre sites pode enviar solicitações mal-intencionadas de um usuário autenticado ao seu controlador ASP.NET MVC. Para obter mais informações, consulte [prevenção de XSRF/CSRF no ASP.NET MVC e páginas da web](/aspnet/mvc/overview/security/xsrfcsrf-prevention-in-aspnet-mvc-and-web-pages).

Esta regra verifica se esse controlador ASP.NET MVC métodos de ação ambos:

- Ter o <xref:Microsoft.AspNetCore.Mvc.ValidateAntiForgeryTokenAttribute> e especifique verbos HTTP permitidos, não incluindo HTTP GET.

- Especifique o HTTP GET como um verbo permitido.

## <a name="how-to-fix-violations"></a>Como corrigir violações

- Para ações do controlador ASP.NET MVC que manipulam solicitações HTTP GET e não têm efeitos colaterais potencialmente nocivos, adicione um <xref:Microsoft.AspNetCore.Mvc.HttpGetAttribute> para o método.

   Se você tiver um ASP.NET MVC solicitações de ação do controlador que manipula a HTTP GET e tem potencialmente prejudiciais efeitos colaterais, como a modificação de dados confidenciais, seu aplicativo é vulnerável a ataques de falsificação de solicitação entre sites.  Você precisará recriar seu aplicativo para que somente as solicitações HTTP POST, PUT ou DELETE executam operações confidenciais.

- Para ações do controlador ASP.NET MVC que lidar com HTTP POST, PUT ou as solicitações de exclusão, adicione <xref:Microsoft.AspNetCore.Mvc.ValidateAntiForgeryTokenAttribute> e especificando os verbos HTTP permitidos de atributos (<xref:Microsoft.AspNetCore.Mvc.AcceptVerbsAttribute>, <xref:Microsoft.AspNetCore.Mvc.HttpPostAttribute>, <xref:Microsoft.AspNetCore.Mvc.HttpPutAttribute>, ou <xref:Microsoft.AspNetCore.Mvc.HttpDeleteAttribute>). Além disso, você precisará chamar <xref:Microsoft.AspNetCore.Mvc.ViewFeatures.HtmlHelper.AntiForgeryToken%2A?displayProperty=nameWithType> do modo de exibição do MVC ou página da web Razor. Por exemplo, consulte [examinando os métodos edit e Editar modo de exibição](/aspnet/mvc/overview/getting-started/introduction/examining-the-edit-methods-and-edit-view).

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso nessa regra se:

- A ação do controlador MVC do ASP.NET não tem prejudiciais efeitos colaterais.

- O aplicativo valida o token antifalsificação de maneira diferente.

## <a name="validateantiforgerytoken-attribute-example"></a>Exemplo de atributo ValidateAntiForgeryToken

### <a name="violation"></a>Violação

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            // You don't want an attacker to specify to who and how much money to transfer.

            return null;
        }
    }
}
```

### <a name="solution"></a>Solução

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            return null;
        }
    }
}
```

## <a name="httpget-attribute-example"></a>Exemplo de atributo HttpGet

### <a name="violation"></a>Violação

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult Help(int topicId)
        {
            // This Help method is an example of a read-only operation with no harmful side effects.
            return null;
        }
    }
}
```

### <a name="solution"></a>Solução

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpGet]
        public ActionResult Help(int topicId)
        {
            return null;
        }
    }
}
```
