# ANTECIPE V5
## Manual completo de instalação e execução no Windows

O **Antecipe V5** é uma plataforma web local para gerenciamento, validação e análise de recebíveis financeiros.

Este documento explica como instalar e executar o programa em um computador novo, incluindo todos os programas necessários, comandos para o terminal, configuração inicial, utilização e solução de erros comuns.

**Leia este manual antes de executar o sistema pela primeira vez.**

---

# 1. O que é necessário instalar?

Para utilizar o Antecipe V5 em outro computador Windows, é necessário instalar apenas o **Python 3**.

| Programa | Obrigatório? | Finalidade |
|---|---|---|
| Python 3 | Sim | Executar o servidor |
| Navegador atualizado | Sim | Acessar a interface |
| Visual Studio Code | Não | Facilitar a execução e visualizar o código |
| SQLite | Não | Já acompanha o Python |
| Git | Não | Opcional para baixar o projeto pelo GitHub |
| Node.js | Não | Não utilizado |
| Streamlit | Não | Não utilizado |
| pandas | Não | Não utilizado |
| Plotly | Não | Não utilizado |
| Microsoft Visual Studio | Não | Não necessário |

O programa utiliza apenas bibliotecas da instalação padrão do Python.

Portanto, **não é necessário executar `pip install` nem instalar pacotes por meio de `requirements.txt`.**

## 1.1 Requisitos recomendados

- Windows 10 ou Windows 11.
- Python 3.13.
- Google Chrome, Microsoft Edge ou Firefox.
- Conexão com a internet para baixar os arquivos e instalar o Python.
- Espaço disponível em disco para armazenar o banco de dados e os recebíveis.

O processamento de arquivos muito grandes pode exigir mais memória e espaço em disco. O desempenho depende das especificações do computador.

---

# 2. Instalação completa do Python

O Python é responsável por executar o servidor do Antecipe.

## Passo 1 — Baixar o Python

Acesse o site oficial:

https://www.python.org/downloads/windows/

Baixe uma versão compatível do Python 3. Recomenda-se utilizar o Python 3.13 para este projeto.

## Passo 2 — Instalar

Abra o instalador baixado.

Se a opção **Add Python to PATH** aparecer, marque-a antes de continuar.

Conclua a instalação seguindo as instruções apresentadas na tela.

Caso esteja utilizando o Python Install Manager, instale o Python 3.13 pelo comando:

```powershell
py install 3.13
```

## Passo 3 — Reiniciar o terminal

Após a instalação:

1. Feche todos os terminais abertos.
2. Feche o VS Code, caso esteja aberto.
3. Abra novamente o terminal.

Se o instalador solicitar uma reinicialização do computador, realize-a.

## Passo 4 — Verificar a instalação

Abra o PowerShell do Windows.

Execute:

```powershell
python --version
```

O resultado esperado será semelhante a:

```text
Python 3.13.x
```

Se o comando anterior não funcionar, tente:

```powershell
py --version
```

Também é possível verificar todas as versões reconhecidas pelo Python Install Manager:

```powershell
py list
```

Se uma versão do Python for apresentada, a instalação foi reconhecida.

### Se o Python não for encontrado

Se aparecer:

```text
python : O termo 'python' não é reconhecido
```

Verifique se o Python foi instalado corretamente e se está disponível no PATH.

Feche e reabra o terminal após corrigir a instalação.

**Não prossiga até conseguir executar o Python pelo terminal.**

---

# 3. Baixar o Antecipe V5

Existem duas opções.

## Opção A — Baixar diretamente do GitHub

1. Acesse o repositório do
