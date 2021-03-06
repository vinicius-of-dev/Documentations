# Tawk to Documentação

[Documentação_Tawk.to](https://developer.tawk.to/jsapi/)

## onLoad

Função de callback invocado logo após o widget ser renderizado. 
Este callback não é suportado em pop out da janela de chat.

````
Tawk_API = Tawk_API || {}

Tawk_API.onLoad = function() {
	//code here
}
````

## onStatusChange

Função de callback invocado quando o status da página muda.

```
Tawk_API = Tawk_API || {}
Tawk_API.onStatusChange = function(status){}
```

## visitor{};

Objeto utilizado para configurar o nome e email do visitante. 

Não coloque este objeto em uma função já que o valor precisa ser configurado antes do script do widget ser baixado.

````
Tawk_api.visitor = {
	nome: 'nome',
	email: 'email@email.com'
}
````

## popup();

Abre o wigdet do chat como um pop out.

```
Tawk_API.onLoad = function(){
	Tawk_API.popup();
}
```

## showWidget();

Função que faz o chat aparecer.

`Tawk_API.showWidget();`

## hideWidget();

Função que esconde o chat.

`Tawk_API.hideWidget();`

## toggleVisibility();

Mostra ou esconde o widget de chat baseado no estado de visibilidade atual.

```
Tawk_API.onLoad = function(){
    Tawk_API.toggleVisibility();
};
```

## getStatus();

Retorna o status atual da página.

`Tawk_API.getStatus();`

## isVisitorEngaged();

Retornao um valor booleano quando o visitante está atualmente conversando ou pediu um chat de conversa.

`Tawk_API.isVisitorEngaged()`

## endChat();

Finaliza o chat em andamento atual.

`Tawk_API.endChat()`

## setAttributes();

Configure um metadado costumizado independente do chat ou do visitante.

Essta função leva dois parâmetros: **atributo e callback.**

O valor **Atributo** é um dado do tipo Object que é um par chave-valor. A chave pode ser do tipo string e somente pode conter caracteres alfanuméricos e "-"(Dash).

Esta função pode ser utilizado para configurar o nome do visitante e o e-mail, mas você irá precisar habilitar o **Secure Mode** primeiro e suprir o valor hash calculado para esta função.

O modo de segurança é necessário para asegurar a integridade dos dados.

A função callback será invocado para notificar quando a configuração falar.

```
Tawk_API.setAttributes(attributes, callback);

Tawk_API.onLoad = function(){
	Tawk_API.setAttributes({

		'id': 'A1234',
		'store': 'Midvalley'
		'hash': 'hash value'

	}, function(error){
		// Coloque o código aqui quando a atribuição retornar um erro.
	})
}

```

## addEvent();

Configure um evento ao chat. Essa função necessita de 3 valores, um **nome para o evento**, um **metadado opcional** e uma **Função Callback**.

O nome de evento é do tipo string e pode somente conter caracteres alfanuméricos e '-'(Dash).

A função de callback é uma funçção que será invocado para notificar quando ocorrer um erro durante o processo.

```
Tawk_API.addEvent(eventName, metadata, callback);

Tawk_API.onLoad = function(){
    Tawk_API.addEvent('requested-quotation', function(error){});

    Tawk_API.addEvent('product-add-to-cart', {

        'sku'    : 'A0012',
        'name'  : 'Jeans',
        'price' :'50'

    }, function(error){});
};

```

## addTags();

Adicionar tags ao chat.

Esta função toma dois valores como paramêtros; **Tags** and **Função Callback**

O conteúdo das tags deverá ser do tipo String. Este parâmetro poderá receber um array de até 10 strings.

A função callback será invocado para notificar quando ocorrer um erro.

```
Tawk_API.addTags(tags, callback);

Tawk_API.onLoad = function(){
    Tawk_API.addTags(['hello', 'world'], function(error){});
};
```

## removeTags();

Remove as tags do chat.

Esta função recebe dois paramêtros; **Tags** e **Função Callback**.

O paramêtro **Tags** deverá ser do tipo Array, contendo até 10 dados do tipo string.

O função callback será invocado para notificar de quando ocorrer um erro no processo.

```
Tawk_API.removeTags(tags, callback);

//Example

Tawk_API.onLoad = function(){
    Tawk_API.removeTags(['hello', 'world'], function(error){});
};
```

## Secure Mode

**Secure method** é para assegurar que o dado que você esteja enviando seja realmente por você, aumentando a confiabilidade da mensagem.

Para habilitar este modo, adicione o seguinte código na página.

```
Tawk_API = Tawk_API || {};
Tawk_API.visitor = {
    name  : 'Name',
    email : 'email@email.com',
    hash  : 'calculate-hash'
};
```

O código Hash é gerado pelo lado do servidor usando SHA256 para a encriptação, usando o e-mail do usuário e a chave da API do seu site.

Você pode conseguir esta chave da API em Admin -> Property Settings.


## Referências de outros eventos e funç

onBeforeLoad
onChatMaximized
onChatMinimized
onChatHidden
onChatStarted
onChatEnded
onPrechatSubmit
onOfflineSubmit
maximize();
minimize();
toggle();
isChatMaximized();
isChatMinimized();
isChatHidden();
isChatOngoing();
