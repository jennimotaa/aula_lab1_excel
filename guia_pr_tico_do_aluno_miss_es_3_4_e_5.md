# 📊 Laboratório Prático de Planilhas — Continuação (Missões 3, 4 e 5)

Bem-vindo(a) à continuação do nosso laboratório prático! Como encerramos nossa aula síncrona após a **Missão 2**, este guia foi preparado para você concluir as etapas restantes de forma autônoma, aplicando a mentalidade de um(a) Analista de Dados Júnior.

> **⚠️ Regra de Ouro:** O objetivo deste exercício é praticar a lógica e a construção das fórmulas. Os valores finais foram omitidos propositalmente para que você descubra os resultados na sua própria planilha.

---

## 📋 Ponto de Partida (Pré-requisitos)

Antes de começar, certifique-se de que sua planilha possui as duas primeiras abas concluídas conforme fizemos em aula:
1. **`Dados_Brutos`**: A aba original intacta.
2. **`1_Dados_Limpos`**: Com as 6 células vazias de *Unidades Vendidas* preenchidas com `45`, as duas datas impossíveis substituídas pelo texto `Data Inválida` e a coluna *Preço Unitário* formatada como moeda (`£ #,##0.00`).
3. **`2_Matematica_Estatistica`**: Contendo a coluna `F` (*Vendas Totais*) e os indicadores gerais nas colunas `G` até `M`.

---

## 🚀 Missão 3: Ordenação, Texto e Datas (Enriquecendo a Base)

Na vida real, os dados raramente vêm prontos para um relatório gerencial. Muitas vezes precisamos juntar informações para criar etiquetas, extrair códigos iniciais ou calcular prazos.

### Passo 3.1: Preparar o Ambiente de Trabalho (Boa Prática)
1. Clique com o botão direito na aba **`2_Matematica_Estatistica`** e selecione **Duplicar** (no Excel: *Mover ou Copiar > Criar uma cópia*).
2. Renomeie esta nova aba para: **`3_Ordenado_Texto_Datas`**.
3. **Limpeza visual:** Selecione as colunas **G até M** (os indicadores estatísticos gerais da missão anterior) e exclua essas colunas. Você deve manter apenas as colunas **A até F**:
   * `A`: Nome do Item
   * `B`: Categoria
   * `C`: Unidades Vendidas
   * `D`: Preço Unitário da Venda
   * `E`: Data da Venda
   * `F`: Vendas Totais

### Passo 3.2: Criar o Ranking de Vendas (Ordenação)
Queremos visualizar os produtos que geraram maior faturamento no topo da tabela.
1. Clique em **apenas uma célula** dentro da coluna **F** (*Vendas Totais*), por exemplo, a célula `F2`.
2. Acesse a guia **Dados** no menu superior e clique na opção de ordenar do **Maior para o Menor (`Z → A`)**.

> **🚨 Alerta de Segurança:** **Nunca** selecione apenas a coluna F antes de ordenar! Se você selecionar somente uma coluna, a planilha ordenará os valores isoladamente e misturará os preços e categorias dos outros produtos. Clicando em apenas uma célula, a ferramenta entende que deve mover a linha inteira junto.

* **Checkpoint Visual:** Verifique se o produto no topo da lista (linha 2) pertence à categoria *Eletrodomésticos* e possui 90 unidades vendidas, e se o último produto (linha 51) pertence à categoria *Móveis* com apenas 2 unidades vendidas.

### Passo 3.3: Criar Novas Colunas com Fórmulas de Texto e Data
Agora vamos enriquecer nossa tabela criando **4 novas colunas** (G, H, I e J). Digite os títulos na **Linha 1**, insira as fórmulas na **Linha 2** e depois arraste a alça de preenchimento (o quadradinho no canto inferior direito da célula) até a **Linha 51**.

| Coluna | Título (Linha 1) | Lógica / Objetivo | Fórmula (Português) | Fórmula (Inglês) |
| :--- | :--- | :--- | :--- | :--- |
| **G** | `Categoria - Item` | Juntar o texto da Categoria com o Nome do Item, separados por um traço com espaços (`" - "`). | `=CONCATENAR(B2; " - "; A2)` | `=CONCATENATE(B2; " - "; A2)` |
| **H** | `Prefixo` | Extrair apenas os **3 primeiros caracteres** do Nome do Item para isolar o código de catálogo. | `=ESQUERDA(A2; 3)` | `=LEFT(A2; 3)` |
| **I** | `Dias Desde a Venda` | Subtrair a Data da Venda da data atual do sistema para saber a idade daquela venda em dias. | `=HOJE()-E2` | `=TODAY()-E2` |
| **J** | `Mês-Ano` | Converter a data completa em um rótulo textual contendo o nome do mês por extenso e o ano. | `=TEXTO(E2; "MMMM-AAAA")` | `=TEXT(E2; "MMMM-YYYY")` |

#### 💡 Dicas e "Pegadinhas" desta etapa:
* **Separador de argumentos:** Dependendo da configuração do seu computador ou Google Sheets, a fórmula pode exigir ponto e vírgula (`;`) ou vírgula (`,`). Observe a dica flutuante que aparece enquanto você digita.
* **Erro na Coluna I (Formatação):** Se ao digitar `=HOJE()-E2` aparecer uma data estranha (como `15/03/1902`), não se assuste! O programa aplicou formato de data automaticamente. Basta selecionar toda a coluna **I** e mudar o formato para **Número** (sem casas decimais).
* **Erro `#VALOR!` na Coluna I:** Nas duas linhas onde temos o texto `"Data Inválida"`, a fórmula retornará `#VALOR!`. Isso é perfeitamente normal e esperado, pois não é possível fazer cálculos matemáticos subtraindo texto de uma data.

