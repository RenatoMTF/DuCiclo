# TRABALHO 01:  DuCiclo
Trabalho desenvolvido durante a disciplina de BD1

# Sumário

### 1. COMPONENTES<br>
Integrantes do grupo<br>
Gabrielle Duda: gabiabacduda@gmail.com<br>
Renato Marques: renatomtf26@gmail.com<br>
<br>

### 2.INTRODUÇÃO E MOTIVAÇÃO<br>
> Em meio a toda a crise mundial causada pela pandemia do Coronavírus, muitos lojistas tiveram que reinventar suas vendas presencias para não serem afetados. Segundo a ValorInveste o crescimento no setor de delivery beira 94%, e com isso uma nova oportunidade surge para quem perdeu seu emprego em meio a toda essa situação: trabalhar com entregas de mercadorias. O DuCiclo é um aplicativo que visa ajudar e crescer junto com essa nova onda de superação, interligando pequenos e grandes lojistas de diversos setores com entregadores motivados a ganharem uma nova renda. O sistema proposto é mais que um app de logistica de entrega, a ideia é criar oportunidades! O entregaDu, ao adentrar na plataforma recebe um codnome carinhoso e tambem a chance de trabalhar seja qual for o seu meio de locomoção (carro, moto, bicicleta, patins, cavalo), basta se cadastrar e se empenhar de acordo com sua possibilidade. Um cliente com sua mercadoria, o vendedor com sua venda, e o entregador com sua nova jornada.
 

### 3.MINI-MUNDO<br>

A plataforma DuCiclo vem com a ideia de interligar motoboys, lojistas e clientes, com o objetivo de entregar com segurança qualquer coisa que possa ser carregada de maneira segura. A missão da plataforma é resolver o problema de lojistas que agora atendem delivery mas não possuem serviços próprios de entrega de mercadoria, além de gerar empregos para entregadores que não possuam carro ou moto para realizar a entrega.  Primeiramente ocorre um cadastro no aplicativo onde lojista se cadastra com CNPJ ou CPF, nome do estabelecimento, Razão social, nome do responsável, telefone, endereço da loja. Os entregadores podem ser motoboys, ciclistas, ou qualquer forma de locomoção importante é cadastrar nome, cpf, meio de locomoção e descrição, área geográfica de atuação,  telefone para contato, email. A área geográfica vai ajudar a delimitar a atuação do entregador e assim possibilitar maior segurança no prazo para entrega das encomendas. O cliente tambem se cadastra com nome, CPF, telefone, email, podendo assim acompanhar a sua entrega. O lojista cadastra a encomenda (nome,produto,descrição, valor, quantidade, data da entrega, data de retirada, hora da entrega, hora de retirada) e estas são agrupadas por bairros próximos. O aplicativo apresenta ao entregador, de acordo com sua área, as entregas disponiveis para o dia seguinte, importante salientar que para o agrupamento de área as entregas tem prazo de 24horas. Ao aceitar é criado o pedido, que interliga o cliente cadastrado previamente (importante o logista orientar ao cliente essa necessidade), ao entregaDu e a encomenda cadastrada pelo lojista. Entega feita então se avalia todos os critérios por todos os envolvidos e assim a plataforma ganha em melhoria de atuação.

### 4.PROTOTIPAÇÃO, PERGUNTAS A SEREM RESPONDIDAS E TABELA DE DADOS<br>
#### 4.1 RASCUNHOS BÁSICOS DA INTERFACE (MOCKUPS)<br>
Neste ponto a codificação não e necessária, somente as ideias de telas devem ser criadas, o princípio aqui é pensar na criação da interface para identificar possíveis informações a serem armazenadas ou descartadas <br>

Sugestão: https://balsamiq.com/products/mockups/<br>

![Alt text](https://github.com/discipbd1/trab01/blob/master/balsamiq.png?raw=true "Title")
![Arquivo PDF do Protótipo Balsamiq feito para Aplicativo DuCiclo](https://github.com/GabrielleDuda/DuCiclo/blob/main/Prototipo-%20Renato%20Marques%20e%20Gabrielle%20Azevedo.pdf?raw=true "Aplicativo DuCiclo")
#### 4.2 QUAIS PERGUNTAS PODEM SER RESPONDIDAS COM O SISTEMA PROPOSTO?
      
> O aplicativo DuCiclo precisa inicialmente dos seguintes relatórios:
* Relatório de entregadores por bairro ou cidade.
* Relatório de compradores por bairro ou cidade.
* Relatorio de entregas por período.
* Relatório de entregadores com mais entregas por período.
* Relatório de lojistas com mais vendas por período.
* Relatório de bairros que mais possuem pedidos de delivery

 
#### 4.3 TABELA DE DADOS DO SISTEMA:
    a) Esta tabela deve conter todos os atributos do sistema e um mínimo de 10 linhas/registros de dados.
    b) Esta tabela tem a intenção de simular um relatório com todos os dados que serão armazenados 
    
