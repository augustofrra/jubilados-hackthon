# Registro de Prompts — Projeto ANTECIPE V5

## 1. Apresentação

Este documento registra o uso de ferramentas de Inteligência Artificial durante o desenvolvimento do **ANTECIPE V5**, uma plataforma de gerenciamento, análise e validação de recebíveis financeiros.

O projeto foi desenvolvido com auxílio do ChatGPT, da OpenAI, para planejamento da arquitetura, geração e revisão de código, identificação de erros, implementação de funcionalidades, elaboração de testes e documentação.

O objetivo deste registro é garantir transparência sobre a utilização de IA e demonstrar a evolução do projeto.

**Ferramentas utilizadas:**
- ChatGPT — OpenAI.
- Codex — OpenAI, utilizado ou solicitado para auxiliar na revisão e auditoria do código.
- Visual Studio Code — Ambiente de desenvolvimento.
- GitHub — Versionamento e armazenamento do projeto.

**Observação:** os prompts abaixo foram organizados e resumidos a partir das solicitações realizadas durante o desenvolvimento. Não representam necessariamente transcrições literais de todas as mensagens.

---

## 2. Prompt 1 — Concepção inicial

**Objetivo:** desenvolver uma plataforma de análise de recebíveis.

**Solicitação:**

> Crie um sistema capaz de receber diversos arquivos CSV contendo informações de notas fiscais e recebíveis, armazenando todos os dados em um banco de dados centralizado.
>
> O programa também deverá receber arquivos com regras de validação, analisar os recebíveis, identificar quais estão aptos à antecipação e apresentar os motivos específicos de cada recusa.
>
> Desenvolva uma interface profissional, com filtros, tabelas, indicadores financeiros e gráficos.

**Tecnologias escolhidas:**
- Python.
- HTML.
- CSS.
- JavaScript.
- SQLite.

---

## 3. Prompt 2 — Importação e armazenamento

**Objetivo:** implementar a importação automática de arquivos.

**Solicitação:**

> Desenvolva um sistema que receba arquivos CSV, JSON e ZIP, identifique automaticamente o tipo de informação e armazene os registros em um banco SQLite.
>
> Todas as importações devem ser registradas, permitindo consultar dados anteriores sem perder informações.
>
> Evite arquivos duplicados e apresente mensagens explicativas sobre o resultado das importações.

**Funcionalidades solicitadas:**
- Importação de recebíveis.
- Importação de cadastros de CNPJ.
- Leitura de regras JSON.
- Armazenamento persistente.
- Histórico de importações.
- Identificação de arquivos duplicados.

---

## 4. Prompt 3 — Desenvolvimento da interface

**Objetivo:** criar um dashboard financeiro profissional.

**Solicitação:**

> Melhore a interface do sistema para que seja visualmente semelhante às plataformas financeiras modernas, utilizando como inspiração a identidade visual da Kanastra.
>
> Crie um menu lateral profissional, gráficos, indicadores e filtros que facilitem a análise de grandes volumes de recebíveis.
>
> A interface deve ser simples, intuitiva e apresentar explicações claras sobre os resultados.

**Elementos solicitados:**
- Dashboard financeiro.
- Menu lateral.
- Indicadores de carteira.
- Tabelas de recebíveis.
- Gráficos de aprovação e reprovação.
- Filtros por período.
- Filtros por fundo e empresa.
- Filtros por situação cadastral.
- Motivos de recusa.
- Histórico de arquivos.

---

## 5. Prompt 4 — Sistema de autenticação

**Objetivo:** restringir o acesso aos dados.

**Solicitação:**

> Implemente uma página de login, permitindo criar uma conta de administrador na primeira execução.
>
> O sistema deverá proteger as informações de acesso, solicitar autenticação e permitir encerrar a sessão.

**Funcionalidades solicitadas:**
- Cadastro inicial de administrador.
- Login com usuário e senha.
- Armazenamento protegido das credenciais.
- Controle de sessão.
- Botão de logout.

---

## 6. Prompt 5 — Implementação dos validadores JSON

**Objetivo:** executar as regras financeiras fornecidas no desafio.

**Solicitação:**

