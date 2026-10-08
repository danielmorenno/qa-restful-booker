# Análise da Aplicação - Restful-Booker Platform

## 1. Objetivo

Realizar o levantamento inicial da aplicação Restful-Booker Platform com o objetivo de compreender suas principais funcionalidades, fluxos de negócio, pontos de entrada, integrações e riscos.

Esta análise será utilizada como base para a definição da estratégia de testes e para o planejamento das atividades de QA do projeto.


## 2. Visão geral da aplicação

O Restful-Booker Platform é uma aplicação web voltada para o gerenciamento de um estabelecimento de hospedagem, permitindo que usuários consultem quartos disponíveis e realizem reservas.

A plataforma também possui uma área administrativa destinada ao gerenciamento das informações do estabelecimento.

A aplicação disponibiliza uma interface web e uma arquitetura baseada em APIs, permitindo que diferentes componentes da plataforma sejam validados de forma independente e também por meio de fluxos integrados.

A instância utilizada neste projeto é:

**https://automationintesting.online/**

A aplicação possui dados previamente cadastrados e a instância pública pode ser restaurada periodicamente ao seu estado inicial.


## 3. Principais áreas identificadas

### 3.1 Página inicial

A página inicial apresenta informações gerais sobre o estabelecimento e funciona como principal ponto de entrada da aplicação.

Entre os elementos identificados estão:

* Informações e apresentação do estabelecimento;
* Listagem de quartos;
* Informações relacionadas aos quartos;
* Área para consulta de disponibilidade;
* Formulário de contato;
* Informações de localização;
* Acesso à área administrativa.

A página inicial utiliza informações provenientes de dados armazenados na aplicação, incluindo configurações de branding, quartos e informações de contato.


### 3.2 Quartos

A aplicação permite visualizar os quartos disponíveis no estabelecimento.

Os quartos possuem informações como:

* Nome ou identificação;
* Tipo;
* Preço;
* Descrição;
* Imagem;
* Acessibilidade;
* Características do quarto.

No contexto administrativo, os quartos podem ser gerenciados, incluindo operações de criação, consulta, atualização e exclusão.

A API de quartos disponibiliza operações autenticadas para gerenciamento dessas informações.


### 3.3 Consulta de disponibilidade

A aplicação possui funcionalidades relacionadas à consulta de disponibilidade dos quartos.

Esse fluxo envolve principalmente:

1. Seleção de período;
2. Consulta de disponibilidade;
3. Apresentação dos quartos disponíveis;
4. Seleção do quarto;
5. Continuação para o processo de reserva.

A disponibilidade é uma funcionalidade crítica porque influencia diretamente a possibilidade de realização de uma reserva.



### 3.4 Reserva

A reserva representa um dos principais fluxos de negócio da aplicação.

O processo envolve informações como:

* Quarto;
* Nome do hóspede;
* Sobrenome;
* Datas de entrada e saída;
* Informação de pagamento do depósito;
* E-mail;
* Telefone.

Na API, existem operações para criação, consulta, atualização e exclusão de reservas. Algumas operações administrativas exigem autenticação.

O fluxo de reserva deve receber prioridade nos testes devido ao seu impacto direto no objetivo principal da aplicação.


### 3.5 Formulário de contato

A aplicação disponibiliza um formulário para envio de mensagens ao estabelecimento.

Esse fluxo envolve o preenchimento de dados pelo usuário e o envio das informações para o sistema.

Devem ser considerados nos testes:

* Campos obrigatórios;
* Formato dos dados;
* Dados inválidos;
* Campos vazios;
* Limites de caracteres;
* Envio com sucesso;
* Mensagens de validação;
* Persistência da mensagem na área administrativa.



### 3.6 Área administrativa

A aplicação possui uma área administrativa acessível por autenticação.

Essa área concentra funcionalidades de gerenciamento do estabelecimento.

Entre as principais áreas estão:

