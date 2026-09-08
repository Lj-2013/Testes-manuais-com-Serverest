# 🧪 Testes Manuais & Qualidade de Software — ServeRest Frontend

[![QA Status](https://img.shields.io/badge/Status-Conclu%C3%ADdo-brightgreen)](https://front.serverest.dev/login)
[![Suíte de Testes](https://img.shields.io/badge/Testes%20Executados-16-blue)](#-resumo-da-execu%C3%A7%C3%A3o)
[![Taxa de Sucesso](https://img.shields.io/badge/Pass%20Rate-93.75%25-green)](#-resumo-da-execu%C3%A7%C3%A3o)
[![Bug Encontrado](https://img.shields.io/badge/Bugs-1%20Aberto-red)](#-relat%C3%B3rio-de-bugs-defects)

## 📌 Sobre o Projeto
Este repositório armazena o **Plano de Testes** e os **Casos de Teste Manuais** elaborados para a aplicação e-commerce [ServeRest Front-end](https://front.serverest.dev/login). 

O objetivo principal desta validação foi garantir a estabilidade, usabilidade, integridade de dados e aderência às regras de negócio nas rotas de **Autenticação (Login)** e **Gestão/Cadastro de Usuários**, identificando falhas de experiência do usuário (UX) e comportamentos inesperados no sistema.

---

## 👨‍💻 Responsável pelo Projeto
* **QA Analyst:** Luciano Silva
* **Papel:** Elaboração da estratégia, escrita dos casos de teste, execução funcional e relatório de bugs.

---

## 🎯 Objetivos e Escopo

### Em Escopo (In-Scope):
* **Módulo de Login (`/login`):**
  * Autenticação com credenciais válidas (Usuário Comum e Administrador).
  * Tratamento de erros com e-mail/senha incorretos ou em branco.
  * Validação de formato/máscara do campo de e-mail no HTML5/Front.
  * Comportamento do componente "Botão Entrar" em diferentes estados.
* **Módulo de Cadastro (`/cadastrarusuarios`):**
  * Redirecionamento correto da tela de login para cadastro.
  * Criação de contas de perfil Administrador e Perfil Padrão.
  * Validação de regra de negócio para e-mails duplicados.
  * Tratamento de campos obrigatórios ausentes.


---

## 📊 Resumo da Execução

| Módulo / Funcionalidade | Casos Planejados | Passou (Pass) | Falhou (Fail) | Taxa de Sucesso |
| :--- | :---: | :---: | :---: | :---: |
| **Login** | 7 | 7 | 0 | 100% |
| **Cadastro** | 7 | 7 | 0 | 100% |
| **Botão Entrar** | 2 | 1 | 1 | 50% |
| **TOTAL** | **16** | **15** | **1** | **93.75%** |

---

## 📝 Detalhamento dos Casos de Teste

### 🔑 1. Módulo de Login (`/login`)

| ID | Caso de Teste | Prioridade | Status | Resultado Esperado |
| :---: | :--- | :---: | :---: | :--- |
| **CT-001** | Autenticação Admin com sucesso | Alta | `PASS` | Redirecionamento para a Dashboard Admin com mensagem *"Bem Vindo Usuário"*. |
| **CT-002** | Autenticação Usuário Comum com sucesso | Alta | `PASS` | Redirecionamento para a Home Store com mensagem *"Serverest Store"*. |
| **CT-003** | Login com E-mail Incorreto | Alta | `PASS` | Exibição da mensagem *"E-mail e/ou senha inválidos"*. |
| **CT-004** | Login com Senha Incorreta | Alta | `PASS` | Exibição da mensagem *"E-mail e/ou senha inválidos"*. |
| **CT-005** | Login com E-mail em branco | Média | `PASS` | Exibição da mensagem de validação *"Email não pode ficar em branco"*. |
| **CT-006** | Login com Senha em branco | Média | `PASS` | Exibição da mensagem de validação *"Password não pode ficar em branco"*. |
| **CT-007** | Login com formato de e-mail inválido | Média | `PASS` | Validação de HTML5/Browser *"Inclua um @ no endereço de e-mail"*. |

---

### 👤 2. Módulo de Cadastro (`/cadastrarusuarios`)

| ID | Caso de Teste | Prioridade | Status | Resultado Esperado |
| :---: | :--- | :---: | :---: | :--- |
| **CT-008** | Redirecionamento via link "Cadastre-se" | Alta | `PASS` | Navegação correta para o formulário de cadastro. |
| **CT-009** | Cadastro de Admin com sucesso | Alta | `PASS` | Mensagem *"Cadastro realizado com sucesso"* e login na Dashboard Admin. |
| **CT-010** | Cadastro de Usuário Comum com sucesso | Alta | `PASS` | Mensagem *"Cadastro realizado com sucesso"* e login na Serverest Store. |
| **CT-011** | Cadastro com e-mail já existente | Alta | `PASS` | Mensagem de erro *"Este e-mail já está sendo usado"* e bloqueio do formulário. |
| **CT-012** | Cadastro com Senha em branco | Alta | `PASS` | Mensagem de erro *"Password não pode ficar em branco"*. |
| **CT-013** | Cadastro com E-mail em branco | Alta | `PASS` | Mensagem de erro *"E-mail não pode ficar em branco"*. |
| **CT-014** | Cadastro com formato de e-mail inválido | Alta | `PASS` | Validação de formato obrigatório de e-mail no input. |

---

### 🔘 3. Módulo Componente: Botão Entrar

| ID | Caso de Teste | Prioridade | Status | Observação / Resultado |
| :---: | :--- | :---: | :---: | :--- |
| **CT-015** | Ativação do botão com dados preenchidos | Alta | `PASS` | Botão funcional ao conter dados para submissão. |
| **CT-016** | Desativação do botão com campos vazios | Baixa | `FAIL` | **BUG:** Botão permanece ativo mesmo sem nenhum dado preenchido. |

---

## 🚨 Relatório de Bugs (Defects Report)

### **[BUG-001] Botão "Entrar" permanece ativado sem o preenchimento de campos obrigatórios**
* **Módulo:** Login (`/login`)
* **Severidade:** Baixa | **Prioridade:** Baixa
* **Caso de Teste Relacionado:** CT-016
* **Descrição:** Ao acessar a tela de login sem digitar e-mail e senha, o botão "Entrar" encontra-se habilitado (`enabled`). O comportamento ideal de UX/UI para evitar chamadas desnecessárias de validação seria manter o botão desabilitado até que os campos mínimos fossem preenchidos.
* **Impacto:** Permite submissões desnecessárias do formulário vazio, gerando alertas no front-end que poderiam ser evitado prevenindo o clique.

---

📥 [Clique aqui para baixar a Planilha de Testes (.xlsx)](./PLANILHA%20DE%20TESTE%20SERVEREST%20-%20Casos%20de%20Teste.xlsx)

