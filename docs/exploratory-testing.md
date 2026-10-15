# Exploratory Testing — Restful-Booker Platform

## 1. Identificação da Sessão

- **Projeto:** QA Validation — Restful-Booker Platform
- **Aplicação sob teste:** https://automationintesting.online/
- **Tipo de teste:** Teste exploratório manual
- **Responsável:** QA Analyst
- **Ambiente:** Aplicação web pública de demonstração
- **Status da sessão:** Exploração inicial realizada
- **Gerenciamento da atividade:** Jira — KAN-5
- **Repositório:** https://github.com/danielmorenno/qa-restful-booker

---

## 2. Objetivo

Realizar uma exploração inicial da plataforma Restful-Booker para compreender o comportamento das principais funcionalidades, avaliar respostas da interface, investigar validações e identificar possíveis defeitos.

A exploração também tem como objetivo levantar informações para a elaboração de casos de teste funcionais, orientar futuras validações de API e apoiar a implementação de testes automatizados.

---

## 3. Escopo da Exploração

A sessão contemplou os seguintes elementos:

- Carregamento e apresentação da página inicial.
- Navegação geral pela aplicação.
- Visualização da listagem de quartos e preços.
- Abertura do formulário de reserva.
- Validação do formulário de reserva com campos vazios.
- Exploração do formulário de contato.
- Validação do formulário de contato.
- Acesso à área administrativa.
- Tentativa de autenticação com credenciais inválidas.

### 3.1 Itens fora do escopo desta sessão

Os seguintes itens não foram considerados concluídos nesta exploração inicial:

- Testes automatizados de interface com Cypress.
- Testes automatizados de API com Newman.
- Validação direta do banco de dados com SQL/MySQL.
- Testes de carga e desempenho.
- Testes de segurança aprofundados.
- Validação completa de todos os campos e combinações possíveis.
- Testes exaustivos de regras de negócio e integrações.

Esses itens poderão ser abordados em etapas posteriores do projeto.

---

## 4. Estratégia de Teste Exploratório

A exploração foi conduzida manualmente, utilizando a interface web da aplicação para observar o comportamento dos principais fluxos.

A abordagem priorizou funcionalidades relacionadas à navegação, reserva, validação de formulários e autenticação administrativa.

Durante a exploração, foram observados os elementos apresentados pela interface, as respostas às tentativas de envio de dados e o comportamento diante de credenciais inválidas.

Os resultados foram registrados com base nas observações realizadas durante a sessão. A ausência de defeitos identificados não representa garantia de ausência de defeitos na aplicação.

---

## 5. Cenários Exploratórios e Resultados

| ID | Cenário | Prioridade | Resultado observado | Situação |
|---|---|---|---|---|
| EXP-001 | Acessar e carregar a página inicial | Alta | Página carregada com cabeçalho e conteúdo principal visíveis | Explorado |
| EXP-002 | Navegar pela página e identificar as seções | Média | Navegação geral explorada; detalhes específicos não registrados | Explorado parcialmente |
| EXP-003 | Verificar a apresentação dos quartos e preços | Alta | Listagem de quartos e informações de preços visíveis | Explorado |
| EXP-004 | Abrir o fluxo de reserva | Alta | Formulário de reserva aberto e campos disponíveis | Explorado |
| EXP-005 | Tentar enviar a reserva com campos vazios | Alta | Mensagens ou indicações de campos obrigatórios apresentadas | Sem bug identificado |
| EXP-006 | Informar dados inválidos nos campos da reserva | Alta | Cenário ainda sem resultado específico registrado | Pendente |
| EXP-007 | Explorar o formulário de contato | Média | Formulário acessado e campos explorados | Explorado |
| EXP-008 | Tentar enviar contato com campos vazios ou inválidos | Média | Campos inválidos ou obrigatórios indicados | Sem bug identificado |
| EXP-009 | Acessar a área administrativa | Alta | Área administrativa ou tela de login acessada | Explorado |
| EXP-010 | Tentar login com credenciais inválidas | Alta | Acesso negado com mensagem de erro | Sem bug identificado |

### 5.1 Interpretação dos resultados

Nos cenários EXP-005 e EXP-008, a interface apresentou indicações de campos obrigatórios ou inválidos, conforme observado durante a exploração.

