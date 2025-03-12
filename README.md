# Pandas_Engenharia_Dados
Aplicação da Arquitetura Medallion da Microsoft, utilizando unicamente biblioteca Pandas da linguagem Python no VSCode.

Neste projeto, existem um notebook com código explorando a biblioteca Pandas da linguagem Python.

No notebook "Pandas_Pipeline_Fluxo_de Caixa" abordamos um negocio de Fluxo de Caixa e produzimos uma pipeline como saída. Neste processo, configuramos e organizamos os diretórios necessários para usar as camadas: Bronze, Silver e Gold. Aplicamos SCD1 na camada Gold. Produzimos arquivo com formato parquet, particionados por Mês/Ano.

Os arquivos usados como fonte de dados de origem são: 
Pandas_Fluxo_de_Caixa 
Pandas_Pessoas
