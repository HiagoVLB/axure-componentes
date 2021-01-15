# Axure-Projetos

Este respositório tem por objetivo:
- Disponibilizar os arquivos gerados pelo Axure de forma online no Heroku;
- Disponibilizar o template básico para utilização em novos projetos;
- Diisponibilizar uma biblioteca do Axure contendo Campos, Componentes e Telas para utilização nos projetos;
- Apresentar as motivações da protótipação ser realizada conforme o exemplo disponibilizado neste repositório;
- Apresentar as vantagens de se utilizar algumas metodologias (Painel Dinamico e Master) na prototiapação e possíveis problemas do uso exagerado.

## Heroku

#### Primeiro Deploy

Foi utilizado o Heroku para disponibilização dos códigos html etc gerados pelo Axure, seguem abaixos os passos para criação do servidor etc no Heroku:

- Acionar a opção "New" na página de "Apss"
- Sugiro utilizar algum tipo de padronização ao nome, por exemplo, no seguinte formato "SiglaDaEmpresa-SiglaSistema-prot" no campo "App name", a região pode deixar no default que é "United States", após isso acionar a opção "Create app";
- Para o Deploy acionar a aba "Deploy", colocar "Heroku git" como "Deployment Method", após isso seguir os passos referentes a "Install the Heroku CLI" e "Clone the repository";
- Depois de clonar o repositório copie os artefatos da pasta "Servidor" (não copiar a pasta em si só os arquivos dentro dela) para dentro da pasta do respositório do servidor que foi criado no Heroku;
- Os arquivos gerados pelo axure também podem ser disponibilizados em conjunto com o servidor, para isso coloque como pasta de geração a "Web". Portanto,  a pasta "Web" pode ser sempre a default na geração do Axure para cada projeto.

#### Acesso a Aplicação

Após essas etapas a aplicação terá sido disponibilizada no Heroku, podendo ser acessada através de sua URL, a qual está disponível no Heroku como "Open App" para acesso direto, mas que segue a seguinte lógica:

- https://NomeEscolhido.herokuapp.com/

Caso se tenha seguido o padrão de nomenclatura sugerido neste respositório, caso contrário como se pode verificar o nome em si da aplicação é o nome do App no Heroku.

## Axure

#### Template

para seguir garantir que os protótipos criados no Axure sigam o mesmo padrão sugiro a utilização de um arquivo template para os projetos, pois se existir uma arquitetura de referência ou algo deste tipo evita retrabalho e garante padronização, por exemplo:

- Prot - Template.rp

#### Biblioteca

Para biblioteca padrão de componentes, campos e telas utilize:

- Prot - Bliblioteca.rplib
  Tais artefatos irão diminuir o esforço (tempo) necessário para criação de novos projetos, além de garantir que todos estejam seguindo os mesmos padrões no Axure, facilitando a alteração de outros projetos por pessoas que não fizeram parte do projeto em seu levantamento se vir a acontecer.

#### Padrões - Painel Dincamico (Dynamic Panel)

Seguem abaixo as motivações da utilização do Painel Dinâmico:

- **Modal:** possibilitar apresentar as funcionalidades como modais;
- **Agrupamento:** todas as modais apresentadas através de uma funcionalidade ficam como Estados (State) centralizando em um local só e possibilitando trocar facilmente entre as modais mudando o Estado delas;
- **Arquitetura de Referência:** possibilitar que os protótipos apresentem um compontamente proxímo ou igual ao da aplicação;
- **Reutilização:** possibilitar a reutilização de um Painel Dinamico entre diferentes funcionalidades, pois muitas vezes dentro de um projeto CRUD (Create, Read, Update, Remove) utilizam as mesmas funcionalidades, portanto as ações disponibilizadas na consulta para cada registros tendem a serem as mesmas, por exemplo, "Informar Filtros, Alterar, Excluir, Ativar/Inativar e Visualizar Histórico". Logo, esse padrão tende a reduzir o tempo de prototipação;
- **Utilização de Componentes:** permitir utilizar Master (Componentes) dentro dos Paineis Dinamicos a fim de garantir que uma determinada funcionalidade que apresenta o mesmo comportamento entre diferentes entidades da aplicação possa ser facilmente se for o caso, tal qual ocorreria no próprio sistema ao ser programado;
- **Barra de Rolagem:** a utilização do Painel Dinamico no cadastro, alteração, avaliação etc permite a utilização de barra de rolagem, garantido que sempre será possível ver todos os campos e novamente apresentando um comportamento muito proxímo ao do sistema.

#### Padrões - Master (Componente)

Seguem abaixo as motivações da utilização da Master:

