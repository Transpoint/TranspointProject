# TRABALHO 01:  Transpoint
Trabalho desenvolvido durante a disciplina de BD

# Sumário

### 1. COMPONENTES<br>
Integrantes do grupo<br>
André Martins: objetovazio@gmail.com<br>
Elimar Macena: elimar.macena@gmail.com<br>
Hellesandro Gonzaga: hellesandro@hotmail.com<br>
Serenna Ferrari: serenna.ferrari@hotmail.com<br>

### 2.INTRODUÇÃO E MOTIVAÇAO<br>
Este documento contém a especificação do projeto do banco de dados Transpoint 
<br>e com a motivação de facilitar o uso do transporte público. <br>

### 3.MINI-MUNDO<br>
&emsp; A ideia do projeto se baseia no pagamento de passagem do sistema Transcol via celular e na efetuação de recarga no mesmo, utilizando as coordenadas do ônibus toda vez que uma pessoa efetua um pagamento pelo aplicativo. <br>
&emsp; Uma pessoa tem um cadastro onde consta seu nome, CPF e data de nascimento. Ela pode se enquadrar em 4 modalidades distintas: gratuidade, estudante, normal e idoso. <br>
&emsp; No sistema temos o histórico do saldo de cada usuário, monitorando as datas de liberação da próxima compra, baseando na data da última compra e o saldo atual. Ao realizar o pagamento de uma passagem, é salvo o saldo anterior e a data do pagamento dessa passagem. <br>
&emsp; Aliado ao pagamento da passagem, o local do ônibus onde foi constatado o pagamento também é coletado, sendo necessário assim identificar qual coletivo em questão, pela sua linha e seu local de partida e destino. <br>
&emsp; Para o recarregamento do saldo diretamente do celular se faz necessário do cadastramento do cartão, um cartão possui bandeira, nome e CPF (não sendo necessariamente o mesmo da pessoa cadastrada no sistema), CVV e número do cartão. <br><br>


### 4.RASCUNHOS BÁSICOS DA INTERFACE (MOCKUPS)<br>
Neste ponto a codificação não e necessária, somente as ideias de telas devem ser criadas, o princípio aqui é pensar na criação da interface para identificar possíveis informações a serem armazenadas ou descartadas.<a href="https://github.com/Transpoint/TranspointProject/blob/master/Transpoint.pdf"> Mockup </a><br>

#### 4.1 TABELA DE DADOS DO SISTEMA:
   <a href="https://github.com/Transpoint/TranspointProject/blob/master/tabelaTransPointF.xlsx"><img src="https://github.com/Transpoint/TranspointProject/blob/master/tabela_transpoint.PNG" title="Tabela do sistema" /></a>
   
### 5.MODELO CONCEITUAL<br>
    
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Modelos/Modelo%20Conceitual/Modelo%20Conceitual.jpg "Modelo Conceitual")
    
    B) NOTACAO UML (Caso esteja fazendo a disciplina de analise)
    C) QUALIDADE 
        Garantir que a semântica dos atributos seja clara no esquema
        Criar o esquema de forma a garantir a redução de informação redundante, possibilidade de valores null, 
        e tuplas falsas
    
#### 5.1 Validação do Modelo Conceitual
    [IPAO]: [Yan de Paula, Lucas Gomes, Tadeu da Penha, Ewerson Vieira]
    [GeMan]: [Gabriel Marchezi, Helen França, Olavo Curátola]

#### 5.2 DECISÕES DE PROJETO
    
    Campo Coordenadas:  A utilização de varchar é justificada pela opção de usar coordenadas geográficas para localização dos coletivos ao invés de endereços, facilitando a manipulação e evitando conflitos com nomes de ruas iguais em pontos diferentes. <br>
    

#### 5.3 DESCRIÇÃO DOS DADOS 

Tabela PESSOA: Tabela que armazena informações referente aos usuários do aplicativo.<br>
* cod_pessoa: (CHAVE PRIMARIA) Campo que armazena um número único identificador da pessoa.<br>
* nome_pessoa: Campo que armazena o nome da pessoa.<br>
* cpf: Campo que armazena o número de Cadastro de Pessoa Física para cada usuário.<br>
* data_nasc: Campo que armazena a data de nascimento do usuário.<br>