![Exemplo de Tabela de dados da Empresa Devcom](https://github.com/discipbd1/trab01/blob/master/arquivos/TabelaEmpresaDevCom_sample.xlsx?raw=true "Tabela - Empresa Devcom")
    
    
### 5.MODELO CONCEITUAL<br>
![Alt text](https://github.com/GabrielleDuda/DuCiclo/blob/main/conceitual%20-%20DUCICLO.png?raw=true "Modelo Conceitual")
    
    
        
    
#### 5.1 Validação do Modelo Conceitual
    [Grupo01]: [Nomes dos que participaram na avaliação]
    [Grupo02]: [Nomes dos que participaram na avaliação]

#### 5.2 Descrição dos dados 

LOJISTA: Tabela que armazena as informações relativa a loja que necessita da entrega. 
    nomefantasia: nome popularizado da loja
    CNPJ: número de identicação da loja de caracter jurídico
    razaosocial: nome jurídico da loja
    nome_resp: nome do funcionário que responde pela loja
    telefone: número para comunicação com o lojista
    id_lojista integer PRIMARY KEY

ENTREGADU (
    cod_entregador integer PRIMARY KEY,
    nome varchar,
    telefone char,
    area_geografica varchar,
    email varchar,
    meio_transporte varchar,
    data_nascimento date,
    cpf char
);

CREATE TABLE CLIENTE (
    cod_cliente integer PRIMARY KEY,
    nome varchar,
    telefone varchar
);

CREATE TABLE ENCOMENDA (
    cod_encomenda integer PRIMARY KEY,
    nomeprod varchar,
    descricao varchar,
    valor decimal,
    quantidade int,
    data_entrega date,
    hora_entrega timestamp,
    hora_retirada timestamp,
    FK_ENTREGADU integer,
    FK_LOJISTA_ integer
);

CREATE TABLE PEDIDO_entrega (
    fk_encomenda integer,
    cod_pedido integer PRIMARY KEY,
    fk_ENTREGADU integer,
    fk_CLIENTE integer
);

CREATE TABLE ENDERECO (
    logradouro varchar,
    número int,
    bairro varchar,
    cep char,
    cidade varchar,
    complemento varchar,
    refencia varchar,
    id_lojista integer,
    id_cliente integer

### 6	MODELO LÓGICO<br>

![Alt text](https://github.com/GabrielleDuda/DuCiclo/blob/main/logico%20-%20DUCICLO.png?raw=true "Modelo LÓGICO")


### 7	MODELO FÍSICO<br>
        a) inclusão das instruções de criacão das estruturas em SQL/DDL 
        (criação de tabelas, alterações, etc..) 
        
       
### 8	INSERT APLICADO NAS TABELAS DO BANCO DE DADOS<br>
        a) inclusão das instruções de inserção dos dados nas tabelas criadas pelo script de modelo físico
        (Drop para exclusão de tabelas + create definição de para tabelas e estruturas de dados + insert para dados a serem inseridos)
        b) Criar um novo banco de dados para testar a restauracao 
        (em caso de falha na restauração o grupo não pontuará neste quesito)
        c) formato .SQL


### 9	TABELAS E PRINCIPAIS CONSULTAS<br>
    OBS: Incluir para cada tópico as instruções SQL + imagens (print da tela) mostrando os resultados.<br>
#### 9.1	CONSULTAS DAS TABELAS COM TODOS OS DADOS INSERIDOS (Todas) <br>

># Marco de Entrega 01: Do item 1 até o item 9.1<br>

#### 9.2	CONSULTAS DAS TABELAS COM FILTROS WHERE (Mínimo 4)<br>
#### 9.3	CONSULTAS QUE USAM OPERADORES LÓGICOS, ARITMÉTICOS E TABELAS OU CAMPOS RENOMEADOS (Mínimo 11)
    a) Criar 5 consultas que envolvam os operadores lógicos AND, OR e Not
    b) Criar no mínimo 3 consultas com operadores aritméticos 
    c) Criar no mínimo 3 consultas com operação de renomear nomes de campos ou tabelas