> Implemente no sistema os validadores definidos no arquivo JSON do fundo ANTECIPE FIDC.
>
> As regras devem ser interpretadas dinamicamente, respeitando seus parâmetros e o estado ativo ou inativo.
>
> Para cada recebível, apresente o resultado da análise e os motivos específicos de reprovação.

### Regras fornecidas

| Código | Configuração | Ativa |
|---|---|---|
| CNPJ_SACADO_VALIDO | Validar CNPJ do sacado | Sim |
| SITUACAO_CADASTRAL_SACADO | Aceitar somente ATIVA | Sim |
| TIPO_RECEBIVEL | Duplicata ou Duplicata de Serviço | Sim |
| VALOR_MINIMO | R$ 100,00 | Sim |
| NAO_VENCIDA | Verificar vencimento | Sim |
| PRAZO_MAXIMO | 180 dias | Sim |
| CONCENTRACAO_MAXIMA_SACADO | 10% por raiz do CNPJ | Sim |
| PRAZO_MINIMO | 30 dias | Não |
| CONCENTRACAO_MAXIMA_CEDENTE | 8% | Não |

O sistema também deveria registrar todas as regras violadas por cada recebível, e não somente a primeira.

---

## 7. Prompt 6 — Precificação dos recebíveis

**Objetivo:** calcular o valor estimado de antecipação.

**Solicitação:**

> Implemente a precificação financeira utilizando desconto simples, com taxa mensal de 2% e base de cálculo de 30 dias.
>
> Utilize a diferença entre a data de aquisição e a data de vencimento para determinar o prazo.
>
> Apresente o valor nominal, o desconto calculado e o valor estimado disponível para antecipação.

### Fórmula utilizada

\[
VA = VN \times \left(1 - \frac{0,02 \times d}{30}\right)
\]

Onde:

- VA = Valor antecipável.
- VN = Valor nominal.
- d = Prazo em dias.

O cálculo corresponde à configuração do JSON fornecido.

---

## 8. Prompt 7 — Aplicação independente

**Objetivo:** simplificar a execução do sistema.

**Solicitação:**

> Modifique o projeto para que ele funcione localmente sem depender de Streamlit, pandas, Plotly ou Node.js.
>
> A aplicação deve possuir servidor próprio em Python, interface HTML integrada e banco SQLite.
>
> Crie um arquivo BAT que permita iniciar o sistema com dois cliques no Windows.

**Arquitetura proposta:**
- Servidor HTTP em Python.
- Interface HTML, CSS e JavaScript.
- Banco SQLite.
- Inicialização por arquivo BAT.
- Acesso pelo navegador em endereço local.

O Python continua sendo necessário no computador utilizado para executar a aplicação.

---

## 9. Prompt 8 — Testes de desempenho

**Objetivo:** avaliar o comportamento do sistema com grandes volumes de dados.

**Solicitação:**

> Realize testes com a base de aproximadamente 100 mil recebíveis e execute também um teste sintético com cerca de 10 milhões de registros.
>
> Avalie o armazenamento, o tempo das consultas e o comportamento da aplicação.
>
> Utilize paginação para evitar carregar todos os dados simultaneamente na interface.

**Base de referência:**
- 100.554 recebíveis.
- 3.041 cadastros de CNPJ.
- 85.215 aprovações esperadas.
- 15.339 recusas esperadas.

O teste sintético de 10 milhões de registros não substitui uma validação financeira completa desse volume.

---

## 10. Prompt 9 — Auditoria com Codex

**Objetivo:** verificar a integração do sistema.

**Solicitação:**

> Analise todos os arquivos do projeto Antecipe V4/V5 e identifique possíveis erros de execução, integração e processamento.
>
> Verifique a comunicação entre HTML, JavaScript, Python e SQLite.
>
> Teste a importação de CSV, JSON e ZIP, o armazenamento dos dados, a autenticação, as regras financeiras, os filtros e os gráficos.
>
> Corrija os problemas encontrados e apresente as modificações realizadas, os resultados efetivamente testados e as limitações restantes.

A solicitação também incluiu recomendações de segurança, desempenho, paginação e persistência de dados.

