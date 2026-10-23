# Pacote de entrada por agente

Cada agente recebe só o necessário. Contexto a mais faz o agente puxar informação da etapa
errada (ex.: requisitos lidos da TAP bruta em vez do contexto validado).

| Agente | Documentos brutos (TAP, anexos) | Transcrição | 01-contexto | 01-roteiro | 02-ata | Protótipo + 03-mapa-telas | design-system.md | 04-requisitos | Modelo ADS |
|--------|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| 1 Entendimento da TAP | ● | | | | | | | | |
| 2 Reunião | ○ | ● | ● | ● | | | | | |
| 3 Protótipo | | | ● | | ● | | ○ | | ○ |
| 4 Requisitos | ○ | | ● | | ● | ● | | | ○ |
| 5 Documentação | | | ● | | ● | ● | ● | ● | ● |

● obrigatório · ○ consulta (para citar origem primária ou seguir a estrutura do modelo)

Na etapa 1, os documentos brutos são passados pelo caminho original; o agente os copia para
`fluxo/<projeto>/fontes/`. A partir da etapa 2, passe os caminhos dentro de `fontes/`. O
`01-benchmark.md` acompanha o `01-contexto` sempre que este for obrigatório para o agente.

## Prompt-padrão para o subagente

```
Modo subagente.
Projeto: <nome> | Pasta: fluxo/<projeto>/
Etapa: <n — nome> | Gerar versão: <x.y> (<primeira emissão | reemissão>)
Entradas:
- <caminho> — <o que é>
Saída esperada: <caminho(s)>
Respostas desde a última versão (só em reemissão):
- Q-003: <resposta, quem respondeu, data>
Suposições autorizadas pelo usuário:
- <suposição>
Termine com o bloco de status das convenções.
```
