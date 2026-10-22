# Padrões de tela

Estruturas base alinhadas aos blocos do Documento de especificação ADS. O padrão define a
organização; campos, regras e permissões vêm do contexto.

## Bloco comum — Cabeçalho

- Logotipo do Grupo Plaenge.
- Botão Home → página principal do portal de origem (ex.: portal CSC) — confirmar o portal no
  contexto; se ausente, [pendente].
- Ação contextual: Atualizar (consulta, mantém filtros) ou Voltar (cadastro, alerta de dados
  não salvos).

## Consulta

1. **Cabeçalho**
2. **Barra de títulos** — título da tela · botão Novo (abre cadastro em modo inclusão), se o
   perfil puder incluir.
3. **Filtros** — campos de filtro do contexto, cada um com tipo (inteiro, texto, lista, data com
   calendário) · Limpar filtros.
4. **Resultado** — lista de cartões com rolagem vertical (padrão do modelo) ou tabela quando houver
   muitas colunas comparáveis — escolha registrada no mapa de telas. Cartão: ID, título, data,
   status (badge), ação Editar/Visualizar.
5. **Estados** — vazio sem filtro ("nenhum registro"), vazio com filtro ("nenhum resultado para
   os filtros" + limpar), carregando (skeleton), erro (mensagem + tentar novamente).

Regra a verificar no contexto: quais registros cada perfil enxerga.

## Cadastro / edição

1. **Cabeçalho** com Voltar.
2. **Barra de títulos** — título · identificador do registro em modo edição (ID, título,
   responsável).
3. **Acompanhamento do status** — migalha com os status na ordem, destacando os já percorridos.
   Só se o contexto tiver lista de status.
4. **Grupos de formulário** expansíveis/recolhíveis, agrupando campos por assunto.
   Por campo: tipo, obrigatório, comportamento em inclusão e em edição, origem do dado.
5. **Rodapé de ações** — Salvar e ações de transição de status (Aprovar, Cancelar, Concluir…),
   cada uma visível conforme perfil e status atual. Ação de transição pede confirmação
   (AlertDialog) quando irreversível.
6. **Estados** — validação de obrigatórios (mensagem no campo), erro ao salvar, sucesso
   (toast), sem permissão (ação oculta ou desabilitada — escolha marcada [inferido] se o
   contexto não disser).

## Aprovação

Variante do cadastro em modo leitura para quem aprova: dados somente leitura, histórico de
transições, campo de justificativa (obrigatoriedade conforme regra) e ações Aprovar / Reprovar /
Devolver conforme o contexto.

## Dashboard

1. **Cabeçalho**
2. **Barra de títulos** com período/filtros globais.
3. **Indicadores** — um cartão por indicador citado no contexto, com fórmula ou [pendente].
4. **Gráficos e tabela de detalhe** — só os citados. Indicador sem definição de cálculo não é
   desenhado com número: mostra "[pendente] definição do indicador".

Se o dashboard for de outra área de TI (ex.: Data Science, Power BI), registre a dependência e
desenhe só o ponto de acesso.

## Detalhe / visualização

Igual ao cadastro em modo leitura, sem rodapé de edição. Use quando um perfil só consulta.
