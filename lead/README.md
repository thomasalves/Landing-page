# Exemplo de formulário para captura de Leads do assignment Show me the Leads

## Resumo

- Você receberá a URL exclusiva de sua equipe
- O Formulário deverá executar um POST nessa URL
- Deverão ser enviados name e email
- A validação desses dados deverá ser feita no próprio formulário HTML (Detalhes abaixo)
- Você poderá enviar o parametro redirectTo com um input hidden para direcionar o usuário para uma outra página após preenchimento
- Você poderá enviar o parametro debugMode com valor 'true' para testar o funcionamento sem salvar seus testes

## Configurando o formulário

Utilizando as propriedades method e action vamos configurar a maneira que o formulário envia os dados.

#### METHOD

Essa propriedade indica qual método será colocado no cabeçalho da requisição, nesse caso vamos colocar POST pois estamos criando um registro em nosso backend. Mais informações em https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods

#### ACTION

Essa propriedade indica para qual URL os dados serão enviados, esse dado será entregue a vocês assim que o assignmento começar.


```html
<form method="POST" action="URL do seu time">
</form>
```

## Validação

Ambos name e email deverão ser preenchidos obrigatóriamente, por isso vamos colocar a pripriedade required nos input. Dessa maneira impedimos que o formulário seja submetido sem o preenchimento desses campos.

#### Name

O nome deve ser completo, então vamos validar que seja um texto com pelo menos duas palavras. Para isso vamos usar o propriedade pattern com a RegExp `/\D{2,}\s[\D\s]{2,}$/` e a propriedade title para alterar a mensagem de erro caso o usuário não preencha corretamente.

```html
<input
  name="name"
  type="text"
  pattern="^\D{2,}\s[\D\s]{2,}$"
  title="Digite seu nome completo"
  required
/>
```

#### Email

Para garantir que o campo esteja no padrão correto de email (exemplo: xpto@xpto.xpto) vamos utilizar a propriedade type com o valor 'email', isso vai impedir que o formulário seja submetido caso o dado não esteja no padrão correto. Dessa vez não vamos precisar do title, pois a mensagem padrão já fica bem clara para o usuário.

```html
<input
  name="email"
  type="email"
  required
/>
```
## Hidden fields

Para facilitar a utilização desse backend, criamos 2 parametros de apoio que são ESPECIFICOS desse backend. Isso significa que eles não são padrão de qualquer formulário e não funcionarão em outros backends.

#### redirectTo

Esse parametro faz com que o backend redirecione o usuário para outra URL após a submissão do formulário, isso permite que vocês mandem o usuário para onde quiserem (Exemplo: Página de agradecimento, conteúdo exclusivo, etc...) pós cadastro.

Para utilizar basta adicionar um hidden input no formulário utilizando a propriedade type com valor 'hidden' e value com a URL que o usuário será redirecionado, exemplo:


```html
<input name="redirectTo" type="hidden" value="https://gama.academy" />
```

#### debugMode

Adicionamos esse parametro para ajudar vocês a testar o funcionamento do formulário sem precisar gerar 'lixo' na base. Quando ligado os dados enviados pelo formulário não serão salvos e não aparecerão no relatório final. NÂO ESQUEÇAM DE REMOVER ESSE PARAMETRO ANTES DE DIVULGAR A PÁGINA

```html
<input name="debugMode" type="hidden" value="true" />
```

## Submit

Para enviar o formulário precisamos de um botão de submit, quando o usuário clicá-lo o formulário será enviado. Exemplo:

```html
<input type="submit" />
```

## Exemplo completo

[Documento Exemplo](example.html)