Tabela MODALIDADE: Tabela que armazena informações de classes que cada usuário pertence.<br>
* cod_modalidade: (CHAVE PRIMÁRIA) Campo que armazena um número único identicador das modalidadee existentes.<br>
* nome_modalidade: Campo que armazena a identificação por nome de cada modalidade.<br>
* limite_uso: Campo que armazena a quantidade de utilizações permitidas para cada modalidade.<br>

Tabela HISTORICO_SALDO: Tabela que armazena informações relevantes do saldo do usuário.<br>
* cod_saldo: (CHAVE PRIMARIA) Campo que armazena um número único identificador do saldo.<br>
* lib_prox_compra: Campo que armazena a data de liberação da proxima compra.<br>
* ultima_compra: Campo que armazena a data da ultima compra efetuada.<br>
* saldo: Campo que armazena o saldo atual do usuário.<br>

Tabela PGT_PASSAGEM: Tabela que armazena informações relacionadas a passagens pagas.<br>
* cod_pagamento: (CHAVE PRIMARIA) Campo que armazena um número único identificador do pagamento.<br>
* saldo_anterior: Campo que armazena o saldo antes do pagamento da passagem.<br>
* data: Campo que armazena a data do pagamento.<br>

Tabela LOCAL_COLETIVO: Tabela que armazena informações da localização dos ônibus.<br>
* cod_localizacao: (CHAVE PRIMARIA) Campo que armazena um número único identificador do ônibus.<br>
* coordenadas: Campo que armazena informações de coordenadas do ônibus.<br>

Tabela COLETIVO: Tabela que armazena informações do ônibus.<br>
* cod_coletivo: Campo que armazena um número único identificador dos ônibus.<br>
* linha: Campo que armazena o número da linha do ônibus.<br>
* partida: Campo que armazena a partida do ônibus.<br>
* destino: Campo que armazena o destino do ônibus.<br>

Tabela BANDEIRA: Tabela que armazena das bandeiras de cartão.<br>
* cod_bandeira: Campo identificador do registro de bandeira.<br>
* nome_bandeira: Nome da bandeira de cartão.<br>

Tabela CARTAO: Tabela que armazena os dados de um cartão do usuario.<br>
* cod_cartao: Campo identificador de um cartao.<br>
* cpf: CPF do dono do cartao.<br>
* vencimento: Data de vencimento do cartão.<br>
* cvv: Código de segurança do cartão.<br>
* nome: Nome do dono do cartão.<br>
* numero_cartao: Número do cartão do usuário.<br>


### 6	MODELO LÓGICO<br>
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Modelos/Modelo%20L%C3%B3gico/Modelo%20L%C3%B3gico.jpg "Modelo Conceitual")

### 7	MODELO FÍSICO<br>
<a href="https://github.com/Transpoint/TranspointProject/blob/master/Modelos/Modelo%20Fisico/Modelo%20F%C3%ADsico.sql"> Modelo físico </a><br>
       

### 8	INSERT APLICADO NAS TABELAS DO BANCO DE DADOS<br>
#### 8.1 DETALHAMENTO DAS INFORMAÇÕES
Geramos os dados de forma aleatória pelo seguintes links: <br>http://pt.fakenamegenerator.com/ <br>http://random-date-generator.com/ <br>http://listofrandomnames.com/index.cfm<br> http://www.geomidpoint.com/random/<br>
<br>Não utilizamos nenhum código previamente pronto e desenvolvemos nosso projeto a partir de situações
cotidianas.


#### 8.2 INCLUSÃO DO SCRIPT DE INSERÇÃO DOS DADOS
<a href="https://github.com/Transpoint/TranspointProject/blob/master/Scripts/Insert%20Data%20Transpoint.sql"> Script de insert de dados ao banco. </a><br>

#### 8.3 INCLUSÃO DO SCRIPT PARA CRIAÇÃO DE TABELA E INSERÇÃO DOS DADOS
<a href="https://github.com/Transpoint/TranspointProject/blob/master/Scripts/Create%20Database%20and%20Insert%20Data.sql"> Script de criação do banco, inserção dos dados e backup das tabelas. </a><br>

### 9	TABELAS E PRINCIPAIS CONSULTAS<br>
#### 9.1	CONSULTAS DAS TABELAS COM TODOS OS DADOS INSERIDOS (Todas) <br>

```sql
SELECT * FROM PESSOA;
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.1/9.1.1.png "Tabela Pessoa") <br>

```sql
SELECT * FROM COLETIVO;
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.1/9.1.2.png "Tabela Coletivo") <br>

