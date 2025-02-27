import mysql.connector
from mysql.connector import errorcode

def main():
    # Configurações de conexão - ajuste conforme necessário
    config = {
        'user': 'root',
        'password': 'sua_senha',  # substitua pela sua senha
        'host': 'localhost'
    }
    
    try:
        # Conecta ao MySQL
        cnx = mysql.connector.connect(**config)
        cursor = cnx.cursor()
        
        # Cria o banco de dados se não existir e usa-o
        cursor.execute("CREATE DATABASE IF NOT EXISTS OficinaMecanica")
        cursor.execute("USE OficinaMecanica")
        
        # Lista com os comandos SQL para criar as tabelas
        sql_commands = [
            # CLIENTE
            """
            CREATE TABLE CLIENTE (
                idCliente INT AUTO_INCREMENT PRIMARY KEY,
                tipoPessoa ENUM('PF','PJ') NOT NULL,
                nomeRazaoSocial VARCHAR(100) NOT NULL,
                cpf VARCHAR(14),
                cnpj VARCHAR(18),
                endereco VARCHAR(200),
                telefone VARCHAR(20)
            ) ENGINE=InnoDB;
            """,
            # EQUIPE
            """
            CREATE TABLE EQUIPE (
                idEquipe INT AUTO_INCREMENT PRIMARY KEY,
                nome VARCHAR(50)
            ) ENGINE=InnoDB;
            """,
            # MECANICO
            """
            CREATE TABLE MECANICO (
                idMecanico INT AUTO_INCREMENT PRIMARY KEY,
                nome VARCHAR(100) NOT NULL,
                endereco VARCHAR(200),
                especialidade VARCHAR(100)
            ) ENGINE=InnoDB;
            """,
            # SERVICO
            """
            CREATE TABLE SERVICO (
                idServico INT AUTO_INCREMENT PRIMARY KEY,
                descricao VARCHAR(100) NOT NULL,
                valorMaoDeObra DECIMAL(10,2) NOT NULL
            ) ENGINE=InnoDB;
            """,
            # PECA
            """
            CREATE TABLE PECA (
                idPeca INT AUTO_INCREMENT PRIMARY KEY,
                descricao VARCHAR(100) NOT NULL,
                valorUnitario DECIMAL(10,2) NOT NULL
            ) ENGINE=InnoDB;
            """,
            # VEICULO
            """
            CREATE TABLE VEICULO (
                idVeiculo INT AUTO_INCREMENT PRIMARY KEY,
                idCliente INT NOT NULL,
                marca VARCHAR(50),
                modelo VARCHAR(50),
                ano INT,
                placa VARCHAR(10),
                CONSTRAINT fk_veiculo_cliente
                    FOREIGN KEY (idCliente)
                    REFERENCES CLIENTE (idCliente)
                    ON UPDATE CASCADE
                    ON DELETE RESTRICT
            ) ENGINE=InnoDB;
            """,
            # ORDEM_SERVICO
            """
            CREATE TABLE ORDEM_SERVICO (
                idOS INT AUTO_INCREMENT PRIMARY KEY,
                numeroOS VARCHAR(20) NOT NULL,
                dataEmissao DATE NOT NULL,
                valorTotal DECIMAL(10,2) DEFAULT 0.00,
                status VARCHAR(50) DEFAULT 'Aberta',
                dataConclusao DATE,
                idVeiculo INT NOT NULL,
                idEquipe INT NOT NULL,
                CONSTRAINT fk_os_veiculo
                    FOREIGN KEY (idVeiculo)
                    REFERENCES VEICULO (idVeiculo)
                    ON UPDATE CASCADE
                    ON DELETE RESTRICT,
                CONSTRAINT fk_os_equipe
                    FOREIGN KEY (idEquipe)
                    REFERENCES EQUIPE (idEquipe)
                    ON UPDATE CASCADE
                    ON DELETE RESTRICT
            ) ENGINE=InnoDB;
            """,
            # EQUIPE_MECANICO (associação N:N)
            """
            CREATE TABLE EQUIPE_MECANICO (
                idEquipe INT NOT NULL,
                idMecanico INT NOT NULL,
                PRIMARY KEY (idEquipe, idMecanico),
                CONSTRAINT fk_eq_mec_equipe
                    FOREIGN KEY (idEquipe)
                    REFERENCES EQUIPE (idEquipe)
                    ON UPDATE CASCADE
                    ON DELETE RESTRICT,
                CONSTRAINT fk_eq_mec_mecanico
                    FOREIGN KEY (idMecanico)
                    REFERENCES MECANICO (idMecanico)
                    ON UPDATE CASCADE
                    ON DELETE RESTRICT
            ) ENGINE=InnoDB;
            """,
            # ITEM_SERVICO_OS (associação N:N entre OS e SERVICO)
            """
            CREATE TABLE ITEM_SERVICO_OS (
                idItemServico INT AUTO_INCREMENT PRIMARY KEY,
                idOS INT NOT NULL,
                idServico INT NOT NULL,
                quantidade INT DEFAULT 1,
                valorUnitario DECIMAL(10,2),
                valorTotal DECIMAL(10,2),
                CONSTRAINT fk_itemservico_os
                    FOREIGN KEY (idOS)
                    REFERENCES ORDEM_SERVICO (idOS)
                    ON UPDATE CASCADE
                    ON DELETE RESTRICT,
                CONSTRAINT fk_itemservico_servico
                    FOREIGN KEY (idServico)
                    REFERENCES SERVICO (idServico)
                    ON UPDATE CASCADE
                    ON DELETE RESTRICT
            ) ENGINE=InnoDB;
            """,
            # ITEM_PECA_OS (associação N:N entre OS e PECA)
            """
            CREATE TABLE ITEM_PECA_OS (
                idItemPeca INT AUTO_INCREMENT PRIMARY KEY,
                idOS INT NOT NULL,
                idPeca INT NOT NULL,
                quantidade INT DEFAULT 1,
                valorUnitario DECIMAL(10,2),
                valorTotal DECIMAL(10,2),
                CONSTRAINT fk_itempeca_os
                    FOREIGN KEY (idOS)
                    REFERENCES ORDEM_SERVICO (idOS)
                    ON UPDATE CASCADE
                    ON DELETE RESTRICT,
                CONSTRAINT fk_itempeca_peca
                    FOREIGN KEY (idPeca)
                    REFERENCES PECA (idPeca)
                    ON UPDATE CASCADE
                    ON DELETE RESTRICT
            ) ENGINE=InnoDB;
            """,
            # PAGAMENTO
            """
            CREATE TABLE PAGAMENTO (
                idPagamento INT AUTO_INCREMENT PRIMARY KEY,
                idOS INT NOT NULL,
                formaPagamento VARCHAR(50) NOT NULL,
                valorPago DECIMAL(10,2) NOT NULL,
                CONSTRAINT fk_pagamento_os
                    FOREIGN KEY (idOS)
                    REFERENCES ORDEM_SERVICO (idOS)
                    ON UPDATE CASCADE
                    ON DELETE RESTRICT
            ) ENGINE=InnoDB;
            """,
            # ENTREGA
            """
            CREATE TABLE ENTREGA (
                idEntrega INT AUTO_INCREMENT PRIMARY KEY,
                idOS INT NOT NULL,
                statusEntrega VARCHAR(50) DEFAULT 'Em trânsito',
                codigoRastreio VARCHAR(50),
                CONSTRAINT fk_entrega_os
                    FOREIGN KEY (idOS)
                    REFERENCES ORDEM_SERVICO (idOS)
                    ON UPDATE CASCADE
                    ON DELETE RESTRICT
            ) ENGINE=InnoDB;
            """
        ]
        
        # Executa cada comando SQL da lista
        for command in sql_commands:
            cursor.execute(command)
        
        # Confirma as alterações no banco
        cnx.commit()
        print("Banco de dados e tabelas criados com sucesso.")
    
    except mysql.connector.Error as err:
        if err.errno == errorcode.ER_ACCESS_DENIED_ERROR:
            print("Erro: Verifique suas credenciais.")
        elif err.errno == errorcode.ER_BAD_DB_ERROR:
            print("Erro: Banco de dados não existe.")
        else:
            print(err)
    finally:
        cursor.close()
        cnx.close()

if __name__ == "__main__":
    main()
