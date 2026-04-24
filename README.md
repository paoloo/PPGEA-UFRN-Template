# Template LaTeX para Dissertação do PPgEA/UFRN

Template LaTeX para dissertação de mestrado do Programa de Pós-Graduação em Engenharia Aeroespacial da Universidade Federal do Rio Grande do Norte (PPgEA/UFRN), baseado em `abntex2` com cadeia bibliográfica migrada para `biblatex-abnt`.

## Estado atual

Este repositório foi revisado e ajustado para:

- remover páginas em branco extras entre elementos pré-textuais;
- compilar com `latexmk` sem warnings no `main_ppgea_ufrn.log`;
- usar `biblatex-abnt` + `biber` no lugar de `abntex2cite` + BibTeX;
- atualizar as referências normativas citadas no próprio modelo para versões mais recentes.
- manter o PDF principal na raiz do projeto e deixar arquivos auxiliares fora do versionamento via `.gitignore`.

## Normas ABNT cobertas

### Diretamente refletidas no template

- ABNT NBR 14724:2024
  Trabalhos acadêmicos - Apresentação.
- ABNT NBR 10520:2023
  Citações em documentos - Apresentação.
- ABNT NBR 6028:2021
  Resumo - Apresentação.
- ABNT NBR 6024:2012
  Numeração progressiva das seções de um documento.

### Referências bibliográficas

- O template usa `biblatex-abnt`.
- A cadeia bibliográfica foi modernizada em relação ao `abntex2cite`.
- Foi adicionada referência à ABNT NBR 6023:2025 em `referencias.bib`.

Importante:
O pacote `biblatex-abnt` disponível neste ambiente declara, em seu changelog, conformidade com a NBR 10520:2023 e testes para a NBR 6023:2018. Portanto, o template está em estado melhor e mais atual que a cadeia antiga do `abntex2cite`, mas isso não deve ser lido como uma garantia automática de conformidade integral com toda a NBR 6023:2025 sem revisão institucional específica.

## Validações realizadas

As seguintes validações foram feitas neste repositório:

- inspeção do fluxo pré-textual para identificar geração indevida de páginas em branco;
- correção da abertura de páginas com `openany` e neutralização de `\cleardoublepage` extra no fluxo do template;
- recompilação completa do projeto para confirmar a remoção das páginas vazias;
- limpeza dos avisos de compilação do template;
- criação de uma cópia local de `abntex2.cls` para eliminar avisos de compatibilidade da instalação padrão com `babel` e `memoir`;
- migração de `abntex2cite`/BibTeX para `biblatex-abnt`/Biber;
- normalização do arquivo `referencias.bib` para o formato aceito por `biber` (`month` numérico e `urldate` em ISO);
- simplificação da configuração do `latexmk` para compilar diretamente na raiz do projeto;
- compilação final com `latexmk -pdf -interaction=nonstopmode main_ppgea_ufrn.tex`.

## Arquivos principais

- [`main_ppgea_ufrn.tex`](./main_ppgea_ufrn.tex)
  Arquivo principal do documento.
- [`PPgEA.sty`](./PPgEA.sty)
  Customizações do template.
- [`abntex2.cls`](./abntex2.cls)
  Cópia local da classe, ajustada para este repositório.
- [`referencias.bib`](./referencias.bib)
  Base bibliográfica do projeto.

## Requisitos

Recomenda-se uma instalação TeX Live ou MacTeX recente contendo:

- `pdflatex`
- `latexmk`
- `biber`
- `biblatex`
- `biblatex-abnt`
- `makeindex`

## Como compilar

Compile a partir da raiz do projeto:

```bash
latexmk -pdf -interaction=nonstopmode main_ppgea_ufrn.tex
```

O projeto já inclui um arquivo `latexmkrc`, então os arquivos auxiliares e a saída de compilação são enviados automaticamente para:

```text
raiz do projeto
```

Para limpar arquivos auxiliares:

```bash
latexmk -C
```

## Saída gerada

O PDF principal é:

```text
main_ppgea_ufrn.pdf
```

Arquivos como `.aux`, `.bbl`, `.bcf`, `.run.xml`, `.log`, `.lof`, `.lot`, `.loq` e similares também são gerados na raiz e em subdiretórios do projeto, mas ficam cobertos pelo `.gitignore`.

## Observações importantes

- O repositório mantém exemplos de texto herdados do modelo canônico do `abntex2`. Eles servem como demonstração e devem ser substituídos pelo conteúdo real da dissertação.
- O template está tecnicamente pronto para uso, mas a conformidade final exigida em defesa e depósito institucional deve sempre ser conferida com as orientações atualizadas do PPgEA/UFRN e da biblioteca da UFRN.
- Se o programa adotar manual interno com exigências adicionais, essas regras institucionais podem prevalecer sobre o padrão ABNT genérico.
- O repositório inclui um `.gitignore` voltado para não versionar artefatos de compilação do LaTeX.

## Base técnica usada nesta revisão

- `abntex2` 1.9.7 como base estrutural da classe;
- `biblatex-abnt` como backend bibliográfico atual;
- `biber` como processador bibliográfico.

## Licença

Este repositório contém o arquivo [`LICENSE`](./LICENSE). Verifique também as licenças dos componentes externos utilizados, especialmente `abntex2` e `biblatex-abnt`.
