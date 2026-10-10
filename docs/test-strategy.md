# Estratégia de Testes — Restful-Booker Platform

## 1. Objetivo

Definir a abordagem de Quality Assurance (QA) para validar as principais funcionalidades da Restful-Booker Platform, estabelecendo o escopo, os níveis de teste, as técnicas de validação, as ferramentas, os critérios de priorização e os resultados esperados.

O objetivo é identificar defeitos, avaliar riscos, verificar regras de negócio e produzir evidências que permitam avaliar a qualidade e a confiabilidade da aplicação.

## 2. Contexto do projeto

A Restful-Booker Platform será utilizada como aplicação sob teste em um projeto prático de QA que simula o fluxo de trabalho de uma equipe de qualidade de software.

O projeto contempla atividades de análise, planejamento, exploração, execução manual, validação de APIs, verificação de dados, automação e integração contínua.

**Aplicação sob teste:** https://automationintesting.online/

**Gestão das atividades:** Jira

**Repositório de documentação e código:** GitHub

## 3. Escopo dos testes

### 3.1. Dentro do escopo

Serão consideradas as seguintes áreas:

* Interface Web e navegação;
* Visualização e gerenciamento de quartos;
* Consulta de disponibilidade;
* Criação e gerenciamento de reservas;
* Autenticação e autorização;
* Formulário de contato e gerenciamento de mensagens;
* Validações de campos e regras de negócio;
* APIs relacionadas às funcionalidades da aplicação;
* Persistência e consistência dos dados, condicionadas ao acesso disponível ao banco de dados;
* Testes de regressão;
* Automação de fluxos prioritários;
* Execução automatizada e integração contínua.

### 3.2. Fora do escopo inicial

Não fazem parte do escopo inicial:

* Alterações no código-fonte da aplicação sob teste;
* Testes de carga e estresse na instância pública;
* Testes de segurança ofensivos;
* Validação de infraestrutura interna sem acesso autorizado;
* Testes de funcionalidades que não estejam disponíveis ou não possam ser verificadas no ambiente utilizado.

Esses itens poderão ser reconsiderados caso o escopo e as condições técnicas sejam ampliados.

## 4. Abordagem de testes

A estratégia será baseada em uma combinação de testes manuais, exploratórios e automatizados, priorizando as funcionalidades de maior impacto para o negócio.

### 4.1. Testes exploratórios

Serão utilizados para investigar a aplicação, compreender comportamentos, identificar riscos adicionais e descobrir possíveis defeitos ainda não previstos nos cenários iniciais.

As sessões exploratórias terão objetivos definidos e registrarão observações, resultados e evidências relevantes.

### 4.2. Testes funcionais manuais

Serão utilizados para verificar se as funcionalidades atendem aos comportamentos esperados, considerando cenários positivos, negativos, limites de entrada e validações de regras de negócio.

### 4.3. Testes de API

Serão utilizados para verificar a comunicação entre cliente e serviços, incluindo:

* Métodos HTTP;
* Códigos de resposta;
* Estrutura e conteúdo do payload;
* Campos obrigatórios;
* Validação de dados;
* Autenticação e autorização;
* Tratamento de erros;
* Operações de criação, consulta, atualização e exclusão;
* Consistência dos dados retornados.

A ferramenta planejada para essa etapa é o Postman.

### 4.4. Testes de banco de dados

Quando houver acesso autorizado a um banco de dados compatível, serão realizadas consultas para verificar a persistência e a consistência das informações.

A abordagem poderá incluir validação de registros criados, alterações realizadas, exclusões e correspondência entre os dados apresentados pela aplicação e os dados persistidos.

A execução desta etapa depende da confirmação do mecanismo de armazenamento e da disponibilidade de acesso.

### 4.5. Automação Web

O Cypress, utilizando JavaScript, será empregado para automatizar os fluxos funcionais prioritários da interface Web.

A automação será desenvolvida após a compreensão dos comportamentos esperados e a validação inicial dos fluxos manualmente.

