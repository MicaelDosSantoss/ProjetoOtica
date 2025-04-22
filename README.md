
# CRIAÇÃO DO BANCO DE DADOS

## PROJETO ÓTICAS FABY

Para a criação do banco foi utilizado a linguagem de programação MySQL, usamos também para colocar em ambiente de teste para fazer as alterações e utlizar ele como teste em nossa API.

### 📜 MODELO UTILIZADO

![MODELO USADO ](./Img/imgUmlIphone.png)

## 💻 CODIGO USADO

    CREATE TABLE Marca (
        ID_Marca VARCHAR(36) NOT NULL,
        Nome VARCHAR(100),
        PRIMARY KEY (ID_Marca)
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

    CREATE TABLE Material (
        ID_Material VARCHAR(36) NOT NULL,
        Tipo VARCHAR(100),
        PRIMARY KEY (ID_Material)
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

    CREATE TABLE Forma (
        ID_Forma VARCHAR(36) NOT NULL,
        Tipo VARCHAR(100),
        PRIMARY KEY (ID_Forma)
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

    CREATE TABLE Oculos (
        ID_Oculos VARCHAR(36) NOT NULL,
        Nome VARCHAR(100),
        ID_Material VARCHAR(36),
        Cor VARCHAR(50),
        Tamanho VARCHAR(20),
        ID_Marca VARCHAR(36),
        Genero VARCHAR(50),
        ID_Forma VARCHAR(36),
        Valor DECIMAL(10,2),
        Data_Recebimento DATE,
        PRIMARY KEY (ID_Oculos),
        FOREIGN KEY (ID_Material) REFERENCES Material(ID_Material),
        FOREIGN KEY (ID_Marca) REFERENCES Marca(ID_Marca),
        FOREIGN KEY (ID_Forma) REFERENCES Forma(ID_Forma)
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

    CREATE TABLE Ala (
        Ala_ID VARCHAR(36) NOT NULL,
        Prateleira VARCHAR(50),
        Secao VARCHAR(50),
        PRIMARY KEY (Ala_ID)
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

    CREATE TABLE Oculos_Ala (
        Oculos_FK VARCHAR(36) NOT NULL,
        Ala_FK VARCHAR(36) NOT NULL,
        PRIMARY KEY (Oculos_FK, Ala_FK),
        FOREIGN KEY (Oculos_FK) REFERENCES Oculos(ID_Oculos),
        FOREIGN KEY (Ala_FK) REFERENCES Ala(Ala_ID)
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

    CREATE TABLE Vendas (
        Oculos_Ala_ID VARCHAR(36) NOT NULL,
        Possivel_desconto DECIMAL(5,2),
        Colaborador VARCHAR(100),
        PRIMARY KEY (Oculos_Ala_ID),
        FOREIGN KEY (Oculos_Ala_ID) REFERENCES Oculos_Ala(Oculos_FK)
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

---

## O QUE FOI UTILIZADO 🤔