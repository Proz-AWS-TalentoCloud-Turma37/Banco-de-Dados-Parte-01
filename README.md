# Banco de dados
> Fundamentos de Banco de dados + Modelagem

## Definição:
> Banco de dados é um conjunto organizado de informações relacionadas entre si, que são armazenadas eletronicamente em computadores ou outros dispositivos de armazenamento. Os bancos de dados são projetados para facilitar a busca, a recuperação, o armazenamento e a organização de grandes quantidades de informações.

## Existem vários tipos de bancos de dados, incluindo:
- Banco de Dados Relacional: 
> é o tipo mais comum de banco de dados, onde as informações são organizadas em tabelas com colunas e linhas. As tabelas são relacionadas entre si através de chaves primárias e estrangeiras. Exemplos: MySQL, Oracle, SQL Server.
- Banco de Dados Não-Relacional: 
> também conhecido como NoSQL, esse tipo de banco de dados armazena informações em formatos diferentes de tabelas. Eles são frequentemente usados em aplicativos web e móveis para armazenar grandes quantidades de dados não-estruturados. Exemplos: MongoDB, Cassandra, Couchbase.
- Banco de Dados em Memória: 
> esses bancos de dados são otimizados para armazenar e recuperar dados em memória RAM, oferecendo alta velocidade e desempenho. Exemplos: SAP HANA, Oracle TimesTen.
---
## Modelagem:
> A modelagem de banco de dados é o processo de projetar a estrutura de um banco de dados. O objetivo é criar um modelo lógico que represente com precisão as informações que serão armazenadas no banco de dados. A modelagem de banco de dados é um processo importante porque ajuda a garantir que o banco de dados seja eficiente, fácil de usar e escalável. 

## Existem várias abordagens de modelagem, incluindo:
- Modelo Entidade-Relacionamento (ER): 
> é a abordagem mais comum para modelagem de banco de dados relacional. Ele usa diagramas para mostrar as entidades (objetos) que serão armazenados no banco de dados e seus relacionamentos.

- Modelo de Banco de Dados Orientado a Objetos: 
> é uma abordagem de modelagem de banco de dados que usa conceitos de programação orientada a objetos (POO). Neste modelo, os dados são armazenados em objetos, que podem ter métodos e atributos.

## Algumas aplicações de banco de dados incluem:
- Sistemas de Gerenciamento de Banco de Dados (SGBD): 
> são softwares que permitem criar, editar e gerenciar bancos de dados. Exemplos: MySQL, SQL Server, Oracle.
- Aplicativos de Negócios: 
> muitos aplicativos de negócios dependem de bancos de dados para armazenar informações sobre clientes, produtos e transações. Exemplos: Salesforce, SAP, Oracle E-Business Suite.
- Aplicativos Web e Móveis: 
> muitos aplicativos web e móveis precisam de bancos de dados para armazenar informações de usuários e outras informações relevantes. Exemplos: Facebook, Instagram, Uber.
---
## Conhecendo o SQL Server
> SQL Server é um sistema de gerenciamento de banco de dados relacional desenvolvido pela Microsoft. Ele é um dos sistemas de gerenciamento de banco de dados mais populares do mundo, usado por empresas de todos os tamanhos e setores para armazenar, organizar e recuperar dados.
---
## SQL
> A linguagem usada no SQL Server é a SQL (Structured Query Language), que é uma linguagem padrão para gerenciamento de bancos de dados relacionais. A SQL é usada para criar, modificar e manipular dados em bancos de dados relacionais. Embora a sintaxe possa variar ligeiramente entre os diferentes sistemas de gerenciamento de banco de dados (DBMS), a SQL é geralmente bastante padronizada e pode ser usada em diferentes plataformas.

## Para usar o SQL Server, você precisa seguir algumas etapas básicas:

1. Instalar o SQL Server: Primeiro, você precisa instalar o SQL Server no seu computador ou servidor. Você pode baixá-lo do site da Microsoft e seguir as instruções de instalação.
2. Conectar-se ao SQL Server: Depois de instalar o SQL Server, você pode se conectar a ele usando o SQL Server Management Studio, que é uma ferramenta gratuita oferecida pela Microsoft. Abra o SQL Server Management Studio e digite as informações de conexão, como o nome do servidor e as 
credenciais de login.
- [Vídeo de instalação](https://youtu.be/gUiFUzs-3bw "Vídeo de instalação")
---
## Criando e deletando um banco de dados
- ``CREATE DATABASE``: Usado para criar um banco de dados
> CREATE DATABASE nome_do_banco_de_dados;
````sql
CREATE DATABASE loja;
````
- ``USE``: Usado para selecionar um banco de dados
> USE nome_do_banco_de_dados;
````sql
USE loja;
````
- ``DROP DATABASE``: Usado para deletar um banco de dados
> DROP DATABASE minha_base_de_dados;
````sql
DROP DATABASE loja;
````
---
## Criando uma tabela
- ``CREATE TABLE``: Usado para criar uma nova tabela no banco de dados.
> CREATE TABLE tabela1 (coluna1 tipo1, coluna2 tipo2, coluna3 tipo3)
````sql
CREATE TABLE clientes (
  id INT PRIMARY KEY,
  nome VARCHAR(255),
  email VARCHAR(255)
);
````
- ``ALTER TABLE``: Usado para alterar a estrutura de uma tabela existente.
> ALTER TABLE tabela1 ADD coluna4 tipo4
````sql
/*Adicionando a coluna telefone*/
ALTER TABLE clientes ADD telefone VARCHAR(20);

/*Alterando a coluna email*/
ALTER TABLE acliente
ALTER COLUMN email NVARCHAR(100);

/*Deletando uma coluna da tabela*/
ALTER TABLE clientes DROP COLUMN telefone;

````
- ``DROP TABLE``: Usado para excluir uma tabela existente.
> DROP TABLE tabela1
````sql
DROP TABLE clientes;
````
## Tipos, NOT NULL e AUTO_INCREMENT
- Tipos de dados: cada coluna em uma tabela deve ser definida com um tipo de dados, que determina o tipo de valor que pode ser armazenado naquela coluna. Alguns exemplos de tipos de dados comuns são "VARCHAR" (para strings), "INTEGER" (para números inteiros) e "DECIMAL" (para números decimais).

- NOT NULL: ao criar uma tabela, você pode especificar se uma determinada coluna é obrigatória (ou seja, não pode ser deixada em branco) usando a cláusula "NOT NULL". Por exemplo, se você quiser que o campo "Nome" em uma tabela "Clientes" seja obrigatório, você pode definir a coluna assim: "Nome VARCHAR(50) NOT NULL".

- Auto-increment: muitas vezes é útil ter uma coluna em uma tabela que é automaticamente incrementada quando um novo registro é inserido. Para isso, você pode usar a cláusula "AUTO_INCREMENT" (ou "IDENTITY" no caso do SQL Server) ao definir a coluna. Por exemplo, se você quiser que a coluna "IdCliente" em uma tabela "Clientes" seja incrementada automaticamente, você pode defini-la assim: "IdCliente INTEGER IDENTITY(1,1) PRIMARY KEY". O "1,1" especifica que a contagem deve começar em 1 e aumentar de 1 em 1. A coluna também é definida como chave primária usando a cláusula "PRIMARY KEY".

Exemplo:
````sql
CREATE TABLE Clientes (
    IdCliente INTEGER IDENTITY(1,1) PRIMARY KEY,
    Nome VARCHAR(50) NOT NULL,
    Email VARCHAR(100),
    Telefone VARCHAR(20) NOT NULL
);
````

- "IdCliente" é uma coluna numérica que é definida como chave primária e é incrementada automaticamente pelo SQL Server usando a cláusula "IDENTITY(1,1)".
- "Nome" é uma coluna de texto (tipo VARCHAR) que é obrigatória e não pode ser deixada em branco.
- "Email" é uma coluna de texto (tipo VARCHAR) que pode ser deixada em branco (não é obrigatória).
- "Telefone" é uma coluna de texto (tipo VARCHAR) que é obrigatória e não pode ser deixada em branco.


---
## Conhecendo o CRUD
> O CRUD é um acrônimo que representa as quatro principais operações de um sistema de gerenciamento de banco de dados: Create (Criar), Read (Ler), Update (Atualizar) e Delete (Excluir). Essas operações básicas são executadas em uma tabela do banco de dados para manipular os dados. 

### READ (Ler) 
- ``SELECT``: Usado para selecionar dados de uma ou mais tabelas.
> SELECT * FROM tabela1

- Listando todos os clientes
````sql
SELECT * FROM clientes;
````

### CREATE (Criar)
- ``INSERT INTO``: Usado para inserir novos dados em uma tabela.
> INSERT INTO tabela1 (coluna1, coluna2) VALUES (valor1, valor2)
````sql
INSERT INTO clientes (id, nome, email) VALUES (1, 'João', 'joao@gmail.com');
````

### UPDATE (Atualizar)
- ``UPDATE``: Usado para atualizar dados existentes em uma tabela.
> UPDATE tabela1 SET coluna1 = valor1 WHERE coluna2 = valor2 
````sql
UPDATE clientes SET email = 'joao123@gmail.com' WHERE id = 1;
````

### DELETE (Excluir)
- ``DELETE``: Usado para excluir dados existentes de uma tabela.
> DELETE FROM tabela1 WHERE coluna1 = valor1
````sql
DELETE FROM clientes WHERE id = 1;
````

---
## Exercícios:
1. Crie um banco de dados chamado "loja".
2. Crie uma tabela chamada "produto" com as seguintes colunas: id (inteiro), nome (texto), quantidade (inteiro) e preço (decimal).
3. Adicione um produto com id igual a 1, nome "Camiseta", quantidade 10 e preço 29.99.
4. Adicione um segundo produto com id igual a 2, nome "Calça", quantidade 5 e preço 79.99.
5. Adicione um terceiro produto com id igual a 3, nome "Tênis", quantidade 2 e preço 149.99.
6. Delete o produto com id igual a 3.
7. Altere o preço do produto com id igual a 2 para 89.99.