No cenário EXP-010, o acesso foi negado e uma mensagem de erro foi apresentada após a tentativa de autenticação com credenciais inválidas.

Esses comportamentos são compatíveis com as expectativas iniciais de validação de formulários e controle de acesso.

Entretanto, a validação completa das regras de negócio e de segurança exige testes adicionais.

---

## 6. Registro de Defeitos

Durante a exploração inicial, não foram identificados bugs nos cenários relatados.

Nenhum defeito foi registrado nesta sessão.

A ausência de bugs identificados deve ser interpretada dentro dos limites do escopo explorado. Outros defeitos podem existir em funcionalidades, condições ou combinações de dados ainda não investigadas.

Caso um comportamento inesperado seja identificado em sessões futuras, deverá ser registrado com:

- Identificador do defeito.
- Título objetivo.
- Ambiente de reprodução.
- Pré-condições.
- Passos para reproduzir.
- Resultado esperado.
- Resultado atual.
- Severidade e prioridade sugeridas.
- Evidências associadas.

---

## 7. Evidências de Teste

As evidências da sessão são organizadas no diretório `evidence/` do repositório.

### ### 7.1 Evidências disponíveis

Foram selecionadas duas capturas de tela para compor as evidências desta sessão exploratória.

| Arquivo | Cenário relacionado |
|---|---|
| `EXP-008-contact-validation.png` | Validação do formulário de contato com campos vazios ou inválidos |
| `EXP-010-invalid-login.png` | Tentativa de autenticação com credenciais inválidas |

As demais capturas previstas inicialmente não serão incluídas nesta entrega. Os resultados dos outros cenários permanecem documentados com base nas observações realizadas durante a exploração, sem que isso implique a existência de evidências visuais anexadas para todos eles.

A correspondência entre cada captura e o resultado registrado deve ser conferida antes da publicação final do repositório.

### 7.2 Importância das evidências

As capturas de tela permitem demonstrar os estados observados da aplicação, facilitam a revisão dos resultados e ajudam a reproduzir ou investigar comportamentos inesperados.

As evidências também apoiam a rastreabilidade entre cenários exploratórios, documentação, tarefas do Jira e futuros casos de teste.

---

## 8. Riscos e Limitações

Durante a interpretação dos resultados, devem ser consideradas as seguintes limitações:

- A aplicação é uma instância pública de demonstração e pode sofrer alterações.
- Os dados e estados da aplicação podem ser restaurados periodicamente.
- Os resultados representam apenas os cenários explorados.
- Não foram executados testes automatizados nesta sessão.
- Não foi realizada validação direta de dados no banco de dados.
- Não foi realizada avaliação aprofundada de segurança ou desempenho.
- O cenário EXP-006 permanece pendente de validação específica.
- Apenas os cenários EXP-008 e EXP-010 possuem capturas de tela incluídas nesta entrega.
- Os demais resultados exploratórios estão documentados, mas não possuem capturas anexadas ao repositório.

---

## 9. Próximas Ações

Com base nos resultados da exploração inicial, as próximas atividades recomendadas são:

1. Validar o cenário EXP-006, utilizando dados inválidos no formulário de reserva.
2. Conferir a correspondência entre os resultados registrados e as capturas de tela.
3. Transformar os cenários relevantes em casos de teste funcionais.
4. Detalhar pré-condições, dados de entrada, passos e resultados esperados.
5. Executar os casos de teste e registrar seus resultados.
6. Investigar possíveis defeitos encontrados durante as próximas execuções.
7. Utilizar os casos de teste como base para a automação com Cypress e JavaScript.
8. Avançar posteriormente para os testes de API com Postman e Newman.

---

## 10. Conclusão

A exploração inicial da Restful-Booker permitiu investigar os principais elementos da interface, o fluxo de reserva, as validações dos formulários e o acesso administrativo.

Nos cenários relatados, não foram identificados bugs. As observações registradas fornecem uma base inicial para o aprofundamento dos testes funcionais.

A continuidade da validação deverá priorizar a investigação dos cenários ainda pendentes, a consolidação das evidências e a criação de casos de teste reproduzíveis.

Esta documentação representa uma etapa inicial do processo de Quality Assurance do projeto QA Validation — Restful-Booker Platform.