### 4.6. Automação de API

As coleções do Postman poderão ser executadas pelo Newman para permitir a repetição dos testes e sua futura integração ao pipeline de CI/CD.

### 4.7. Testes de regressão

Serão utilizados para verificar se alterações, correções ou novas implementações comprometem funcionalidades anteriormente validadas.

A suíte de regressão será formada progressivamente, priorizando os fluxos críticos e os defeitos identificados durante o projeto.

## 5. Priorização baseada em risco

A priorização considerará a probabilidade de ocorrência de uma falha e o impacto que ela poderá causar.

### Prioridade P1 — Crítica

Funcionalidades cuja falha pode comprometer o objetivo principal da aplicação ou permitir ações não autorizadas.

Exemplos:

* Falhas graves de autenticação ou autorização;
* Impossibilidade de concluir reservas;
* Inconsistências graves na disponibilidade;
* Perda ou corrupção relevante de dados.

### Prioridade P2 — Alta

Funcionalidades importantes para a operação, mas cujo impacto depende do cenário e da existência de alternativas.

Exemplos:

* Falhas no gerenciamento de quartos;
* Problemas na atualização ou consulta de reservas;
* Validações incorretas de dados;
* Falhas de integração entre interface e API.

### Prioridade P3 — Normal

Funcionalidades secundárias ou problemas de apresentação cujo impacto sobre as operações principais seja menor.

Exemplos:

* Problemas visuais pontuais;
* Inconsistências de conteúdo;
* Problemas de apresentação que não impeçam o uso das funcionalidades principais.

A prioridade definitiva será atribuída considerando o comportamento observado, o impacto funcional e a probabilidade de ocorrência.

## 6. Ambiente de testes

O ambiente inicial será a instância pública disponibilizada pela Restful-Booker Platform.

**URL:** https://automationintesting.online/

Antes da execução, deverão ser verificadas as condições do ambiente, a disponibilidade da aplicação, as funcionalidades acessíveis e as restrições de utilização.

Como a instância pública pode sofrer alterações ou restaurações de dados, os resultados deverão registrar, quando relevante, a data da execução e as condições observadas.

Os testes deverão evitar operações destrutivas desnecessárias e respeitar os limites do ambiente compartilhado.

## 7. Ferramentas

| Ferramenta     | Finalidade                                                    |
| -------------- | ------------------------------------------------------------- |
| Jira           | Planejamento, acompanhamento e rastreabilidade das atividades |
| Git            | Controle de versão e histórico de alterações                  |
| GitHub         | Repositório de documentação, código e evidências selecionadas |
| Navegador      | Exploração e testes manuais da interface                      |
| Postman        | Testes manuais de API                                         |
| SQL/MySQL      | Consultas e validações de dados, conforme acesso disponível   |
| Cypress        | Automação de testes Web                                       |
| JavaScript     | Desenvolvimento dos testes automatizados                      |
| Newman         | Execução automatizada de coleções Postman                     |
| GitHub Actions | Automação de execução e integração contínua                   |

## 8. Critérios de entrada

Uma atividade de teste poderá ser iniciada quando:

* A funcionalidade ou o fluxo a ser validado estiver identificado;
* O objetivo do teste estiver definido;
* O ambiente estiver acessível, quando necessário;
* Os dados e as credenciais necessários estiverem disponíveis;
* Os pré-requisitos da execução estiverem documentados;
* Os cenários ou procedimentos necessários estiverem preparados para a atividade.

Esses critérios serão aplicados de acordo com o tipo de teste. Uma sessão exploratória, por exemplo, poderá começar antes da existência de casos de teste detalhados.

## 9. Critérios de saída

Uma atividade ou ciclo de testes poderá ser considerado concluído quando:

