-- Criar Banco de Dados
CREATE DATABASE db_gp_de_brasil;
USE db_gp_de_brasil;

-- Criação das Tabelas
CREATE TABLE Pais(
    nome_pais VARCHAR(50) NOT NULL PRIMARY KEY
);

CREATE TABLE Corrida(
    brasil_gp VARCHAR(100) NOT NULL PRIMARY KEY,
    nome_pais_fk VARCHAR(50),
    qntd_voltas INTEGER NOT NULL,
    tmhn_pista VARCHAR(15),
    FOREIGN KEY (nome_pais_fk) REFERENCES Pais(nome_pais)
);

CREATE TABLE Equipe(
    nome_equi VARCHAR(70) NOT NULL PRIMARY KEY,
    nome_pais_fk VARCHAR(50),
    FOREIGN KEY (nome_pais_fk) REFERENCES Pais(nome_pais)
);

CREATE TABLE Piloto(
    num_pilo INTEGER NOT NULL PRIMARY KEY,
    nome_pilo VARCHAR(100) NOT NULL,
    nome_equi_fk VARCHAR(50),
    nome_pais_fk VARCHAR(50),
    FOREIGN KEY (nome_equi_fk) REFERENCES Equipe(nome_equi),
    FOREIGN KEY (nome_pais_fk) REFERENCES Pais(nome_pais)
);

CREATE TABLE Participantes(
    brasil_gp_fk VARCHAR(100),
    num_pilo_fk INTEGER,
    pose_larg INTEGER NOT NULL,
    FOREIGN KEY (brasil_gp_fk) REFERENCES Corrida(brasil_gp),
    FOREIGN KEY (num_pilo_fk) REFERENCES Piloto(num_pilo),
    PRIMARY KEY (brasil_gp_fk, num_pilo_fk)
);

-- Inserção de Dados
INSERT INTO Pais (nome_pais) VALUES
('Brasil'),
('Itália'),
('França'),
('Bolívia'),
('Argentina'),
('Estados Unidos'),
('México'),
('Chile'),
('Irlanda'),
('Nova Zelândia');

INSERT INTO Corrida (brasil_gp, nome_pais_fk, qntd_voltas, tmhn_pista) VALUES
('Corrida de Goiânia', 'Brasil', 3, '9km'),
('Corrida de Belém', 'México', 3, '9km'),
('Corrida de Vitória', 'Irlanda', 3, '9km'),
('Corrida de Rio de Janeiro', 'Estados Unidos', 3, '9km'),
('Corrida de São Paulo', 'Argentina', 5, '5km'),
('Corrida de Rio Branco', 'Bolívia', 5, '5km'),
('Corrida de Londrina', 'Chile', 5, '5km'),
('Corrida de Salvador', 'França', 9, '3km'),
('Corrida de Fortaleza', 'Itália', 9, '3km'),
('Corrida de Brasília', 'Nova Zelândia', 9, '3km');

INSERT INTO Equipe (nome_equi, nome_pais_fk) VALUES
('Fittipaldi', 'Brasil'),
('Alpine', 'França'),
('Minardi', 'Itália'),
('Mercedes', 'Nova Zelândia'),
('McLaren', 'México'),
('Williams', 'Irlanda'),
('Haas', 'Chile'),
('Audi', 'Argentina'),
('Cadillac', 'Bolívia'),
('Aston Martin', 'Estados Unidos');