* Dashboard;
* Gerenciamento de quartos;
* Gerenciamento de reservas;
* Mensagens;
* Branding/configurações;
* Relatórios;
* Logout.

A área administrativa representa uma área de maior risco porque concentra operações de alteração de dados e funcionalidades que não devem estar disponíveis para usuários não autorizados.

A arquitetura da plataforma utiliza um serviço específico de autenticação para controlar o acesso a operações protegidas.



## 4. Autenticação e autorização

A plataforma possui uma API específica de autenticação.

O processo de autenticação permite gerar um token utilizado para acessar determinadas operações protegidas.

As APIs de gerenciamento utilizam esse mecanismo para validar se o usuário possui autorização para executar determinadas ações.

Os testes deverão verificar principalmente:

* Login com credenciais válidas;
* Login com credenciais inválidas;
* Acesso sem autenticação;
* Acesso com token inválido;
* Expiração ou invalidação do token;
* Logout;
* Controle de acesso às funcionalidades administrativas.



## 5. APIs identificadas

A plataforma é composta por diferentes APIs responsáveis por partes específicas do sistema.

Foram identificados serviços relacionados a:

| Serviço  | Responsabilidade                        |
| -------- | --------------------------------------- |
| Auth     | Autenticação e autorização              |
| Room     | Gerenciamento de quartos                |
| Booking  | Gerenciamento de reservas               |
| Message  | Gerenciamento de mensagens              |
| Branding | Configurações e identidade da aplicação |
| Report   | Relatórios                              |
| Assets   | Recursos utilizados pela aplicação      |

Essa separação permite realizar testes individuais das APIs e também validar os fluxos integrados entre diferentes serviços.



## 6. Principais fluxos críticos

Com base no levantamento inicial, os seguintes fluxos são considerados prioritários:

### Fluxo 1 — Consulta de quartos

```text
Acessar aplicação
→ Visualizar quartos
→ Consultar informações
→ Verificar disponibilidade
```

### Fluxo 2 — Realização de reserva

```text
Consultar disponibilidade
→ Selecionar quarto
→ Informar dados
→ Selecionar período
→ Confirmar reserva
→ Validar resultado
```

### Fluxo 3 — Autenticação administrativa

```text
Acessar área administrativa
→ Informar credenciais
→ Autenticar
→ Acessar dashboard
```

### Fluxo 4 — Gerenciamento de quartos

```text
Login administrativo
→ Acessar quartos
→ Criar/consultar/alterar/excluir quarto
→ Validar resultado
```

### Fluxo 5 — Gerenciamento de reservas

```text
Login administrativo
→ Acessar reservas
→ Consultar reserva
→ Alterar ou excluir
→ Validar resultado
```

### Fluxo 6 — Comunicação

```text
Preencher formulário
→ Enviar mensagem
→ Validar envio
→ Acessar área administrativa
→ Validar mensagem recebida
```



## 7. Principais riscos identificados

### Risco 1 — Disponibilidade incorreta

Uma falha na consulta de disponibilidade pode permitir que um quarto seja apresentado como disponível quando não deveria estar.

**Impacto:** alto.



### Risco 2 — Falha na criação de reservas

Problemas durante a criação ou confirmação de uma reserva podem impedir o usuário de concluir o objetivo principal da aplicação.

**Impacto:** alto.



### Risco 3 — Conflito de reservas

Uma inconsistência entre disponibilidade e reservas pode permitir reservas para períodos incompatíveis.

**Impacto:** alto.



### Risco 4 — Falhas de autenticação/autorização

Usuários não autorizados podem conseguir acessar ou alterar informações administrativas.

**Impacto:** crítico.



### Risco 5 — Inconsistência entre interface e API

A interface pode apresentar um comportamento aparentemente correto enquanto os dados persistidos ou retornados pelas APIs estão incorretos.

**Impacto:** alto.



### Risco 6 — Integridade dos dados

