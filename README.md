﻿
<h1 align="center">
  
  ![Captura de tela_20-4-2025_145125_localhost](https://github.com/user-attachments/assets/5a2d0880-c9d5-45e5-9895-7a2a35e0bb8e)

  <br>
AspnetEasterEggs - Prova de Conceito
</h1>

<p align="center">
  <img alt="Repository size" src="https://img.shields.io/github/repo-size/WataNegreirosMonteiro/AspnetEasterEggs.svg">
  <a href="https://github.com/WataNegreirosMonteiro">
    <img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/WataNegreirosMonteiro/AspnetEasterEggs.svg">
  </a>
  <a href="https://github.com/WataNegreirosMonteiro/AspnetEasterEggs/issues">
    <img alt="Repository issues" src="https://img.shields.io/github/issues/WataNegreirosMonteiro/AspnetEasterEggs.svg">
  </a>
  <img alt="GitHub" src="https://img.shields.io/github/license/WataNegreirosMonteiro/AspnetEasterEggs.svg">
</p>

<h4 align="center">
  Prova de Conceito: Cadastro de Destinatários para Envio de Ovos de Páscoa com ASP.NET Core
</h4>

<p align="center">
  <a href="#sobre-a-prova-de-conceito">Sobre a Prova de Conceito</a> •
  <a href="#pré-requisitos">Pré-requisitos</a> •
  <a href="#como-rodar-o-projeto">Como Rodar o Projeto</a> •
  <a href="#tecnologias-utilizadas">Tecnologias Utilizadas</a> •
  <a href="#resultados-e-aprendizados">Resultados e Aprendizados</a> •
  <a href="#licença">Licença</a>
</p>

---

## Sobre a Prova de Conceito

Este projeto é uma **prova de conceito (PoC)** desenvolvida para explorar pela primeira vez o framework **ASP.NET Core**, utilizando a linguagem **C#** no ambiente **Visual Studio**. A temática escolhida foi o **cadastro de destinatários para envio de ovos de Páscoa**, simulando um sistema simples que poderia ser usado por uma empresa de chocolates para gerenciar entregas.

### Objetivo
O objetivo principal desta PoC foi testar a viabilidade de criar uma aplicação web com ASP.NET Core que:
- Permita o cadastro e gerenciamento de destinatários (clientes).
- Integre-se a um banco de dados relacional para armazenar informações.
- Seja desenvolvida de forma simples e funcional em um ambiente local.

### Contexto
- **Tecnologia Web**: Foi utilizado o ASP.NET Core na versão **NET 8.0.15**, uma escolha moderna para desenvolvimento web em C#.
- **Banco de Dados**: O banco de dados escolhido foi o **SQL Server Express 2022**, configurado para armazenar os dados dos destinatários.
- **Escopo**: A aplicação permite criar, visualizar e gerenciar informações básicas de clientes, como nome, e-mail, telefone e endereço, com um timestamp de criação.

Esta PoC foi um experimento inicial para entender o fluxo de desenvolvimento com ASP.NET Core, desde a configuração do ambiente até a integração com o banco de dados.

---

## Pré-requisitos

Para executar este projeto, você precisará dos seguintes softwares instalados:

- **Visual Studio**: Recomenda-se a versão mais recente (2022 ou superior) com a workload de desenvolvimento para ASP.NET e web instalada.
- **.NET SDK 8.0.15**: Necessário para rodar aplicações ASP.NET Core na versão utilizada. [Baixe aqui](https://dotnet.microsoft.com/download/dotnet/8.0).
- **SQL Server Express 2022**: Utilizado como banco de dados. [Baixe aqui](https://www.microsoft.com/en-us/sql-server/sql-server-downloads).
- **SQL Server Management Studio (SSMS)** (opcional): Para facilitar a configuração e visualização do banco de dados.

Além disso, certifique-se de que o Git está instalado para clonar o repositório, ou baixe o código diretamente como um arquivo ZIP.

---

## Como Rodar o Projeto

Siga os passos abaixo para configurar e executar a prova de conceito em sua máquina local.

### 1. Clone o Repositório
Clone o repositório para sua máquina local usando o comando:

```bash
git clone https://github.com/WataNegreirosMonteiro/AspnetEasterEggs.git
```

Ou faça o download do código como ZIP e descompacte.

### 2. Configure o Banco de Dados
1. Abra o SQL Server Management Studio (ou outra ferramenta de gerenciamento de SQL Server) e conecte-se à sua instância do SQL Server Express 2022.
2. Crie um novo banco de dados chamado `EasterEggsDB` (ou outro nome de sua preferência).
3. Execute o seguinte script SQL para criar a tabela `clients`:

```sql
CREATE TABLE clients (
    id INT NOT NULL PRIMARY KEY IDENTITY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(150) NOT NULL UNIQUE,
    phone VARCHAR(20) NULL,
    address VARCHAR(100) NULL,
    created_at DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP
);
```

4. (Opcional) Insira alguns dados iniciais para testes:

```sql
INSERT INTO clients (name, email, phone, address)
VALUES
('João Miguel Costa', 'joao.costa@example.com', '(11) 99999-9999', 'Rua Oscar Freire, 1000, São Paulo - SP'),
('Isadora Lima', 'isadora.lima@example.com', '(21) 88888-8888', 'Rua Visconde de Pirajá, 2000, Rio de Janeiro - RJ'),
('Gustavo Fernandes', 'gustavo.fernandes@example.com', '(31) 77777-7777', 'Avenida Afonso Pena, 3000, Belo Horizonte - MG');
```

### 3. Configure a String de Conexão

### Aviso sobre Boas Práticas
Este projeto foi desenvolvido de forma rápida e simplificada como parte de uma prova de conceito (PoC), e, por isso, não segue todas as boas práticas recomendadas para projetos em produção. Um dos principais pontos de melhoria identificados é o uso de **strings de conexão hardcoded** diretamente no código-fonte, o que pode trazer riscos de segurança e dificultar a manutenção.

Para evitar problemas e seguir boas práticas, faça:
- Armazenar configurações sensíveis, como strings de conexão, em arquivos de configuração (como `appsettings.json`) ou em variáveis de ambiente.
- Utilizar ferramentas de gerenciamento de segredos para proteger dados sensíveis em produção.
- Documentar claramente os passos para configuração, como feito abaixo.

### Instruções para Configurar a Conexão
Para que a aplicação se conecte corretamente ao seu banco de dados, é necessário substituir a string de conexão padrão presente no código pela string correspondente à sua instância do SQL Server. A string de conexão atualmente utilizada no projeto é:

```
Data Source=.\\SQLEXPRESS;Initial Catalog=master;Integrated Security=True;
```

### 5. Teste a Funcionalidade
- Acesse a página inicial da aplicação.
- Cadastre um novo destinatário preenchendo os campos necessários (nome, e-mail, telefone e endereço).
- Verifique se os dados são salvos corretamente no banco de dados, consultando a tabela `clients` pelo SSMS.

---

## Tecnologias Utilizadas

Este projeto foi desenvolvido com as seguintes tecnologias:

- **ASP.NET Core (NET 8.0.15)**: Framework principal para desenvolvimento web.
- **C#**: Linguagem de programação utilizada.
- **Visual Studio**: IDE usada para desenvolvimento e depuração.
- **SQL Server Express 2022**: Banco de dados relacional para armazenamento dos dados.

---

## Resultados e Aprendizados

### O que foi Validado
Esta prova de conceito teve como objetivo principal testar a viabilidade de construir uma aplicação web com ASP.NET Core integrada ao SQL Server Express. Os seguintes pontos foram validados:
- Configuração de um projeto ASP.NET Core no Visual Studio.
- Integração com o SQL Server Express para armazenamento de dados.
- Criação de uma interface web simples para cadastro e consulta de destinatários.

### Resultados
- A aplicação foi capaz de rodar localmente e realizar o cadastro de destinatários com sucesso.
- Os dados foram salvos corretamente no SQL Server Express, respeitando as restrições da tabela (como unicidade de e-mails).
- A interface web permitiu interação básica, como adicionar e visualizar registros.

### Aprendizados
- Configurar a string de conexão corretamente é essencial para a integração com o SQL Server.
- O uso do Visual Studio facilita o desenvolvimento e a depuração de projetos ASP.NET Core.
- A criação manual de tabelas no SQL Server é uma alternativa viável quando as migrações automáticas não são usadas.
- A escolha de uma temática simples (cadastro de destinatários para ovos de Páscoa) ajudou a focar no aprendizado das tecnologias, sem complicações desnecessárias.

### Limitações
- A PoC não inclui autenticação ou validações avançadas, como verificação de formato de e-mail ou telefone.
- A interface é básica e pode ser melhorada para uso em produção.
- O projeto foi testado apenas em ambiente local, sem considerar deploy ou escalabilidade.

---

Feito com ♥ por Wata Negreiros Monteiro :wave: [Entre em contato!](https://www.linkedin.com/in/wata-negreiros-monteiro-2a94ab1a7/)

| [<img src="https://avatars.githubusercontent.com/u/90472705?v=4" width=115><br><sub>Wata Negreiros Monteiro</sub>](https://github.com/WataNegreirosMonteiro) |

---