---

## 🔍 Missão 4: Filtros Estratégicos (Isolando Insights)

Um(a) analista de dados não analisa dezenas ou milhares de linhas de uma só vez para responder a uma pergunta específica de negócio. Usamos **Filtros** para ocultar temporariamente o que não interessa e focar apenas no grupo investigado.

### Filtro 1: Produtos Campeões de Volume (`Unidades Vendidas > 50`)
1. Volte para a sua aba **`1_Dados_Limpos`** (ou use a aba `3_Ordenado_Texto_Datas` antes de aplicar qualquer filtro) e **duplique-a**.
   *(Nota: Se duplicar a `1_Dados_Limpos`, lembre-se de garantir que a coluna F de Vendas Totais esteja calculada).*
2. Renomeie esta nova aba para: **`4_Filtro_Mais_de_50`**.
3. Clique na célula `A1` e ative a ferramenta de filtro: vá em **Dados > Criar um filtro** (ou **Filtrar**). Pequenas setas aparecerão ao lado de cada título na Linha 1.
4. Clique no ícone de filtro (setinha) da coluna **C (`Unidades Vendidas`)**:
   * **No Google Sheets:** Vá em *Filtrar por condição* → escolha **É maior que** → digite `50` → clique em **OK**.
   * **No Excel:** Vá em *Filtros de Número* → escolha **É maior que...** → digite `50` → clique em **OK**.
5. **Reflexão:** Observe quantos produtos permaneceram visíveis. Note que produtos que venderam *exatamente* 50 unidades ficam de fora, pois a regra exige um valor estritamente maior que 50.

### Filtro 2: Análise de Categoria Específica (`Eletrônicos`)
1. Duplique novamente uma aba limpa (sem filtros ativos e com as colunas A até F) e renomeie para: **`5_Filtro_Eletronicos`**.
2. Ative os filtros na Linha 1 (**Dados > Filtrar**).
3. Clique na setinha da coluna **B (`Categoria`)**.
4. Clique em **Limpar** (para desmarcar todas as categorias de uma vez), selecione apenas a caixa **`Eletrônicos`** e clique em **OK**.
5. **Truque de Analista (Barra de Status):** Com a aba filtrada, selecione com o mouse apenas os números visíveis da coluna **C (`Unidades Vendidas`)** e olhe para o canto inferior direito da janela do programa. A barra de status exibe automaticamente a **Soma** e a **Contagem** dos itens selecionados sem você precisar escrever nenhuma fórmula!

---

## 📈 Missão 5: Resumo Executivo por Categoria (Consolidando Dados)

Para encerrar, a diretoria precisa de uma visão resumida do desempenho de cada uma das 4 categorias da loja (`Eletrodomésticos`, `Eletrônicos`, `Móveis` e `Ferramentas`).

1. Crie uma nova aba em branco (clicando no botão `+` no canto inferior esquerdo) e renomeie para: **`6_Resumo_por_Categoria`**.
2. Monte uma pequena tabela estruturada a partir da célula `A1` com os seguintes cabeçalhos:
   * `A1`: **Categoria**
   * `B1`: **Total de Unidades Vendidas**
   * `C1`: **Faturamento Total (£)**
3. Na coluna **A** (`A2` até `A5`), digite exatamente os nomes das 4 categorias:
   * `A2`: `Eletrodomésticos`
   * `A3`: `Eletrônicos`
   * `A4`: `Móveis`
   * `A5`: `Ferramentas`
4. Agora, utilize a função condicional **`SOMASE`** (em inglês: **`SUMIF`**) para buscar os valores lá da sua aba limpa (ex: `3_Ordenado_Texto_Datas`) e somar apenas o que pertence a cada categoria:
   * **Lógica da função:** `=SOMASE(intervalo_onde_estão_as_categorias; critério_da_categoria; intervalo_que_será_somado)`
   * **Na célula `B2` (Unidades):** Aponte o primeiro intervalo para a coluna B da sua aba base (`$B$2:$B$51`), o critério para `A2`, e o intervalo de soma para a coluna C (`$C$2:$C$51`).
   * **Na célula `C2` (Faturamento):** Use a mesma lógica, alterando apenas o último intervalo para a coluna F (`$F$2:$F$51`).
5. Arraste as fórmulas até a linha 5 e adicione uma linha `A6` chamada **Total Geral** usando a função `=SOMA(...)` para conferir se o valor bate exatamente com a Receita Total que você encontrou na Missão 2!

---

## ✅ Checklist de Entrega

Antes de enviar sua planilha, confira se o arquivo final contém **todas as 7 abas** organizadas nesta ordem:
- [ ] `Dados_Brutos` (intacta)
- [ ] `1_Dados_Limpos`
- [ ] `2_Matematica_Estatistica`
- [ ] `3_Ordenado_Texto_Datas` (com as 4 novas colunas G, H, I e J preenchidas)
- [ ] `4_Filtro_Mais_de_50` (com o filtro ativo exibindo apenas > 50 unidades)
- [ ] `5_Filtro_Eletronicos` (com o filtro ativo exibindo apenas Eletrônicos)
- [ ] `6_Resumo_por_Categoria` (com a tabela consolidada usando `SOMASE` e formatada como moeda)

Bom trabalho, Analista! Qualquer dúvida durante o processo, revise a lógica de cada fórmula ou chame no canal da turma.