---

## 11. Prompt 10 — Correção do motor de validação na V5

**Objetivo:** resolver os problemas identificados na avaliação da versão anterior.

**Solicitação:**

> Crie a versão V5 a partir da avaliação funcional da plataforma.
>
> Corrija a execução dos validadores JSON, implemente o cálculo de antecipação com taxa de 2% ao mês e melhore a apresentação dos motivos de reprovação.
>
> Compare os resultados calculados com o gabarito de 100.554 recebíveis e investigue as divergências em relação às 85.215 aprovações esperadas.

### Avaliação que motivou a V5

| Funcionalidade | Situação anterior |
|---|---|
| Importação ZIP | Funcionando |
| Armazenamento de recebíveis | Funcionando |
| Importação de CNPJs | Funcionando |
| Consultas SQLite | Funcionando |
| Reconhecimento de JSON | Funcionando |
| Execução dos validadores | Não funcionando corretamente |
| Reprodução das aprovações esperadas | Não funcionando |
| Precificação de 2% | Não implementada |
| Motivos de recusa | Parcial |

A V5 foi desenvolvida para enfrentar essas limitações.

---

## 12. Prompt 11 — Documentação e instalação

**Objetivo:** permitir a utilização em outros computadores.

**Solicitação:**

> Desenvolva um README.md completo, explicando como baixar, instalar, configurar e executar o Antecipe V5 em outro computador Windows.
>
> Documente todas as dependências, os comandos de terminal, a instalação do Python, a execução pelo arquivo BAT e as formas de solucionar erros.
>
> A documentação deve ser compreensível para pessoas sem experiência em programação.

---

## 13. Evolução das versões

| Versão | Principal objetivo |
|---|---|
| V1 | Importação inicial e armazenamento SQLite |
| V2 | Reconhecimento automático e melhoria dos filtros |
| V3 | Login e modernização do menu lateral |
| V4 | Simplificação da execução e integração local |
| V4 JSON | Inclusão do motor de validação e comparação com o gabarito |
| V5 | Correção das regras, precificação e tratamento de pendências |

---

## 14. Limitações conhecidas

O uso de inteligência artificial auxiliou o desenvolvimento, mas não garante que todo o código produzido esteja correto.

Entre as limitações identificadas estão:

- Divergências entre as decisões calculadas e o gabarito oficial.
- Registros com informações cadastrais insuficientes.
- Necessidade de ampliar os testes de desempenho.
- Necessidade de auditoria adicional da segurança.
- Necessidade de validar integralmente a interpretação dos critérios de concentração.
- Necessidade de testar o programa em diferentes computadores Windows.

A reprodução integral das 85.215 aprovações esperadas ainda não foi comprovada.

Por isso, o Antecipe V5 deve ser tratado como um protótipo, e não como uma solução pronta para operações financeiras reais.

---

## 15. Responsabilidade e transparência

As ferramentas de inteligência artificial foram utilizadas como apoio técnico ao planejamento, desenvolvimento, revisão e documentação.

As sugestões e códigos gerados devem ser submetidos a testes e verificação humana.

As regras financeiras e os arquivos de referência foram fornecidos como requisitos do desafio.

Este documento registra a colaboração com IA e permite compreender as principais decisões tomadas durante o desenvolvimento.

---

## 16. Considerações finais

O projeto ANTECIPE V5 demonstra a aplicação de programação, banco de dados, automação e inteligência artificial para resolver um problema de análise de recebíveis financeiros.

A utilização do ChatGPT contribuiu para organizar os requisitos, propor arquiteturas, desenvolver funcionalidades, documentar procedimentos e identificar problemas.

O histórico apresentado também demonstra que o desenvolvimento de software é um processo iterativo, no qual resultados precisam ser testados, avaliados e corrigidos continuamente.

**Projeto:** ANTECIPE V5

**Finalidade:** Gestão, validação e análise de recebíveis financeiros.

**Tecnologias:** Python, HTML, CSS, JavaScript e SQLite.

**Ferramentas de apoio:** ChatGPT e Codex, da OpenAI.

**Data do registro:** 24 de outubro de 2026.
