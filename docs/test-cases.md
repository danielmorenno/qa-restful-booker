# Functional Test Cases - Restful-Booker Platform

## 1. Identificação

- **Projeto:** QA Validation — Restful-Booker Platform
- **Aplicação sob teste:** https://automationintesting.online/
- **Tipo de teste:** Testes funcionais manuais
- **Sprint:** Sprint 2 — Functional Test Design
- **Tarefa Jira:** KAN-7 — Elaboração de casos de teste funcionais
- **Responsável:** QA Analyst
- **Status do documento:** Em elaboração

---

## 2. Objetivo

Definir casos de teste funcionais reproduzíveis para verificar os principais comportamentos da aplicação Restful-Booker, incluindo navegação, visualização de quartos, reserva, validação de formulários e autenticação administrativa.

Os casos serão utilizados como base para a execução manual, o registro de defeitos e a futura automação de testes.

---

## 3. Escopo

### 3.1 Incluído

- Carregamento da página inicial.
- Visualização dos quartos e preços.
- Abertura do formulário de reserva.
- Validação de campos obrigatórios na reserva.
- Validação de dados de reserva.
- Preenchimento e validação do formulário de contato.
- Acesso à área administrativa.
- Tentativa de autenticação com credenciais inválidas.

### 3.2 Fora do escopo inicial

- Testes de carga e desempenho.
- Testes aprofundados de segurança.
- Validação direta do banco de dados.
- Automação com Cypress nesta etapa.
- Testes automatizados de API.

---

## 4. Convenções

### Prioridade

- **P1 — Alta:** fluxo crítico ou validação importante para o funcionamento da aplicação.
- **P2 — Média:** funcionalidade relevante, mas de menor criticidade.
- **P3 — Baixa:** comportamento complementar ou de menor impacto.

### Status de execução

Os casos começam com o status **Não executado**. O status somente deverá ser atualizado após a execução e o registro do resultado observado.

- **Não executado:** ainda não realizado nesta etapa.
- **Aprovado:** resultado observado corresponde ao esperado.
- **Reprovado:** resultado observado diverge do esperado.
- **Bloqueado:** não foi possível executar o caso por uma dependência ou impedimento identificado.

---

## 5. Casos de teste

### TC-001 — Carregar a página inicial

- **Prioridade:** P1
- **Categoria:** Navegação
- **Origem:** EXP-001
- **Pré-condições:** acesso à internet disponível.
- **Dados de entrada:** URL `https://automationintesting.online/`.
- **Passos:**
  1. Abrir o navegador.
  2. Acessar a URL da aplicação.
  3. Aguardar o carregamento da página.
- **Resultado esperado:** a página inicial é carregada e os elementos principais da interface ficam visíveis.
- **Resultado obtido:** a página inicial carregou e os elementos principais estavam visíveis. Nenhum erro ou comportamento inesperado foi observado durante a execução.
- **Status:** Aprovado.
- **Evidências:** nenhuma captura de tela registrada nesta execução.

### TC-002 — Visualizar quartos e preços

- **Prioridade:** P1
- **Categoria:** Consulta de informações
- **Origem:** EXP-003
- **Pré-condições:** página inicial acessível.
- **Dados de entrada:** nenhuma entrada específica.
- **Passos:**
  1. Acessar a aplicação.
  2. Localizar a seção de quartos.
  3. Observar as informações apresentadas.
- **Resultado esperado:** os quartos disponíveis na interface apresentam suas informações e preços de forma legível.
- **Resultado obtido:** a seção de quartos foi localizada; os quartos e preços estavam visíveis e totalmente legíveis. Nenhum comportamento inesperado foi observado.
- **Status:** Aprovado.
- **Evidências:** nenhuma captura de tela registrada nesta execução.

### TC-003 — Abrir o formulário de reserva

- **Prioridade:** P1
- **Categoria:** Reserva
- **Origem:** EXP-004
- **Pré-condições:** página inicial carregada.
- **Dados de entrada:** nenhuma entrada específica.
- **Passos:**
  1. Acessar a aplicação.
  2. Localizar um quarto ou a funcionalidade de reserva.
  3. Acionar a opção de reserva.
- **Resultado esperado:** o formulário de reserva é apresentado e permite visualizar os campos disponíveis.
- **Resultado obtido:** conforme informado na execução manual, o teste ocorreu sem problemas.
- **Status:** Aprovado.
- **Evidências:** nenhuma captura de tela registrada nesta execução.


### TC-004 — Validar reserva com campos vazios

