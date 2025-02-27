Sistema de Controle de Ordens de Serviço em Oficina Mecânica
Este projeto foi desenvolvido para organizar as atividades de uma oficina mecânica, facilitando o gerenciamento desde o cadastro dos clientes até o acompanhamento da execução dos serviços. Nele, você pode cadastrar clientes (PF e PJ), registrar veículos, emitir ordens de serviço, associar serviços e peças, controlar pagamentos e acompanhar entregas.

Funcionalidades
Cadastro de Clientes e Veículos
Permite registrar clientes, diferenciando pessoas físicas e jurídicas, e associar os respectivos veículos.

Emissão e Gerenciamento de Ordens de Serviço
Criação de OS com informações como data de abertura, status, valor total e equipe responsável.

Registro de Serviços e Peças
Adiciona múltiplos serviços e peças a uma OS, possibilitando o controle de custos e quantidade.

Gestão de Equipes e Mecânicos
Organização das equipes que executam os serviços, com associação de mecânicos a cada equipe.

Controle de Pagamentos e Entregas
Registro de diferentes formas de pagamento e acompanhamento do status e código de rastreio de entregas.

Estrutura do Banco de Dados
O banco de dados foi modelado em MySQL e abrange as seguintes tabelas:

Clientes: Informações sobre pessoas físicas ou jurídicas.
Veículos: Dados dos veículos dos clientes.
Ordens de Serviço (OS): Registro das ordens com detalhes como data, status e equipe designada.
Serviços e Peças: Itens associados a cada OS, permitindo a inclusão de quantidades e valores.
Equipes e Mecânicos: Relação entre equipes e seus respectivos mecânicos.
Pagamentos: Registro de múltiplas formas de pagamento para cada OS.
Entrega: Controle do status de entrega e rastreamento.
Como Utilizar
Clone o repositório:

bash
Copiar
git clone https://github.com/seu-usuario/seu-repositorio.git
Importe o script SQL:
Utilize o MySQL Workbench ou a linha de comando para executar o script de criação das tabelas. Exemplo via linha de comando:

bash
Copiar
mysql -u seu_usuario -p < script_criacao_tabelas.sql
Configure sua aplicação:
Ajuste a conexão com o banco de dados na sua aplicação e comece a utilizar as funcionalidades do sistema.

Tecnologias Utilizadas
MySQL – Gerenciamento do banco de dados.
Python (opcional) – Automação do script de criação e possíveis integrações com a aplicação.
Contribuições
Sua colaboração é muito bem-vinda! Se tiver sugestões, encontrar problemas ou desejar melhorar alguma funcionalidade, abra uma issue ou envie um pull request.

Observações
Este projeto foi criado para auxiliar na organização e controle das atividades de uma oficina mecânica. Ele pode ser ajustado conforme as necessidades específicas do seu negócio.

Agradeço por conferir este projeto e espero que ele seja útil para você!
