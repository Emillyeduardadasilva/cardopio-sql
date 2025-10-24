# ROSA

alunos: Lucas Yuri, Emilly Eduarda

-Tabela:pano
CREATE table plano (
    id_plano SERIAOL primary key <
    nome VARCHAR(100),
    descricao TEXT,
    preco Decimal(10,2)
);
--Tabela:estabelecimento
create table estabelecimento(
 id UUID primary key ,
 nome VARCHAR (100)
 endereco text,
 cnpj VARCHAR(20)
);
--tabela : usuario 
create table usuario (
 id_usuario UUID primary key,
 email VARCHAR (100) unique,
 senha VARCHAR(50)
 id_estabelecimento UUID,
FOREIGN key (id_estabelecimento) References estabelecimento(id)
);

--tabela : documento
create table documento (
 id_notificacao SERIAL PRIMARY key,
 tipo VARCHAR (50),
 caminho TEXT,
 status VARCHAR
 descricao TEXT,
 id_usurio UUID,
 id_estabelecimento UUId,
 primary key (id_usuario , id_estabelecimento),
 foreign key (id_usuario) references usuario (id_usuario),
 foreign key (id_estabelecimento) references estabelimento (id)
);

-- tabela: assinatura 
create table assinatura(
 id_plano INT,
 id_estabelicimento UUID,
 status VARCHAR(30),
 PRIMARY key (id_plano, id_estabelecimento),
 FOREIGN key (id_plano) references plano (id_plano),
 FOREING key  (id_estabelecimento) references estabelecimento (id)
 );