INSERT INTO Piloto (num_pilo, nome_pilo, nome_equi_fk, nome_pais_fk) VALUES
(1, 'Ayrton Senna', 'Fittipaldi', 'Brasil'),
(11, 'Nelson Piquet', 'Fittipaldi', 'Brasil'),
(38, 'Emerson Fittipaldi', 'Fittipaldi', 'Brasil'),
(101, 'Rubens Barrichello', 'Fittipaldi', 'Brasil'),
(12, 'Felipe Massa', 'Fittipaldi', 'Brasil'),
(5, 'Alberto Ascari', 'Minardi', 'Itália'),
(14, 'Giuseppe Farina', 'Minardi', 'Itália'),
(19, 'Andrea Kimi Antonelli', 'Minardi', 'Itália'),
(10, 'Pierre Gasly', 'Alpine', 'França'),
(31, 'Esteban Ocon', 'Alpine', 'França'),
(17, 'Carlo Abate', 'Aston Martin', 'México'),
(2, 'George Abecassis', 'Cadillac', 'Chile'),
(3, 'Kenny Acheson', 'Audi', 'Argentina'),
(45, 'Andrea de Adamich', 'Haas', 'Irlanda'),
(4, 'Philippe Adams', 'Williams', 'Nova Zelândia'),
(6, 'Walt Ader', 'McLaren', 'Bolívia'),
(7, 'Kurt Adolff', 'Mercedes', 'Estados Unidos');

INSERT INTO Participantes (brasil_gp_fk, num_pilo_fk, pose_larg) VALUES
('Corrida de Goiânia', 1, 1),
('Corrida de Londrina', 11, 2),
('Corrida de Brasília', 38, 3),
('Corrida de São Paulo', 101, 4),
('Corrida de Rio de Janeiro', 12, 5),
('Corrida de Salvador', 5, 6),
('Corrida de Rio Branco', 14, 7),
('Corrida de Fortaleza', 19, 8),
('Corrida de Vitória', 10, 9),
('Corrida de Belém', 31, 10);

-- Consultas Iniciais
SELECT nome_pais
FROM Pais
WHERE nome_pais LIKE 'B%l'; 

SELECT nome_pilo, nome_pais_fk
FROM Piloto;

SELECT nome_pilo
FROM Piloto;

SELECT brasil_gp AS Gp, qntd_voltas AS voltas
FROM Corrida;

SELECT *
FROM Piloto;

-- Alteração na tabela e atualização dos dados
ALTER TABLE Piloto
ADD salario DECIMAL(10,2);

UPDATE Piloto SET salario = 100000.00 WHERE num_pilo = 1;
UPDATE Piloto SET salario = 90000.00 WHERE num_pilo = 11;
UPDATE Piloto SET salario = 80000.00 WHERE num_pilo = 38;
UPDATE Piloto SET salario = 70000.00 WHERE num_pilo = 101;
UPDATE Piloto SET salario = 60000.00 WHERE num_pilo = 12;
UPDATE Piloto SET salario = 50000.00 WHERE num_pilo = 5;
UPDATE Piloto SET salario = 40000.00 WHERE num_pilo = 14;
UPDATE Piloto SET salario = 30000.00 WHERE num_pilo = 19;
UPDATE Piloto SET salario = 20000.00 WHERE num_pilo = 10;
UPDATE Piloto SET salario = 31000.00 WHERE num_pilo = 31;
UPDATE Piloto SET salario = 30000.00 WHERE num_pilo = 17;
UPDATE Piloto SET salario = 40000.00 WHERE num_pilo = 2;
UPDATE Piloto SET salario = 50000.00 WHERE num_pilo = 3;
UPDATE Piloto SET salario = 60000.00 WHERE num_pilo = 45;
UPDATE Piloto SET salario = 70000.00 WHERE num_pilo = 4;
UPDATE Piloto SET salario = 80000.00 WHERE num_pilo = 6;
UPDATE Piloto SET salario = 90000.00 WHERE num_pilo = 7;

-- Consultas Finais
SELECT nome_pilo, salario
FROM Piloto
WHERE salario BETWEEN 70000 AND 100000;

SELECT ROUND(AVG(salario)) AS media_salarial
FROM Piloto
WHERE nome_pais_fk = 'Brasil';

SELECT ROUND(AVG(salario)) AS media_salarial
FROM Piloto
WHERE nome_pais_fk = 'Itália';

SELECT ROUND(AVG(salario), 2) AS media_salarial
FROM Piloto
WHERE nome_pais_fk = 'França';

SELECT DISTINCT salario
FROM Piloto;