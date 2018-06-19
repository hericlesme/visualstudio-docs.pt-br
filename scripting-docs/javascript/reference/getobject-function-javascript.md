---
title: Função GetObject (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- GetObject
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetObject function
ms.assetid: 62efcdbc-8b86-491d-9000-ef38aa9942a9
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d8bad127a0f260395a1ec19f44ff2d495006024
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637456"
---
# <a name="getobject-function-javascript"></a>Função GetObject (JavaScript)
Retorna uma referência a um objeto de automação de um arquivo.  
  
> [!NOTE]
>  Essa função não tem suporte no Internet Explorer 9 (modo de padrões) ou posterior.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
GetObject([pathname] [, class])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pathname`  
 Opcional. Caminho completo e nome do arquivo que contém o objeto a ser recuperada. Se `pathname` for omitido, `class` será necessário.  
  
 `class`  
 Opcional. Classe do objeto.  
  
 O `class` argumento usa a sintaxe `appname.objectype` e possui as seguintes partes:  
  
 `appname`  
 Necessário. Nome do aplicativo que fornece o objeto.  
  
 `objectype`  
 Necessário. Tipo ou classe de objeto para criar.  
  
## <a name="remarks"></a>Comentários  
 O `GetObject` função não é suportada em [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] ou posterior.  
  
 Use o `GetObject` função para acessar um objeto de automação de um arquivo. Atribua o objeto retornado por `GetObject` para a variável de objeto. Por exemplo:  
  
```JavaScript  
var CADObject;  
CADObject = GetObject("C:\\CAD\\SCHEMA.CAD");  
```  
  
 Quando esse código é executado, o aplicativo associado especificado `pathname` é iniciada, e o objeto no arquivo especificado é ativado. Se `pathname` é uma cadeia de caracteres de comprimento zero (""), `GetObject` retorna uma nova instância de objeto do tipo especificado. Se o `pathname` argumento for omitido, `GetObject` retorna um objeto ativo do tipo especificado. Se nenhum objeto do tipo especificado existir, ocorrerá um erro.  
  
 Alguns aplicativos permitem que você ative a parte de um arquivo. Para fazer isso, adicione um ponto de exclamação (!) ao final do nome do arquivo e segui-la com uma cadeia de caracteres que identifica a parte do arquivo que você deseja ativar. Para obter informações sobre como criar essa cadeia de caracteres, consulte a documentação para o aplicativo que criou o objeto.  
  
 Por exemplo, em um aplicativo de desenho, você pode ter várias camadas para um desenho armazenado em um arquivo. Você pode usar o código a seguir para ativar uma camada em um desenho chamado `SCHEMA.CAD`:  
  
```JavaScript  
var LayerObject = GetObject("C:\\CAD\\SCHEMA.CAD!Layer3");  
```  
  
 Se você não especificar a classe do objeto, automação determina qual aplicativo para iniciar e qual objeto ativar, com base no nome do arquivo que você fornecer. Alguns arquivos, no entanto, podem dar suporte a mais de uma classe de objeto. Por exemplo, um desenho pode oferecer suporte a três tipos diferentes de objetos: um objeto de aplicativo, um objeto de desenho e um objeto de barra de ferramentas, que fazem parte do mesmo arquivo. Para especificar qual objeto em um arquivo que você deseja ativar, use opcional `class` argumento. Por exemplo:  
  
```JavaScript  
var MyObject;  
MyObject = GetObject("C:\\DRAWINGS\\SAMPLE.DRW", "FIGMENT.DRAWING");  
```  
  
 No exemplo anterior, `FIGMENT` é o nome de um aplicativo de desenho e `DRAWING` é um dos tipos de objeto suportados. Depois que um objeto é ativado, referenciá-lo no código usando a variável de objeto definida. O exemplo anterior, você acessa propriedades e métodos do novo objeto usando a variável de objeto `MyObject`. Por exemplo:  
  
```JavaScript  
MyObject.Line(9, 90);  
MyObject.InsertText(9, 100, "Hello, world.");  
MyObject.SaveAs("C:\\DRAWINGS\\SAMPLE.DRW");  
```  
  
> [!NOTE]
>  Use o `GetObject` funciona quando há uma instância atual do objeto, ou se você deseja criar o objeto com um arquivo carregado. Se não houver nenhuma instância atual, e você não deseja o objeto iniciado com um arquivo carregado, use o `ActiveXObject` objeto.  
  
 Se um objeto registrou ele mesmo como um objeto de instância única, apenas uma instância do objeto é criada, não importa como muitas vezes `ActiveXObject` é executado. Com um objeto de instância única, `GetObject` sempre retorna a mesma instância quando chamado com a cadeia de caracteres de comprimento zero ("") sintaxe e isso causa um erro se o `pathname` argumento for omitido.  
  
## <a name="requirements"></a>Requisitos  
 Tem suporte nos seguintes modos de documentos: Quirks, padrões do Internet Explorer 6, padrões do Internet Explorer 7 e padrões do Internet Explorer 8. Consulte [Informações sobre versão](../../javascript/reference/javascript-version-information.md).  
  
## <a name="see-also"></a>Consulte também  
 [Objeto ActiveXObject](../../javascript/reference/activexobject-object-javascript.md)