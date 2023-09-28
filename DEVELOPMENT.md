# Guia de Desenvolvimento

Este documento descreve práticas e diretrizes de desenvolvimento.
Por favor, reserve um momento para se familiarizar com este guia antes de se aprofundar no código.

## Princípios Orientadores

1. **Preferência por Módulos Integrados**: Priorizamos o uso das bibliotecas integradas sempre que possível. Isso minimiza dependências externas e aproveita a robustez da biblioteca padrão da linguagem.

1. **Retornos Antecipados**: Em vez de código profundamente aninhado, prefira usar retornos antecipados. Isso torna o código mais legível e reduz a carga cognitiva para entender fluxos de controle.

1. **Programação Orientada à Performance**: Escrevemos códigos que não são apenas funcionais, mas também eficientes. Mantenha a performance em mente ao implementar novos recursos ou refatorar os existentes.

## Começando

### Configurando o Ambiente de Desenvolvimento

#### OSX : Preparação inicial

[Homebrew](https://github.com/Homebrew/install)

#### Windows : Preparação inicial

Seguir as dicas de Fabio Akita:

[![Watch the video](https://img.youtube.com/vi/sjrW74Hx5Po/maxresdefault.jpg)](https://youtu.be/sjrW74Hx5Po)

## Estrutura dos projetos

Tantos os projetos Python quanto os projetos GO usarão um conjunto de padrões de layout de projetos baseados nos [padrões GO](https://github.com/golang-standards/project-layout/blob/master/README_ptBR.md) e são explicado pelo Fullcircle no vídeo:
[![Watch the video](https://img.youtube.com/vi/OFud4iPuAH8/maxresdefault.jpg)](https://youtu.be/OFud4iPuAH8)


# Projetos Python

**Formatação de Código com Black**: Nosso código adere aos padrões de formatação do [Black](https://github.com/psf/black). Antes de enviar qualquer código, certifique-se de executar o Black para garantir a consistência.

## Dependências

1. python e pacotes basicos

Instale python, pip e pipx

2. [Python Venv](https://github.com/pyenv/pyenv)

   ...
   pyvenv install 3.11.4
   pyvenv global 3.11.4

3. Clonar o repositório

4. Criar o ambiente virtual:

   ```bash
   python -m venv .venv
   ```

5. Ativar o ambiente virtual:

Com scripts no terminal :

    - No Windows: `.venv\Scripts\activate`
    - No macOS e Linux: `source .venv/bin/activate`

O vscode tem configuração para carregar automaticamente o ambiente

Se o for Fish Shell Terminal:

    source .venv/bin/activate.fish

1. Instale os pacotes do projeto

   - pip install --upgrade pip
   - pip install -r requirements.txt

o arquivo requirements_test.txt é usado para o ambiente testEnv

### Formatando o Código

Use o Black para atender aos nossos padrões de formatação:

Instalação

    pipx install black

Uso:

    black .

O VSCODE pode ser configurado para para formatação automatica com a extensão [ms-python.black-formatter](https://marketplace.visualstudio.com/items?itemName=ms-python.black-formatter)

- [iSort](https://pycqa.github.io/isort/docs/configuration/black_compatibility.html)

## Melhores Práticas

### Retornos Antecipados

Em vez de:

```python
def alguma_funcao(args):
    if condicao:
        # Algum código aqui
    else:
        return
```

Prefira:

```python
def alguma_funcao(args):
    if not condicao:
        return
    # Algum código aqui
```

### Programação Orientada à Performance

- Use tipos e estruturas de dados integrados de forma eficaz. Por exemplo, ao verificar associações, conjuntos (sets) são mais rápidos do que listas.
- Use variáveis locais em vez das globais sempre que possível, já que a busca por variáveis locais é mais rápida.
- Use compreensões de lista e expressões geradoras para loops concisos e eficientes.

# Testes unitários

Criar o ambiente

    python -m venv .testEnv

Configurar

    source .testEnv/bin/activate.fish
    pip install -r requirements.txt
    pip install -r test_requirements.txt

Rodar

    pytest --capture=tee-sys;

# Linters

    pylint


# Projetos GO

TBD