```sql
SELECT * FROM MODALIDADE;
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.1/9.1.3.png "Tabela Modalidade") <br>

```sql
SELECT * FROM BANDEIRA;
```
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.1/9.1.4.png "Tabela Bandeira") <br>

```sql
SELECT * FROM CARTAO;
```
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.1/9.1.5.png "Tabela Cartão") <br>

```sql
SELECT * FROM LOCAL_BUS;
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.1/9.1.6.png "Tabela Local_Bus") <br>

```sql
SELECT * FROM HISTORICO_SALDO;
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.1/9.1.7.png "Tabela Historico_Saldo") <br>

```sql
SELECT * FROM PGT_PASSAGEM;
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.1/9.1.8.png "Tabela Pgt_Passagem") <br>


#### 9.2	CONSULTAS DAS TABELAS COM FILTROS WHERE (Mínimo 3)<br>

```sql
SELECT * FROM COLETIVO WHERE PARTIDA = 'T. JACARAIPE';
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%20-Prints/Consultas%209.2.1.jpg "9.2 Consulta 1") <br>

```sql
SELECT COD_PESSOA,NOME_PESSOA,DATA_NASC FROM PESSOA WHERE COD_MODALIDADE = 2;
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%20-Prints/Consultas%209.2.2.jpg "9.2 Consulta 2") <br>

```sql
SELECT NOME,CPF,VENCIMENTO,COD_BANDEIRA FROM CARTAO WHERE COD_BANDEIRA = 2 OR COD_BANDEIRA = 4;
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%20-Prints/Consultas%209.2.3.jpg "9.2 Consulta 3") <br>

```sql
SELECT COD_PESSOA,SALDO, ULTIMA_COMPRA FROM HISTORICO_SALDO WHERE LIB_PROX_COMPRA >'2017/07/07' AND LIB_PROX_COMPRA <= '2017/08/21';
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%20-Prints/Consultas%209.2.4.jpg "9.2 Consulta 4") <br>

#### 9.3	CONSULTAS QUE USAM OPERADORES LÓGICOS, ARITMÉTICOS E CAMPOS RENOMEADOS (Mínimo 2)<br>

```sql
select * from HISTORICO_SALDO where SALDO is not null;
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.3/IS%20NOT%20NULL.png "9.3 consulta 1") <br>

```sql
select * from PGT_PASSAGEM where SALDO_ANTERIOR<=80;
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.3/PGT_PASSAGEM%20where%20SALDO_ANTERIOR30%20and%20SALDO_ANTERIOR80.png "9.3 consulta 2") <br>

```sql
select NOME_PESSOA as Cliente, COD_MODALIDADE as "Atual modalidade", CPF from PESSOA;
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.3/select%20NOME_PESSOA%20as%20Cliente%20COD_MODALIDADE%20as%20Atual%20modalidade%20CPF%20from%20PESSOA.png "9.3 consulta 3") <br>

#### 9.4	CONSULTAS QUE USAM OPERADORES LIKE (Mínimo 3) <br>

```sql
select * from PESSOA where NOME_PESSOA like 'L%';
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.4/ALTERNATIVO1_select%20%20from%20PESSOA%20where%20NOME_PESSOA%20like%20'L%25'.png?raw=true "9.4 consulta 1") <br>

```sql
select * from PESSOA where NOME_PESSOA ilike '%La%';
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.4/select%20from%20PESSOA%20where%20NOME_PESSOA%20ilike%20'%25La%25'.png "9.4 consulta 2") <br>

```sql
select * from PESSOA where NOME_PESSOA like '_a%';
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.4/select%20from%20PESSOA%20where%20NOME_PESSOA%20like%20'_a%25'.png "9.4 consulta 3") <br>

#### 9.5	ATUALIZAÇÃO E EXCLUSÃO DE DADOS<br>
```sql
UPDATE PESSOA SET cod_modalidade = 1 WHERE data_nasc < '01-01-1999' AND cod_modalidade = 2;
SELECT * FROM PESSOA WHERE data_nasc < '01-01-1999';
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.5/9.5.1.PNG "9.5")

```sql
UPDATE MODALIDADE SET nome_modalidade = 'Estudante Gratuito' WHERE cod_modalidade = 3;
SELECT cod_modalidade CODIGO, nome_modalidade MODALIDADE FROM MODALIDADE;
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.5/9.5.2.PNG "9.5")

