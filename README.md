[checkmark]: https://raw.githubusercontent.com/mozgbrasil/mozgbrasil.github.io/master/assets/images/logos/logo_32_32.png "MOZG"
![valid XHTML][checkmark]

[getcomposer]: https://getcomposer.org/
[uninstall-mods]: https://getcomposer.org/doc/03-cli.md#remove
[tickets]: https://cerebrum.freshdesk.com/support/tickets/new
[preco]: http://www.cerebrum.com.br/preco/
[requerimentos]: http://mozgbrasil.github.io/requerimentos/
[artigo-composer]: http://mozg.com.br/ubuntu/composer
[ioncube-loader]: http://www.ioncube.com/loaders.php
[acordo]: http://mozg.com.br/acordo-licenca-usuario-final/

# Mozg\Customer

## Sinopse

Personalização dos formulários de clientes

## Demonstração

<a href="http://mozg.com.br/assets/images/docs/2017-06-01-magento-customer.pdf" target="_blank"><img src="http://mozg.com.br/assets/images/docs/2017-06-01-magento-customer.gif" /></a>

## Motivação

Atender o mercado de módulos para Magento oferecendo melhorias e um excelente suporte

## Suporte / Dúvidas

Para obter o devido suporte [Clique aqui][tickets], relatando o motivo da ocorrência o mais detalhado possível e anexe o print da tela para nosso entendimento

## Preço

[Clique aqui][preco]

## Recursos

* Montagem de formulário personalizado

* Suporte a máscaras

* Suporte a validadores

* Preenchimento do endereço pelo CEP

* Checagem de documento "CPF" ou "CNPJ" impedindo registro duplicado

## Suporte / Dúvidas

Para obter o devido suporte [Clique aqui][tickets], relatando o motivo da ocorrência o mais detalhado possível e anexe o print da tela para nosso entendimento

## Preço

[Clique aqui][preco]

## Instalação - Atualização - Desinstalação - Desativação

--

Este módulo destina-se a ser instalado usando o [Composer][getcomposer]

Execute o seguinte comando no terminal, para visualizar a existencia do Composer e sua versão

	composer --version

Caso não tenha o Composer em seu ambiente, sugiro ler o seguinte artigo [Clique aqui][artigo-composer]

--

É necessário que o servidor tenha o suporte a extensão [ionCube PHP Loader][ioncube-loader]

Para visualizar se essa extensão está ativa em seu servidor

Certique se da presença do arquivo phpinfo.php na raiz do seu projeto

	<?php phpinfo(); ?>

Caso não exista o arquivo phpinfo.php na raiz do projeto Magento, crie o mesmo adicionado o conteúdo acima

Acesse o arquivo pelo browser

Em seguida pesquise pelo termo "ionCube PHP Loader"

Caso o seu servidor não tenha o suporte a extensão, [Clique aqui][ioncube-loader]

Em "Loader Downloads API", efetue download do pacote compatível com o seu servidor

Descompacte o pacote e faça upload do arquivo "loader-wizard.php" para seu servidor, onde será demonstrado o passo a passo para a ativação da extensão