#### 9.4	CONSULTAS QUE USAM OPERADORES LIKE E DATAS (Mínimo 12) <br>
    a) Criar outras 5 consultas que envolvam like ou ilike
    b) Criar uma consulta para cada tipo de função data apresentada.

#### 9.5	INSTRUÇÕES APLICANDO ATUALIZAÇÃO E EXCLUSÃO DE DADOS (Mínimo 6)<br>
    a) Criar minimo 3 de exclusão
    b) Criar minimo 3 de atualização

#### 9.6	CONSULTAS COM INNER JOIN E ORDER BY (Mínimo 6)<br>
    a) Uma junção que envolva todas as tabelas possuindo no mínimo 2 registros no resultado
    b) Outras junções que o grupo considere como sendo as de principal importância para o trabalho

#### 9.7	CONSULTAS COM GROUP BY E FUNÇÕES DE AGRUPAMENTO (Mínimo 6)<br>
    a) Criar minimo 2 envolvendo algum tipo de junção

#### 9.8	CONSULTAS COM LEFT, RIGHT E FULL JOIN (Mínimo 4)<br>
    a) Criar minimo 1 de cada tipo

#### 9.9	CONSULTAS COM SELF JOIN E VIEW (Mínimo 6)<br>
        a) Uma junção que envolva Self Join (caso não ocorra na base justificar e substituir por uma view)
        b) Outras junções com views que o grupo considere como sendo de relevante importância para o trabalho

#### 9.10	SUBCONSULTAS (Mínimo 4)<br>
     a) Criar minimo 1 envolvendo GROUP BY
     b) Criar minimo 1 envolvendo algum tipo de junção

># Marco de Entrega 02: Do item 9.2 até o ítem 9.10<br>

### 10 RELATÓRIOS E GRÁFICOS

#### a) análises e resultados provenientes do banco de dados desenvolvido (usar modelo disponível)
#### b) link com exemplo de relatórios será disponiblizado pelo professor no AVA
#### OBS: Esta é uma atividade de grande relevância no contexto do trabalho. Mantenha o foco nos 5 principais relatórios/resultados visando obter o melhor resultado possível.

    

### 11	AJUSTES DA DOCUMENTAÇÃO, CRIAÇÃO DOS SLIDES E VÍDEO PARA APRESENTAÇAO FINAL <br>

#### a) Modelo (pecha kucha)<br>
#### b) Tempo de apresentação 6:40 

># Marco de Entrega 03: Itens 10 e 11<br>
<br>
<br>
<br> 



### 12 FORMATACAO NO GIT:<br> 
https://help.github.com/articles/basic-writing-and-formatting-syntax/
<comentario no git>
    
##### About Formatting
    https://help.github.com/articles/about-writing-and-formatting-on-github/
    
##### Basic Formatting in Git
    
    https://help.github.com/articles/basic-writing-and-formatting-syntax/#referencing-issues-and-pull-requests
    
    
##### Working with advanced formatting
    https://help.github.com/articles/working-with-advanced-formatting/
#### Mastering Markdown
    https://guides.github.com/features/mastering-markdown/

    
### OBSERVAÇÕES IMPORTANTES

#### Todos os arquivos que fazem parte do projeto (Imagens, pdfs, arquivos fonte, etc..), devem estar presentes no GIT. Os arquivos do projeto vigente não devem ser armazenados em quaisquer outras plataformas.
1. <strong>Caso existam arquivos com conteúdos sigilosos<strong>, comunicar o professor que definirá em conjunto com o grupo a melhor forma de armazenamento do arquivo.

#### Todos os grupos deverão fazer Fork deste repositório e dar permissões administrativas ao usuário do git "profmoisesomena", para acompanhamento do trabalho.

#### Os usuários criados no GIT devem possuir o nome de identificação do aluno (não serão aceitos nomes como Eu123, meuprojeto, pro456, etc). Em caso de dúvida comunicar o professor.


Link para BrModelo:<br>
http://www.sis4.com/brModelo/download.html
<br>


Link para curso de GIT<br>
![https://www.youtube.com/curso_git](https://www.youtube.com/playlist?list=PLo7sFyCeiGUdIyEmHdfbuD2eR4XPDqnN2?raw=true "Title")