```sql
UPDATE PESSOA SET nome_pessoa = 'André Martins', data_nasc = '05-05-1997', cod_modalidade = 2 WHERE cod_pessoa = 1;
SELECT * FROM PESSOA WHERE cod_pessoa = 1;
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.5/9.5.3.PNG "9.5")

```sql
DELETE FROM HISTORICO_SALDO hs WHERE hs.saldo > 50;
SELECT * FROM HISTORICO_SALDO;
``` 
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.5/9.5.4.PNG "9.5")

#### 9.6	CONSULTAS COM JUNÇÃO E ORDENAÇÃO<br>

```sql
SELECT P.COD_PESSOA, P.NOME_PESSOA NOME, M.NOME_MODALIDADE MODALIDADE 
	FROM PESSOA P INNER JOIN MODALIDADE M 
	ON P.COD_MODALIDADE = M.COD_MODALIDADE
	ORDER BY NOME ASC;
```
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.6/9.6.1.png "9.6")

```sql
SELECT P.NOME_PESSOA NOME, C.LINHA LINHA, PP.SALDO_ANTERIOR SALDO, PP.DATA DATA_PGT
	FROM PESSOA P INNER JOIN PGT_PASSAGEM PP
	ON P.COD_PESSOA = PP.COD_PESSOA
	INNER JOIN LOCAL_BUS LB
	ON PP.COD_LOCALIZACAO = LB.COD_LOCALIZACAO
	INNER JOIN COLETIVO C
	ON C.COD_COLETIVO = LB.COD_COLETIVO;
```
![Alt text](https://github.com/Transpoint/TranspointProject/blob/master/Consultas%20-%20Prints/Consultas%209.6/9.6.2.png "9.6")

#### 9.7	CONSULTAS COM GROUP BY<br>
#### 9.8	CONSULTAS COM LEFT E RIGHT JOIN (Mínimo 4)<br>
#### 9.9	CONSULTAS COM SELF JOIN E VIEW (Todas Possíveis)<br>
#### 9.10	SUBCONSULTAS (Mínimo 3)<br>
        Entrega até este ponto em: (Data a ser definida)
### 10	ATUALIZAÇÃO DA DOCUMENTAÇÃO DOS SLIDES PARA APRESENTAÇAO FINAL (Mínimo 6 e Máximo 10)<br>
### 11	TUTORIAL COMPLETO DE PASSOS PARA RESTAURACAO DO BANCO E EXECUCAO DE PROCEDIMENTOS ENVOLVIDOS NO TRABALHO PARA OBTENÇÃO DOS RESULTADOS<br>
        a) Outros grupos deverão ser capazes de restaurar o banco 
        b) executar todas as consultas presentes no trabalho
        c) executar códigos que tenham sido construídos para o trabalho 
        d) realizar qualquer procedimento executado pelo grupo que desenvolveu o trabalho
        
### 12   DIFICULDADES ENCONTRADAS PELO GRUPO<br>
### 13   TRABALHO DE MINERAÇÃO DE DADOS
        a) captura das informaçõs
        b) integração com banco de dados em desenvolvimento
        c) atualização da documentação do trabalho incluindo a mineração de dados
        
### 13  FORMATACAO NO GIT: https://help.github.com/articles/basic-writing-and-formatting-syntax/

### 14 Backup completo do banco de dados postgres 
    a) deve ser realizado no formato "backup" 
        (Em Dump Options #1 Habilitar opções Don't Save Owner e Privilege)
    b) antes de postar o arquivo no git o mesmo deve ser testado/restaurado por outro grupo de alunos/dupla
    c) informar aqui o grupo de alunos/dupla que realizou o teste.
    
### OBSERVAÇÕES IMPORTANTES

#### Em tese todos os arquivos do trabalho devem ser compartilhados no git 
1. Caso existam arquivos com conteúdos sigilosos, comunicar o professor que definirá em conjunto com o grupo a melhor forma de armazenamento do arquivo.

#### Todos os grupos deverão fazer Fork deste repositório e dar permissões administrativas ao usuário deste GIT, para acompanhamento do trabalho.

#### Os usuários criados no GIT devem possuir o nome de identificação do aluno (não serão aceitos nomes como Eu123, meuprojeto, pro456, etc). Em caso de dúvida comunicar o professor.



