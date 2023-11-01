# Stored_Proced

![image](https://github.com/fzkdiniz/Stored_Proced/assets/61026576/81ae1c32-894b-4f85-9f92-487048c2d029)


-- Tabela Aluno
CREATE TABLE Aluno (
    ID INT PRIMARY KEY,
    Nome VARCHAR(50),
    Sobrenome VARCHAR(50),
    Email VARCHAR(60),
    CursoID INT,
    FOREIGN KEY (CursoID) REFERENCES Curso(ID)
);


-- Inserir dados de exemplo na tabela Aluno
INSERT INTO Aluno (Nome, Sobrenome, CPF, CursoID) VALUES
    ('Carlos', 'Silva', '12345678901', 1),
    ('Marta', 'Santos', '23456789012', 2),
    ('Luiz', 'Ferreira', '34567890123', 3),
    ('Lucia', 'Oliveira', '45678901234', 4),
    ('Rafael', 'Rodrigues', '56789012345', 5),
    ('Ana', 'Gomes', '67890123456', 6),
    ('Pedro', 'Ribeiro', '78901234567', 7),
    ('Clara', 'Costa', '89012345678', 8),
    ('Renato', 'Pereira', '90123456789', 9),
    ('Camila', 'Martins', '01234567890', 10);


-- Tabela Curso
CREATE TABLE Curso (
    idCurso INT PRIMARY KEY,
    NomeCurso VARCHAR(100),
    ProfessorID INT,
    FOREIGN KEY (ProfessorID) REFERENCES Professor(ID)
);

-- Inserir dados de exemplo na tabela Curso
INSERT INTO Curso (NomeCurso, ProfessorID) VALUES
    ('Matemática', 1),
    ('História', 2),
    ('Física', 3),
    ('Química', 4),
    ('Biologia', 5),
    ('Inglês', 6),
    ('Economia', 7),
    ('Geografia', 8),
    ('Literatura', 9),
    ('Programação', 10);

-- Tabela Professor
CREATE TABLE Professor (
    ID INT PRIMARY KEY AUTO_INCREMENT,
    Nome VARCHAR(50),
    Sobrenome VARCHAR(50)
);
 -- Inserir dados de exemplo na tabela Professor
INSERT INTO Professor (Nome, Sobrenome) VALUES
    ('João', 'Silva'),
    ('Maria', 'Santos'),
    ('Carlos', 'Ferreira'),
    ('Ana', 'Oliveira'),
    ('Pedro', 'Rodrigues'),
    ('Sandra', 'Gomes'),
    ('Miguel', 'Ribeiro'),
    ('Lucia', 'Costa'),
    ('Ricardo', 'Pereira'),
    ('Isabel', 'Martins');
-- Stored Procedure para inserir um novo Curso
DELIMITER //
CREATE PROCEDURE InserirCurso(IN NomeCurso VARCHAR(100), IN ProfessorID INT)
BEGIN
    INSERT INTO Curso (NomeCurso, ProfessorID) VALUES (NomeCurso, ProfessorID);
END;
//
DELIMITER ;

-- Stored Procedure para selecionar todos os Cursos
DELIMITER //
CREATE PROCEDURE SelecionarCursos()
BEGIN
    SELECT * FROM Curso;
END;
//
DELIMITER ;