- **Prioridade:** P1
- **Categoria:** Validação de formulário
- **Origem:** EXP-005
- **Pré-condições:** formulário de reserva aberto.
- **Dados de entrada:** deixar vazios os campos obrigatórios.
- **Passos:**
  1. Abrir o formulário de reserva.
  2. Não preencher os campos obrigatórios.
  3. Tentar enviar o formulário, se a interface permitir.
  4. Observar as mensagens e o comportamento da interface.
- **Resultado esperado:** a aplicação impede uma submissão inválida ou informa claramente quais campos obrigatórios precisam ser preenchidos.
- **Resultado obtido:** o envio foi impedido. A interface apresentou mensagens de alerta em vermelho indicando os campos vazios e informando que o preenchimento era obrigatório. Nenhum comportamento inesperado foi observado.
- **Status:** Aprovado.
- **Evidências:** nenhuma captura de tela registrada nesta execução.

### TC-005 — Validar dados inválidos na reserva

- **Prioridade:** P1
- **Categoria:** Validação de formulário
- **Origem:** EXP-006
- **Pré-condições:** formulário de reserva acessível.
- **Objetivo:** investigar como a aplicação valida os campos do formulário quando são informados dados potencialmente inválidos.

**Dados de entrada:**
- Nome: `123`
- E-mail: `email-invalido`
- Telefone: `6521819181965198195`
- Last Name: `191918111591`
- Demais campos: preenchidos com dados considerados válidos durante as tentativas.

**Passos:**
1. Acessar o formulário de reserva.
2. Preencher os campos obrigatórios com dados considerados válidos, exceto o campo selecionado para investigação.
3. No campo de nome, informar `123` e enviar a reserva.
4. Repetir o procedimento utilizando `email-invalido` no campo de e-mail.
5. Repetir o procedimento utilizando `6521819181965198195` no campo de telefone.
6. Repetir o procedimento utilizando `191918111591` no campo Last Name.
7. Observar as respostas da aplicação, mensagens de validação, bloqueios e confirmações.
8. Registrar os resultados observados e eventuais comportamentos inesperados.

**Resultados observados:**

- **Nome numérico (`123`):** a aplicação aceitou o valor e confirmou a reserva.
- **E-mail inválido (`email-invalido`):** a aplicação bloqueou o envio, exibiu uma mensagem informando que o e-mail era inválido e destacou visualmente o campo.
- **Telefone com 19 dígitos (`6521819181965198195`):** a aplicação aceitou o valor e confirmou a reserva.
- **Last Name numérico (`191918111591`):** a aplicação aceitou o valor e confirmou a reserva.
- **Erro após envio:** em uma tentativa envolvendo o campo Last Name, a página ficou completamente branca e exibiu um aviso de erro. Após atualizar a página, o conteúdo do quarto voltou a aparecer, mas o indicador de carregamento permaneceu ativo. O comportamento ocorreu novamente após a atualização. Em uma tentativa posterior com Last Name numérico, a reserva foi confirmada normalmente.

**Resultado esperado:**

A aplicação deve validar os dados conforme as regras definidas para cada campo, impedir o envio de valores inválidos e apresentar mensagens claras quando necessário. Após o envio, deve concluir o processamento da reserva ou informar adequadamente a ocorrência de um erro.

**Análise inicial:**

- A validação do e-mail funcionou conforme esperado para o valor utilizado.
- Os campos de nome e Last Name aceitaram valores compostos apenas por números. É necessário confirmar as regras esperadas desses campos antes de classificar o comportamento como defeito.
- O telefone aceitou um valor de 19 dígitos. É necessário confirmar o formato e o limite de caracteres previstos.
- O erro de página e o carregamento incompleto precisam ser investigados separadamente, pois a causa não foi identificada e a reserva foi confirmada em uma tentativa posterior.

- **Evidências:** captura de tela disponível do carregamento incompleto após a atualização. Não foi registrada captura do primeiro aviso de erro.
- **Status:** Em investigação — execução parcial concluída.
- **Observações:** os resultados registrados correspondem às tentativas realizadas. As regras de validação esperadas ainda precisam ser confirmadas antes da classificação definitiva de possíveis defeitos.

**Investigação complementar — INV-001: Falha na criação da reserva**

- **Contexto:** durante uma tentativa de reserva com primeiro nome e sobrenome compostos por números, a interface apresentou uma mensagem de falha de carregamento.
- **Método HTTP:** `POST`
- **Endpoint:** `/api/booking`
- **Status HTTP:** `409 Conflict`
- **Resposta da API:** `{"error":"Failed to create booking"}`
- **Dados relevantes enviados:**
  - `roomid`: `2`
  - `firstname`: valor numérico
  - `lastname`: valor numérico
  - `depositpaid`: `false`
  - `bookingdates.checkin`: `2026-10-20`
  - `bookingdates.checkout`: `2026-10-21`
  - `phone`: valor de 11 dígitos
  - `email`: omitido deste registro por privacidade.
