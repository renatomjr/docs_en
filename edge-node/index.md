

# Edge **Node**

O Azion Edge Node permite a criação de uma infraestrutura edge própria, habilitando a instalação de serviços e recursos em real-time.

> 1. [Instalar](#instalar)
> 2. [Visualizar](#Visualizar)
> 3. [Autorizar](#autorizar)
> 4. [Configurações principais](#configurações-principais)
> 5. [Serviços](#serviços)

---

## 1. Instalar {#instalar}

A instalação do Edge Node é, basicamente, dividida em 3 etapas: 1- Geração de uma credencial para executar as ações; 2- Instalação do framework nos devices e; 3- autenticação no device (pós framework) com a credencial criada.

### 1.1 Geração da credencial {#geracao-credencial}

Para gerar a credencial necessária para autenticação dos seus edge nodes, os seguintes passos devem ser executados:
	1- Acessar o [Real-Time Manager](https://manager.azion.com/);
	2- No menu superior direito, acessar a página [Credentials]();
	3- Clicar no botão Add;
	4- Preencher os campos necessários e clicar no botão Save:
		**Description:** Descreva, por exemplo, como ou por quem a credencial será utilizada;
		**Teams:** Vincule as permissões de ações que a credencial poderá exercer;

**Observação:** O Token será gerado após a credencial ser salva.

### 1.2 Código para instalação {#codigo-instalacao}

A instalação do Edge Node acontece por meio do script de instalação abaixo:

ˋˋˋapt-get ...ˋˋˋ

Via linha de comando, você deve inserir o código disponibilizado, para que seu device instale o framework core necessário para iniciar a executar suas aplicações.

Confira a listagem de plataformas/arquiteturas compatíveis com o Azion Edge Node.

Arquitetura |
:-------------
CentOS



### 1.3 Autenticação {#autenticacao}

Durante a instalação do framework, será necessário informar um Token para seu device conseguir se autenticar na Azion e iniciar todo o processo. Você deve informar o token fornecido ou criado nas credenciais, item **1.1 Geração da credencial**.

Após informar o Token e receber a confirmação de que o seu node foi criado, será necessário autorizá-lo e configura-lo no [Real-Time Manager](https://manager.azion.com/).

---

## 2. Visualizar {#visualizar}

O Azion E...

---

## 3. Autorizar {#autorizar}

O Azion E...

---

## 4. Configurações principais {#configurações-principais}

O Azion E...

---

## 5. Serviços {#serviços}

O Azion E...

---

Didn't find what you were looking for? [Open a support ticket.](https://tickets.azion.com/)

[Edit this page](https://github.com/aziontech/docs_en/edit/master/edge-firewall/index.md) on GitHub.