# Limpeza e tratamento de dados meteorológicos (fvm_clima_tempo)

Descrição
---------
Repositório de exemplo para limpeza e tratamento de um pequeno conjunto de dados meteorológicos referentes a dias de jogos esportivos. Inclui um Jupyter Notebook (fvm_clima_tempo.ipynb) que explora, visualiza e sugere tratamentos para dados inconsistentes, ausentes e outliers.

Conteúdo do repositório
-----------------------
- `fvm_clima_tempo.ipynb` — Notebook Jupyter com análise exploratória, visualizações e procedimentos de limpeza/inspeção.
- `tempo.csv` — Conjunto de dados em CSV usado pelo notebook (formatado com `;` como separador).
- `requirements.txt` — Lista de dependências (atenção: o arquivo atualmente contém caracteres inválidos/encodificação estranha; veja seção de setup).
- `.gitignore` — Arquivos/dirs ignorados pelo Git (venv, __pycache__, .pyc).

Resumo do dataset (`tempo.csv`)
-------------------------------
Colunas:
- Aparencia — aparência do céu (valores esperados: `sol`, `nublado`, `chuva`, etc.).
- Temperatura — temperatura em °F.
- Umidade — umidade relativa em %.
- Vento — presença de vento (`VERDADEIRO` / `FALSO`).
- Jogar — decisão (sim/nao).

Problemas observados (detectados no notebook)
- Valores ausentes:
  - Umidade: 1 valor ausente
  - Vento: 1 valor ausente (célula vazia)
- Valores inválidos / inconsistentes:
  - Em `Aparencia` existe o valor `"menos"` (provável erro de digitação).
  - Em `Vento` os valores são strings em português (`VERDADEIRO`, `FALSO`) — convém converter para boolean.
  - Em `Jogar` valores `sim`/`nao` — convém mapear para boolean ou 1/0.
- Outliers numéricos:
  - `Temperatura` contém `1220` — muito acima do razoável (provável erro de entrada).
  - `Umidade` contém `200` — acima de 100% (provável erro).

Instalação e execução
---------------------
Recomenda-se Python 3.8+ e um ambiente virtual.

1. Criar e ativar venv:
   - Linux/macOS:
     ```bash
     python3 -m venv .venv
     source .venv/bin/activate
     ```
   - Windows (PowerShell):
     ```powershell
     python -m venv .venv
     .\.venv\Scripts\Activate.ps1
     ```

2. Corrigir / instalar dependências:
   - Atenção: se `requirements.txt` apresentar erro de codificação, abra o arquivo e salve com codificação UTF-8 sem bytes nulos/BOM.
   - Dependências relevantes encontradas no repositório (versões propostas):
     - pandas==2.3.3
     - seaborn==0.13.2
     - voila==0.5.11
   - Instalar:
     ```bash
     pip install pandas==2.3.3 seaborn==0.13.2 voila==0.5.11
     # ou, após corrigir requirements.txt
     pip install -r requirements.txt
     ```

3. Executar o notebook:
   ```bash
   jupyter notebook fvm_clima_tempo.ipynb
   # ou utilze o voila
   voila fvm_clima_tempo.ipynb
   ```
   Ou usar JupyterLab / Google Colab (suba o notebook e o CSV).

Contribuição
------------
Pull requests são bem-vindos. Para contribuições:
1. Abra uma branch com mudanças.
2. Corrija o `requirements.txt` se necessário (salve em UTF-8).
3. Inclua testes simples ou explique a lógica de limpeza aplicada.

Contato
-------
Criador do repositório: cllmenate (GitHub)

Licença
-------
MIT License.