Operações de criação, atualização e exclusão podem gerar dados inconsistentes caso não sejam corretamente processadas.

**Impacto:** alto.



### Risco 7 — Validação inadequada dos dados

Dados inválidos ou incompletos podem ser aceitos pelo sistema ou gerar comportamentos inesperados.

**Impacto:** médio/alto.



### Risco 8 — Comunicação entre serviços

Como a plataforma utiliza diferentes APIs para funcionalidades específicas, uma falha de integração entre serviços pode afetar fluxos completos da aplicação.

**Impacto:** alto.



## 8. Áreas que serão testadas

O projeto terá como escopo inicial:

* Interface Web;
* Fluxo de consulta de quartos;
* Disponibilidade;
* Reservas;
* Área administrativa;
* Autenticação;
* Autorização;
* Formulário de contato;
* Gerenciamento de quartos;
* Gerenciamento de reservas;
* Mensagens;
* APIs;
* Persistência de dados;
* Integração entre serviços;
* Regressão;
* Automação Web;
* Automação de API.



## 9. Estratégia inicial de validação

A estratégia de QA será construída progressivamente, combinando diferentes técnicas e níveis de teste.

### Testes manuais

Serão utilizados para validar funcionalidades e comportamentos da aplicação sob a perspectiva do usuário.

### Testes exploratórios

Serão utilizados para investigar comportamentos não cobertos inicialmente pelos casos de teste e identificar riscos adicionais.

### Testes de API

Serão realizados utilizando Postman, avaliando requisições, respostas, códigos HTTP, dados e regras de negócio.

### Testes de banco de dados

Serão utilizados para validar a persistência e a consistência dos dados por meio de consultas SQL.

### Automação Web

Será utilizada para automatizar fluxos críticos da interface utilizando Cypress e JavaScript.

### Automação de API

Será realizada utilizando Newman para execução automatizada das coleções do Postman.

### Regressão

Será utilizada para verificar se alterações realizadas na aplicação introduziram impactos em funcionalidades anteriormente validadas.



## 10. Pontos de atenção para as próximas etapas

Durante a execução dos testes, deverão ser investigados especialmente:

* Comportamento de datas de check-in e check-out;
* Disponibilidade de quartos;
* Reservas sobrepostas;
* Campos obrigatórios;
* Formatos inválidos;
* Limites de entrada;
* Autenticação;
* Autorização;
* Persistência das informações;
* Consistência entre UI, API e banco de dados;
* Tratamento de erros;
* Operações CRUD;
* Comunicação entre serviços;
* Comportamento após alterações;
* Regressão das funcionalidades críticas.



## 11. Escopo inicial

### Dentro do escopo

* Aplicação Web;
* APIs da plataforma;
* Fluxos de reserva;
* Área administrativa;
* Autenticação e autorização;
* Gerenciamento de quartos;
* Gerenciamento de reservas;
* Mensagens;
* Persistência de dados;
* Automação;
* Regressão;
* Integração contínua.

### Fora do escopo inicial

* Testes de infraestrutura em produção;
* Testes de carga e estresse em ambiente público;
* Testes de segurança ofensivos;
* Alterações no código-fonte da aplicação;
* Testes de infraestrutura que não estejam relacionados diretamente à validação da aplicação.



## 12. Conclusão

O levantamento inicial demonstra que o Restful-Booker possui complexidade suficiente para a construção de um projeto de QA completo.

A existência de uma interface Web, múltiplas APIs, autenticação, operações de gerenciamento, reservas e persistência de dados permite trabalhar diferentes níveis de validação.

A partir desta análise, os próximos passos serão definir a estratégia detalhada de testes, estabelecer prioridades com base em risco, elaborar cenários e casos de teste e iniciar a execução exploratória.

A abordagem adotada será progressiva:

**Analisar → Planejar → Explorar → Testar → Reportar → Automatizar → Validar → Integrar**