* Os testes planejados para o ciclo tiverem sido executados ou suas pendências justificadas;
* Os resultados estiverem registrados;
* Os defeitos identificados tiverem sido documentados;
* As evidências relevantes estiverem armazenadas;
* Os riscos residuais e as limitações estiverem registrados;
* Os resultados permitirem comunicar o estado da qualidade da funcionalidade avaliada.

A conclusão do ciclo não significa necessariamente ausência de defeitos. A decisão deverá considerar a severidade dos problemas encontrados, a cobertura alcançada e os riscos conhecidos.

## 10. Registro e gestão de defeitos

Os defeitos identificados serão registrados com informações suficientes para permitir sua compreensão, reprodução e investigação.

Sempre que aplicável, o registro deverá conter:

* Identificação do defeito;
* Título objetivo;
* Ambiente;
* Pré-condições;
* Passos para reprodução;
* Resultado esperado;
* Resultado obtido;
* Severidade e prioridade;
* Evidências;
* Status do defeito.

O Jira será utilizado para acompanhar as atividades e os defeitos conforme a organização definida para o projeto. A documentação complementar poderá ser armazenada no GitHub.

Um comportamento inesperado observado durante a exploração deverá ser investigado antes de ser classificado como defeito confirmado.

## 11. Evidências e rastreabilidade

Os artefatos do projeto serão organizados de forma que seja possível relacionar o planejamento, a execução e os resultados.

O Jira será utilizado para acompanhar o trabalho. O GitHub armazenará os documentos e os arquivos técnicos versionados.

As evidências poderão incluir capturas de tela, requisições e respostas de API, registros de execução, consultas SQL e relatórios automatizados, respeitando as limitações do ambiente e evitando a exposição de dados sensíveis.

A estrutura de pastas definida no repositório será utilizada para organizar esses artefatos.

## 12. Riscos e limitações

Os principais riscos e limitações considerados nesta fase são:

* Instabilidade ou indisponibilidade da instância pública;
* Alterações ou restaurações dos dados do ambiente;
* Ausência de acesso direto ao banco de dados;
* Restrições de autenticação e permissões;
* Diferenças entre o comportamento observado e o comportamento esperado;
* Limitações de tempo para execução de todos os cenários;
* Necessidade de confirmar requisitos e regras de negócio durante a exploração.

Esses fatores deverão ser reavaliados durante a execução, com ajustes no escopo e nas prioridades quando necessário.

## 13. Entregáveis

Os principais entregáveis previstos são:

* Análise inicial da aplicação;
* Estratégia de testes;
* Cenários de teste;
* Casos de teste;
* Registros das sessões exploratórias;
* Registros de defeitos;
* Coleções de testes de API;
* Consultas de validação de dados, quando aplicável;
* Testes automatizados Web;
* Execuções automatizadas de API;
* Suíte de regressão;
* Relatório final de testes;
* Configuração de integração contínua, conforme viabilidade técnica.

## 14. Plano de execução

O trabalho seguirá uma sequência progressiva:

1. Análise da aplicação;
2. Planejamento da estratégia de testes;
3. Definição dos cenários e casos de teste;
4. Execução de testes exploratórios;
5. Execução de testes funcionais manuais;
6. Registro e acompanhamento dos defeitos;
7. Testes de API;
8. Validação de dados, conforme acesso disponível;
9. Automação Web e de API;
10. Regressão;
11. Integração contínua;
12. Consolidação dos resultados e relatório final.

A sequência poderá ser ajustada conforme os resultados das etapas anteriores e as limitações técnicas identificadas.

## 15. Conclusão

Esta estratégia estabelece a abordagem inicial de QA para a Restful-Booker Platform, definindo o escopo, as técnicas, as ferramentas, a priorização por risco e os critérios de acompanhamento dos testes.

O planejamento será refinado progressivamente conforme os comportamentos da aplicação forem confirmados, os cenários forem executados e novas informações forem obtidas.

O objetivo é produzir uma validação organizada, rastreável e baseada em evidências, priorizando os riscos relevantes e construindo uma base consistente para os testes manuais, a automação e a regressão.
