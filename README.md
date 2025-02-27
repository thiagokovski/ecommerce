# Sistema de Controle de Ordens de Serviço em Oficina Mecânica

Este projeto tem como objetivo gerenciar o fluxo de trabalho de uma oficina mecânica, desde o **cadastro de clientes** e **veículos** até o **controle de serviços**, **peças**, **pagamentos** e **entregas**.

## Principais Funcionalidades

- **Cadastro de Clientes (PF ou PJ)**  
  Permite gerenciar informações de pessoas físicas e jurídicas, garantindo que apenas um tipo de documento seja preenchido (CPF ou CNPJ).

- **Gestão de Veículos**  
  Cada veículo é vinculado a um cliente, com dados de marca, modelo, ano e placa.

- **Ordens de Serviço (OS)**  
  - Emissão de OS com data de abertura, valor total, status (aberta, em andamento, concluída) e data de conclusão.  
  - Associação a uma equipe de mecânicos responsáveis pela execução.

- **Serviços e Peças**  
  - Serviços e peças são adicionados a cada OS por meio de tabelas intermediárias (itens), permitindo o cálculo de quantidade, valor unitário e valor total.  
  - Facilita o controle de estoque de peças e mão de obra dos serviços.

- **Equipes e Mecânicos**  
  - Mapeamento de equipes com diversos mecânicos (relação N:N).  
  - Cada OS é atribuída a uma única equipe, que cuida da execução.

- **Pagamentos**  
  - Várias formas de pagamento podem ser registradas para uma mesma OS (ex.: parte em cartão, parte em PIX).

- **Entrega**  
  - Controle de status e código de rastreio para acompanhar a entrega do veículo ou peças, se necessário.

## Modelagem do Banco de Dados

A modelagem inclui tabelas para **Clientes**, **Veículos**, **Equipes**, **Mecânicos**, **Ordens de Serviço**, **Serviços**, **Peças**, **Pagamentos** e **Entrega**, além das tabelas intermediárias para relacionamentos muitos-para-muitos (N:N). O diagrama ER e o script de criação das tabelas (MySQL) estão disponíveis no repositório.

## Como Executar

1. **Clone** este repositório localmente:
   ```bash
   git clone https://github.com/seu-usuario/seu-repositorio.git
   ```
2. **Abra** o arquivo `script_criacao_tabelas.sql` (ou equivalente) em uma ferramenta como MySQL Workbench ou no terminal MySQL.
3. **Execute** o script para criar o banco de dados e as tabelas.
4. **Configure** sua aplicação ou scripts de teste para se conectar ao banco de dados criado e iniciar as operações (inserir clientes, veículos, etc.).

## Tecnologias

- **MySQL** para gerenciamento do banco de dados.
- Pode ser integrado com **Python**, **Java**, **PHP** ou outra linguagem que suporte MySQL Connector para manipular os dados.

## Contribuições

Sinta-se à vontade para abrir *issues* com sugestões de melhorias ou correções. Pull requests são bem-vindos para adicionar novas funcionalidades ou corrigir eventuais problemas.

---

**Observação**: Este projeto é apenas uma base de exemplo. Ajustes podem ser necessários conforme regras de negócio específicas da sua oficina ou conforme evolução dos requisitos.