- **Resultado observado:** a API não criou a reserva nessa tentativa e retornou o erro informado. A interface exibiu uma mensagem de falha.
- **Reprodução:** o comportamento foi observado durante a investigação com nomes numéricos. Ainda não foi confirmado que esses valores sejam a causa.
- **Evidências:** captura de tela da interface após a atualização e dados da requisição no Network, incluindo status HTTP, endpoint e resposta.
- **Causa raiz:** não identificada.
- **Status da investigação:** em andamento.
- **Próxima ação:** comparar o comportamento com dados nominais válidos, mantendo as demais condições equivalentes, e verificar se o conflito pode estar relacionado à disponibilidade do quarto ou a outra regra da aplicação.

### INV-002 — Falha no carregamento dos dados dos quartos

- **Origem:** Execução do TC-006 — Visualizar o formulário de contato.
- **Categoria:** Disponibilidade / Carregamento de dados.
- **Prioridade sugerida:** P1 — sujeita à confirmação do impacto.
- **Ambiente:** https://automationintesting.online/
- **Endpoint observado:** `/api/room/1`
- **Método HTTP:** GET
- **Status HTTP:** `500 Internal Server Error`

**Contexto:**

Durante a execução do TC-006, ao acessar o fluxo de reserva de um quarto, a aplicação deixou de carregar os dados e permaneceu em um ciclo de carregamento contínuo. O comportamento, que anteriormente não havia sido observado, também ocorreu em uma janela anônima do navegador.

**Resultado observado:**

- A requisição GET para `/api/room/1` retornou HTTP 500.
- O corpo da resposta apresentou `Internal Server Error`.
- O Console registrou o erro: `Unexpected token 'I', "Internal S"... is not valid JSON`.
- A interface permaneceu em carregamento contínuo, sem concluir a navegação.
- O comportamento foi observado também ao tentar acessar outros quartos.

**Resultado esperado:**

A aplicação deve carregar os dados dos quartos normalmente. Caso ocorra uma falha no servidor, deve apresentar uma mensagem compreensível ao usuário, sem permanecer em carregamento infinito.

**Evidências:**

- Captura do Network mostrando a resposta HTTP 500.
- Corpo da resposta: `Internal Server Error`.
- Mensagem de erro registrada no Console.
- Captura da interface em carregamento contínuo.

**Causa raiz:** Não identificada.

**Status:** Investigação em andamento.

**Observação:** Não foi possível determinar se a falha decorre de uma alteração recente na aplicação, instabilidade do servidor ou outro problema interno. A ocorrência foi observada durante a execução do TC-006 e deve ser investigada separadamente do objetivo principal desse caso de teste.

### TC-006 — Visualizar o formulário de contato

- **Prioridade:** P2
- **Categoria:** Contato
- **Origem:** EXP-007
- **Pré-condições:** Aplicação acessível.
- **Dados de teste:** Não se aplica.

**Passos:**
1. Acessar a página inicial da aplicação.
2. Localizar a seção de contato.
3. Verificar se o formulário está visível.
4. Inspecionar os campos disponíveis e suas identificações.

**Resultado esperado:**

O formulário de contato deve estar visível e apresentar seus campos devidamente identificados, permitindo que o usuário visualize e preencha as informações solicitadas.

**Resultado observado:**

Não foi possível acessar e verificar o formulário de contato devido a uma falha no carregamento da aplicação. Durante a tentativa de navegação, a interface permaneceu em carregamento contínuo.

Foi identificada uma resposta HTTP 500 na requisição GET `/api/room/1`, acompanhada de erro de interpretação da resposta no Console do navegador.

A ocorrência foi registrada separadamente na investigação INV-002 — Falha no carregamento dos dados dos quartos.

**Evidências:**
- Captura do Console mostrando o erro de carregamento.
- Captura do Network mostrando a resposta HTTP 500.
- Captura da interface em carregamento contínuo.

**Status:** Bloqueado — impedido por falha de carregamento da aplicação.

**Próxima ação:** Retomar a execução deste caso de teste após a normalização do funcionamento da aplicação.

### TC-007 — Validar formulário de contato com dados ausentes ou inválidos

- **Prioridade:** P2
- **Categoria:** Validação de formulário
- **Origem:** EXP-008
- **Pré-condições:** Formulário de contato acessível.
- **Dados de entrada:** Campos obrigatórios vazios ou valores inválidos adequados aos campos disponíveis.