- **Componetizar:** garantir que os protótipos possuam componentes para as funcionalidades que de fato se repetem entre toda a aplicação. Sendo que certas partes do sistema, por exemplo, "menu lateral, header e fotter" são apresentadas em todas as funcionalidades existentes, portanto é interessante que sejam componentes sempre, caso contrário teriam que ser alterados em cada local que aparecem;
- **Agrupamento:** em certos casos podem ser utilizados componentes como uma forma de agrupar os campos se for o caso, por exemplo, para os campos do filtro da consulta. São casos que podem acabar não valendo tanto a pena no sentido de reutilização, mas que dependo do cenário podem facilitar mover partes das telas de local ou a possível reutilização no futuro, por exemplo, telas de cadastro/alteração com Master e regras de desabilitar campos aplicadas podem componetizar tais campos e permitir apresentá-los na funcionalidade Visualização e Avaliação (se na tela de avaliar mostrar os campos que a pessoa está avalaindo e se neles estiver contidos o do cadastro);
- **Compotamentos Gerais:** se vier a ocorrer um caso em que existem diversos campos atingidos por um determinado comportamento pode vir a ser o caso de componetizalos, pois isso facilitará a criação da regra de apresentação dentro do Axure. Porém, se deve tomar o cuidado para não sair criando componente para qualquer coisa devido a poucos campos que apresentam o mesmo comportamento, o idela que sejam pelo menos 8 para de fato compensar. Pois, a alteração de componentes leva a uma tela especifica deles não mostrando a tela de origem em conjunto com a alterção que se está fazendo nos componentes.

Seguem algumas considerações sobre a utilização de Master (componentes) que devem ser levadas em conta:

- **Perda de Referência:** o conteúdo dos componentes não possui referência com a tela que estão presentes, isso significa que apesar de ser possível aplicar comportamentos gerais a um componente através de outros campos/opções da funcionalidade, não é possível que a própria Master afete o que está fora dela, pois apesar de estar na funcionalidade ela não está de fato dentro daquela tela. Logo, por exemplo, botões de "Confirmar, Voltar e Prosseguir" nunca dariam certo, pois eles não conseguiriam apresentar um comportamento específico para a tela em que estão presentes, consequentemente esses campos acabam ficando sempre fora da Master na própria funcionalidade ou dentro do Painel Dinamico.
- **Telas dos Componentes:** é indicado ter uma pasta literalmente dentro do Axure em que todos os componentes utilizados possuam uma página dedicada para eles, pois apesar de isso não ser de fato necessário facilita para alguem que não está no projeto identificar todos os componentes que existem, além de facilitar a alteração deles se vir a ser o caso. Vale citar que não é interessante colocar componentes utilizados como Agrupamento ou de Comportamentos Gerais, pois apesar de terem sido criados como componentes eles em geral são especificos, porém se vier a ocorrer de não serem especificos seria interessante criar um subpasta "Componentes Especificos" para os casos em que esses componentes forem utilizados em mais de 1 funcionalidade.

#### Disposição e Tamanho dos Campos

É importante tentar seguir ao máximo o mesmo tamanho e disposição dos campos em cenários semelhantes, por exemplo, que ao acessar telas diferentes de cadastro a posição que os campos padrões estão seja igual, além disso, que o tamanho em si dos campos siga uma lógica comum, portanto que campos de Caixa de Texto e ComboBox, por exemplo, tenham a mesma altura e se uma tela possui 4 campos "por linha" que os proxímas linhas tenham os campos com exatamento o mesmo tamanho, pois é dessa forma que a aplicação se comporta.

#### Nome das Funcionalidades

O padrão para nomenclatura das funcionalidades no Axure é o seguinte:

- Página Principal;
- Consultar;
- Cadstrar/Alterar;
- Visualizar;
- Avaliar;
- Contato;
- Sobre;
- Emitir;
- Exportar.

Esses são exemplos de como nomear as telas em si no Axure. As funcionalidades devem ser agrupadas de acordo com o nome do Menu, por exemplo, "MRT, Tipologia, PPR, Qualificar etc", portanto abaixo está um exemplo de como ficaria na prática:

» Mercado de Terras (Menu Principal)\
»» Nome do Menu Principal \
»»» Consultar\
»»» Cadastrar/Alterar\
»» Nome do Submenu (Especificação Funcional) \
»»» Consultar\
»»» Cadastrar/Alterar\
»» Nome do Submenu (Especificação Funcional) \
»»» Emitir

Se for o caso pode ser acrescentado o nome da Especificação Funcional antes de cada funcionalidade, pois dessa forma as urls no Heroku e as abas do Axure vão ficar mais fáceis de identificar, porém pessoalmente prefiro deixar mais clean (limpo) o nome das funcionalidades.

## Links Úteis
- **[Página Oficial de Icones Angular](https://material.io/resources/icons/?icon=add&style=baseline)**</br>
- **[Ferramenta para Gerar Icones do Angular Coloridos](https://materialdesignicons.com/)**</br>
- **[Versão do Axure Utilizada (7.0)](https://www.axure.com/release-history/rp7)**</br>
- **[Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)**</br>
