# ROSA

alunos: Lucas Yuri, Emilly Eduarda

Codigo SQL do Menu Acessivel 

-- Tabela: plano
CREATE TABLE plano (
    id_plano SERIAL PRIMARY KEY,
    nome VARCHAR(100),
    descricao TEXT,
    preco DECIMAL(10,2)
);

-- Tabela: estabelecimento
CREATE TABLE estabelecimento (
    id UUID PRIMARY KEY,
    nome VARCHAR(100),
    endereco TEXT,
    cnpj VARCHAR(20)
);

-- Tabela: usuario
CREATE TABLE usuario (
    id_usuario UUID PRIMARY KEY,
    email VARCHAR(100) UNIQUE,
    senha VARCHAR(50),
    id_estabelecimento UUID,
    FOREIGN KEY (id_estabelecimento) REFERENCES estabelecimento(id)
);

-- Tabela: documento
CREATE TABLE documento (
    id_notificacao SERIAL PRIMARY KEY,
    tipo VARCHAR(50),
    caminho TEXT,
    status VARCHAR(50),
    descricao TEXT,
    id_usuario UUID,
    id_estabelecimento UUID,
    FOREIGN KEY (id_usuario) REFERENCES usuario(id_usuario),
    FOREIGN KEY (id_estabelecimento) REFERENCES estabelecimento(id)
);

-- Tabela: assinatura
CREATE TABLE assinatura (
    id_plano INT,
    id_estabelecimento UUID,
    status VARCHAR(30),
    PRIMARY KEY (id_plano, id_estabelecimento),
    FOREIGN KEY (id_plano) REFERENCES plano(id_plano),
    FOREIGN KEY (id_estabelecimento) REFERENCES estabelecimento(id)
);
