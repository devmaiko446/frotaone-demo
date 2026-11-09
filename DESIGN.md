# FrotaOne — Sistema visual MV Transportes

## Visão
Produto operacional de gestão de frota; a interface comunica precisão logística, com base escura, superfícies prateadas, hierarquia financeira clara e detalhes das cores do logotipo MV.

## Fonte única e implantação
- Arquivo de tema público: `mv-theme.css`. Carregar sempre por último, depois da folha de estilos gerada pelo aplicativo.
- Página publicada: `index.html` em GitHub Pages (`/frotaone-demo/`). Não modificar caminho/domínio ao atualizar assets.
- Projeto-fonte Lovable: `public/mv-theme.css`. Sincronizar a mesma versão quando o editor estiver disponível; evitar deriva entre projeto-fonte e GitHub Pages.
- O logo `frotaone-logo.webp` já tem transparência; não adicionar cartões brancos, filtros, recortes ou novo fundo à imagem.

## Design tokens de referência
| Papel | Token | Cor |
|---|---|---|
| Base Jet Black | `--mv-black` | `#101015` |
| Dourado ação | `--mv-gold` | `#FFD21A` |
| Amarelo da marca | `--mv-gold-edge` | `#FFCF00` |
| Roxo navegação | `--mv-purple` | `#6D2494` |
| Roxo escuro | `--mv-purple-deep` | `#510078` |
| Prata/cromo | `--mv-silver` | `#DEE0E8` |
| Superfície de trabalho | `--mv-canvas` | `#F2F3F6` |
| Painel | `--mv-panel` | `#FFFFFF` |
| Texto | `--mv-ink` | `#1C1B21` |
| Texto secundário | `--mv-muted` | `#656A75` |
| Borda | `--mv-border` | `#DDE0E7` |

## Regras de UI
1. Navegação escura: roxo sinaliza item selecionado; dourado na marca de localização e ações prioritárias.
2. Cabeçalho do logotipo: faixa completa prata/gradiente cromado; logo transparente sem cartão individual.
3. Painéis e KPIs: superfícies claras, bordas sutis, números tabulares e informações financeiras sempre legíveis.
4. Status de negócio permanecem semânticos: sucesso verde, atenção âmbar, erro/atraso vermelho, informação azul. Não substituir por roxo/dourado.
5. Botão primário dourado com texto Jet Black. Controles secundários claros; foco visível.
6. A experiência precisa funcionar em 320px, desktop e navegação por teclado; reduzir animações quando `prefers-reduced-motion` está ativo.
7. Não modificar operações, permissões, dados, cálculos, API ou alertas financeiros por razões estéticas.

## Observação de publicação
A demonstração GitHub Pages tem HTML/CSS/JS compilados. Alterações de layout implementadas somente no código-fonte Lovable não serão refletidas automaticamente na página da demonstração; sincronizar CSS/compilados antes de considerar as duas versões equivalentes.

## Integridade do módulo de Pneus (09/11/2026)
O entrypoint do JavaScript compilado deve carregar **sem query string**. O chunk dinâmico de Pneus/Truck3DScene reimporta o mesmo entrypoint por caminho relativo e precisa compartilhar a mesma instância React. Colocar `?v=...` apenas no `<script type="module">` causa duas instâncias de React e erro de hook #321, deixando o painel em branco. Para versionar a aplicação, publique arquivos com nome hash diferente e atualize o `src`/HTML, sem query string. Simulação com proxy local (HTML de produção sem query) exibiu o mapa 3D e 10 posições, sem exceções de console.