[Clique aqui](https://youtu.be/GZ2J6MLkko4) para ver os processos executados

--

Para utilizar o(s) módulo(s) da MOZG é necessário aceitar o [Acordo de licença do usuário final][acordo]

--

Sugiro manter um ambiente de testes para efeito de testes e somente após os devidos testes aplicar os devidos procedimento no ambiente de produção

--

Sugiro efetuar backup da plataforma Magento e do banco de dados

--

Antes de efetuar qualquer atualização no Magento sempre mantenha o Compiler e o Cache desativado

--

Certique se da presença do arquivo composer.json na raiz do seu projeto Magento e que o mesmo tenha os parâmetros semelhantes ao modelo JSON abaixo

	{
	  "minimum-stability": "dev",
	  "prefer-stable": true,
	  "license": [
	    "proprietary"
	  ],
	  "repositories": [
	    {
	      "type": "composer",
	      "url": "https?://packages.firegento.com"
	    }
	  ],
	  "extra": {
	    "magento-root-dir": "./",
	    "magento-deploystrategy": "copy",
	    "magento-force": true
	  }
	}

Caso não exista o arquivo composer.json na raiz do projeto Magento, crie o mesmo adicionado o conteúdo acima

### Para instalar o módulo execute o comando a seguir no terminal do seu servidor no diretório do seu projeto

	composer require mozgbrasil/magento-customer-php56:dev-master

Você pode verificar se o módulo está instalado, indo ao backend em:

	STORES -> Configuration -> ADVANCED/Advanced -> Disable Modules Output

--

### Para atualizar o módulo execute o comando a seguir no terminal do seu servidor no diretório do seu projeto

Antes de efetuar qualquer processo que envolva atualização no Magento é recomendado manter o Compiler e Cache desativado

	composer clear-cache && composer update

Na ocorrência de erro, renomeie a pasta /vendor/mozgbrasil e execute novamente

Para checar a data do módulo execute o seguinte comando

	grep -ri --include=*.json 'time": "' ./vendor/mozgbrasil

--

### Para [desinstalar][uninstall-mods] o módulo execute o comando a seguir no terminal do seu servidor no diretório do seu projeto

	composer remove mozgbrasil/magento-customer-php56 && composer clear-cache && composer update

--

### Para desativar o módulo

1. Antes de efetuar qualquer processo que envolva atualização sobre o Magento é necessário manter o Compiler e Cache desativado

2. Caso queira desativar os módulos da MOZG renomeie a seguinte pasta app/code/local/Mozg

A desativação do módulo pode ser usado para detectar se determinada ocorrência tem relação com o módulo

--

## Como configurar o método

Para configurar o método, acesse no backend em:

	∞ MOZG ∞ -> Cadastro de Clientes -> Cadastro de Clientes - (powered by MOZG)

Você terá os campos a seguir

### • **Ativar campos de endereço em /customer/account/create/**

Exibe os devidos campos relativo ao endereço

### • **Ativar suporte aos formulários**

Ao ativar o recurso deve ser utilizado o template presente no módulo, podemos visualizar que no template temos:

- Mascara aos campos: zip "cep", telephone, fax, taxvat "geralmente usado para armazenar o cpf ou cnpj", cpf "modelo de possivel novo atributo", cnpj "modelo de possivel novo atributo"

- Validador aos campos: zip, street_1, cpf, cnpj, taxvat

- Preenchimento do endereço pelo CEP

- Preenchimento automático para testes

- Reordenação de campos

### • **Armazenamento do endereço**

#### • **A opção armazenamento padrão**

Armazena nos 2 campos nativos com os seguintes rótulos: 

- Para o primeiro campo nativo *

endereço, numero, complemento

* Embora seja criado exibido 3 campos fictícios o armazenamento é feito no primeiro campo nativo de endereço no Magento

- Para o segundo campo nativo

bairro

#### • **A opção armazenamento separado**

No uso dessa opção, acesse no backend em:

	Sistema -> Configuração -> Clientes -> Configuração -> Opções de Nome e Endereço

Altere para o campo "Número de linhas em um endereço de rua" para 4

Armazena nos 4 campos nativos com os seguintes rótulos: 

- Para o primeiro campo nativo

endereço

- Para o segundo campo nativo

numero

- Para o terceiro campo nativo

complemento

- Para o quarto campo nativo

bairro

#### Adicionar novos atributos ao formulário

1)

Pode ser utilizado qualquer módulo de terceiros para a criação de atributos de clientes

https://www.magentocommerce.com/magento-connect/catalogsearch/result/?id=&s=7&pl=0&eb=0&hp=0&q=customer+attribute&t=1&p=1

Caso queira utilize esse que está nessa lista como 1 dos mais relevantes nesse quesito

https://www.magentocommerce.com/magento-connect/manage-customer-attributes-1.html

	composer require connect20/clarion_customerattribute

No uso do módulo CustomerAttribute

Podemos acessar o recurso pelo menu no backend do Magento: Clientes -> Gerenciar atributos

Tenha cautela no uso desse recurso

Recomendo o uso apenas para a criação de novos atributos

Como os módulos de gerenciamento de atributos "free" não oferece de forma gratuita o recurso de salvar os atributos no /checkout/ o nosso módulo contem recurso para essa necessidade

2)

Para aplicar o suporte do novo atributo ao formulário