**Passos:**
1. Abrir o formulário de contato.
2. Deixar vazios os campos obrigatórios ou inserir um valor inválido.
3. Tentar enviar o formulário.
4. Observar as mensagens e o comportamento da interface.

**Resultado esperado:**

Os campos inválidos devem ser sinalizados e a aplicação deve informar o que precisa ser corrigido antes do envio.

**Resultado observado:**

Não foi possível executar o caso de teste devido à indisponibilidade da aplicação. A falha de carregamento identificada durante a tentativa de navegação impede o acesso ao formulário de contato.

A ocorrência está documentada na investigação INV-002 — Falha no carregamento dos dados dos quartos.

**Status:** Bloqueado — impedido por falha de carregamento da aplicação.

**Próxima ação:** Retomar a execução após a normalização do funcionamento da aplicação.

### TC-008 — Acessar a área administrativa

- **Prioridade:** P1
- **Categoria:** Autenticação
- **Origem:** EXP-009
- **Pré-condições:** Aplicação acessível.
- **Dados de entrada:** Acesso à opção administrativa.

**Passos:**
1. Acessar a aplicação.
2. Localizar a opção de administração.
3. Acionar o acesso administrativo.

**Resultado esperado:**

A tela de autenticação administrativa ou a área correspondente deve ser apresentada corretamente.

**Resultado observado:**

Não foi possível executar o caso de teste devido à falha de carregamento da aplicação, que impede a navegação normal pela interface.

A ocorrência está documentada na investigação INV-002 — Falha no carregamento dos dados dos quartos.

**Status:** Bloqueado — impedido por falha de carregamento da aplicação.

**Próxima ação:** Retomar a execução após a normalização do funcionamento da aplicação.

### TC-009 — Tentar autenticação com credenciais inválidas

- **Prioridade:** P1
- **Categoria:** Autenticação negativa
- **Origem:** EXP-010
- **Pré-condições:** Tela de login administrativo aberta.
- **Dados de entrada:**
  - Username: `usuario_teste_999`
  - Password: senha fictícia inválida.

**Passos:**
1. Abrir a tela de login administrativo.
2. Inserir credenciais inválidas.
3. Enviar o formulário.
4. Observar o resultado da tentativa.

**Resultado esperado:**

O acesso deve ser negado e a interface deve apresentar um retorno adequado, sem autenticar o usuário.

**Resultado observado:**

- O sistema negou a autenticação.
- A mensagem `Invalid credentials` foi apresentada na interface.
- A tela permaneceu no login, sem redirecionamento para a área administrativa.
- Não foi possível acessar a área administrativa com as credenciais inválidas.

**Status:** Aprovado.
---

## 6. Rastreabilidade

| Caso de teste | Cenário exploratório relacionado |
|---|---|
| TC-001 | EXP-001 |
| TC-002 | EXP-003 |
| TC-003 | EXP-004 |
| TC-004 | EXP-005 |
| TC-005 | EXP-006 |
| TC-006 | EXP-007 |
| TC-007 | EXP-008 |
| TC-008 | EXP-009 |
| TC-009 | EXP-010 |

A rastreabilidade conecta os casos de teste aos cenários exploratórios que motivaram sua elaboração. A existência de um cenário exploratório anterior não substitui a execução formal do respectivo caso de teste.

---

## 7. Critérios para execução

Antes de executar cada caso:

1. Confirmar que a aplicação está acessível.
2. Verificar as pré-condições.
3. Utilizar os dados de entrada descritos ou registrar os dados efetivamente utilizados.
4. Executar os passos na ordem apresentada.
5. Comparar o resultado observado com o resultado esperado.
6. Registrar o status e, em caso de reprovação, coletar evidências.
7. Investigar resultados inesperados antes de registrar um defeito.

---

## 8. Próximas ações

- Revisar os casos de teste e confirmar as regras observáveis na aplicação.
- Definir dados de entrada específicos para cada cenário de validação.
- Executar os casos manualmente e registrar os resultados reais.
- Completar a investigação do cenário EXP-006.
- Criar registros de defeitos quando forem observadas divergências reproduzíveis.
- Utilizar os casos prioritários como base para a futura automação com Cypress.

---

## 9. Conclusão

Este documento estabelece a primeira versão dos casos de teste funcionais do projeto QA Validation — Restful-Booker Platform.

Os casos foram derivados da análise da aplicação e da exploração inicial. Seus resultados permanecem como não executados nesta etapa e deverão ser atualizados com base em execuções formais e evidências correspondentes.