Deve ser inserido no formulário o campo tendo o mesmo identificador usado na criação do atributo

Para a exibição de algum atributo contendo algum tipo de condição sempre será necessário escrever a devida programação, nessa necessidade me informe sua necessidade

<a href="http://mozg.com.br/assets/images/docs/2017-04-25-clarion-mozg.pdf" target="_blank"><img src="http://mozg.com.br/assets/images/docs/2017-04-25-clarion-mozg.gif" /></a>

## Perguntas mais frequentes "FAQ"

### Como personalizar os formulários de cadastro

Você pode personalizar o arquivo do formulário editando o mesmo e em seguida adicionado o arquivo na estrutura de diretório do seu template

A seguir aplicamos o suporte a um template

cp -r app/design/frontend/base/default/template/mozg_customer/ app/design/frontend/smartwave/porto/template

### Como personalizar o formulário de criação de conta em /customer/account/create/

Deve ser ativado o Debug nativo do Magento a fim de ser exibido o caminho do arquivo phtml

Caso tenha o módulo CustomerAttribute, edite na configuração do módulo para desativar, pois esse módulo aplicado o suporte aos formulários

Nunca devemos editar o arquivo disponibilizado pelo módulo, pois quando houver uma atualização o mesmo será sobrescrito

Devemos criar a mesma estrutura de diretório para o nosso template

Você deve levar em consideração o caminho exibido no debug do seu projeto

Como o debug ativo em meu projeto exibiu o seguinte caminho

frontend/base/default/template/mozg_customer/customer/form/register.phtml

Nessa pasta temos o arquivo modelo que iremos usar como base

E o template nativo está localizado em

/app/design/frontend/rwd/default/template

Então devo ter a seguinte estrutura

/app/design/frontend/rwd/default/template/mozg_customer/customer/form/register.phtml

### Como personalizar o formulário de criação de conta em /customer/account/edit/

Deve ser ativado o Debug nativo do Magento a fim de ser exibido o caminho do arquivo phtml

Caso tenha o módulo CustomerAttribute, edite na configuração do módulo para desativar, pois esse módulo aplicado o suporte aos formulários

Nunca devemos editar o arquivo disponibilizado pelo módulo, pois quando houver uma atualização o mesmo será sobreescrevido

Devemos criar a mesma estrutura de diretório para o nosso template

Você deve levar em consideração o caminho exibido no debug do seu projeto

Como o debug ativo em meu projeto exibiu o seguinte caminho

frontend/base/default/template/mozg_customer/customer/form/edit.phtml

Nessa pasta temos o arquivo modelo que iremos usar como base

E o template nativo está localizado em

/app/design/frontend/rwd/default/template

Então devo ter a seguinte estrutura

/app/design/frontend/rwd/default/template/mozg_customer/customer/form/edit.phtml

### Como personalizar o formulário de criação de conta em /checkout/

Deve ser ativado o Debug nativo do Magento a fim de ser exibido o caminho do arquivo phtml

Caso tenha o módulo CustomerAttribute, edite na configuração do módulo para desativar, pois esse módulo aplicado o suporte aos formulários

Nunca devemos editar o arquivo disponibilizado pelo módulo, pois quando houver uma atualização o mesmo será sobreescrevido

Devemos criar a mesma estrutura de diretório para o nosso template

Você deve levar em consideração o caminho exibido no debug do seu projeto

1.

Como o debug ativo em meu projeto exibiu o seguinte caminho

frontend/base/default/template/mozg_customer/persistent/checkout/onepage/billing.phtml

Nessa pasta temos o arquivo modelo que iremos usar como base

E o template nativo está localizado em

/app/design/frontend/rwd/default/template

Então devo ter a seguinte estrutura

/app/design/frontend/rwd/default/template/mozg_customer/persistent/checkout/onepage/billing.phtml


2.

Como o debug ativo em meu projeto exibiu o seguinte caminho

frontend/base/default/template/mozg_customer/checkout/onepage/shipping.phtml

Nessa pasta temos o arquivo modelo que iremos usar como base

E o template nativo está localizado em

/app/design/frontend/rwd/default/template

Então devo ter a seguinte estrutura

/app/design/frontend/rwd/default/template/mozg_customer/checkout/onepage/shipping.phtml

### Como instalar o módulo de compra em 1 passo

Acesse

https://github.com/mozgbrasil/magento-iwd-opc#mozgiwd_opc

### Como alterar a tradução de algum campo ?

Caso queira alterar a tradução de algum campo utilize a ferramenta nativa do Magento "tradução em linha" indo ao backend em:

	STORES -> Configuration -> ADVANCED/Developer -> Translate Inline

### Modificando a tradução do módulo para o template

Cada módulo tem o seu arquivo de tradução com a mesma nomenclatura do módulo

Os arquivos de tradução para português do Brasil no Magento é armazenado no diretório  

	/app/locale/pt_BR/

Recomendo não editar os arquivos nesse diretório pois em uma nova atualização de módulo esse arquivo deve ser atualizado com as informações do módulo

Na necessidade de trocar algum item

Edite o arquivo translate.csv presente no diretório do seu template para ser exibido um novo resultado

	/app/design/frontend/default/default/locale/pt_BR/translate.csv

Caso não exista a estrutura "/locale/pt_BR/translate.csv" em seu template apenas crie o arquivo nessa estrutura de diretório

Obs.

No Windows ou Mac sugiro usar o programa UltraEdit para edição do arquivo, dessa forma será mantido a codificação do arquivo em UTF-8

### Sobre o campo "Profissão"

Informo que tem alguns item no pacote de tradução do MarioSam que está equivocado em 

/app/locale/pt_BR/Mage_Api2.csv:"Company","Profissão"  
/app/locale/pt_BR/Mage_Customer.csv:"Company","Profissão"  
/app/locale/pt_BR/Mage_Checkout.csv:"Company","Profissão"

Edite os arquivos e atualize "Profissão" para "Empresa"

### Sobre separação e armazenamento dos dados de endereço

O nosso módulo contem a separação dos dados de endereço

Mas o armazenamento é feito no padrão nativo do Magento

Armazenando da seguinte forma

Para o atributo de endereço de clientes

"street_1" = logradouro com número e/ou complemento

"street_2" = Bairro

Quando utilizado o banco de dados demonstrativo ou "sample_data"

Vemos preenchido para o campo "street_1"

10441 Jefferson Blvd, Suite 200

Representando o número o logradouro e nesse caso também o complemento, ambas informações armazenada no atributo "street_1"

Eu não recomendo o procedimento que seria separar o número do endereço para o atributo "street_2" pois pode gerar problemas de formatação e em integrações

## Contribuintes

Equipe Mozg

## License

[Comercial License](LICENSE.txt)

## Badges

[![Join the chat at https://gitter.im/mozgbrasil](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/mozgbrasil/)
[![Latest Stable Version](https://poser.pugx.org/mozgbrasil/magento-customer-php56/v/stable)](https://packagist.org/packages/mozgbrasil/magento-customer-php56)
[![Total Downloads](https://poser.pugx.org/mozgbrasil/magento-customer-php56/downloads)](https://packagist.org/packages/mozgbrasil/magento-customer-php56)
[![Latest Unstable Version](https://poser.pugx.org/mozgbrasil/magento-customer-php56/v/unstable)](https://packagist.org/packages/mozgbrasil/magento-customer-php56)
[![License](https://poser.pugx.org/mozgbrasil/magento-customer-php56/license)](https://packagist.org/packages/mozgbrasil/magento-customer-php56)
[![Monthly Downloads](https://poser.pugx.org/mozgbrasil/magento-customer-php56/d/monthly)](https://packagist.org/packages/mozgbrasil/magento-customer-php56)
[![Daily Downloads](https://poser.pugx.org/mozgbrasil/magento-customer-php56/d/daily)](https://packagist.org/packages/mozgbrasil/magento-customer-php56)
[![Reference Status](https://www.versioneye.com/php/mozgbrasil:magento-customer-php56/reference_badge.svg?style=flat-square)](https://www.versioneye.com/php/mozgbrasil:magento-customer-php56/references)
[![Dependency Status](https://www.versioneye.com/php/mozgbrasil:magento-customer-php56/1.0.0/badge?style=flat-square)](https://www.versioneye.com/php/mozgbrasil:magento-customer-php56/1.0.0)

:cat2:
