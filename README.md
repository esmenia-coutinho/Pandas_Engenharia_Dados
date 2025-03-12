# Pandas_Engenharia_Dados
Aplicação da Arquitetura Medallion da Microsoft, utilizando unicamente biblioteca Pandas da linguagem Python no VSCode.

Neste projeto o objeto de negócio é analisar a operação de caixa de uma loja. 
Temos como fonte de dados dois arquivos do tipo csv salvos em diretório nomeado Landingzone, que representa camada Landingzone.
Os arquivos fonte são:
- Pandas_Fluxo_de_Caixa : contém informações da operação do fluxo de caixa, documento e forma de pagamento
- Pandas_Pessoas: contém informações do cliente relacionado a operação do fluxo de caixa.

Para garantir a atomicidade, consistência, isolamento e durabilidade dos dados.
Vamos adotar um padrão de design de dados lógico em camadas, conhecido como Arquitetura Medallion, que também pode ser chamada de arquitetura multi-hop.
Utilizando esta arquitetura podemos de forma incremental e progressiva melhorar a qualidade do dado, tornando mais adequado para aplicativos de business intelligence.

![Fluxograma](https://github.com/user-attachments/assets/736a16ae-a085-4bf2-b721-a458833409ce)

Sobre os termos usados no fluxo hands-on proposto acima:
- Os dados de origem estão salvos na camada Landingzone e a partir desta camada os dados irão fluir por cada camada da arquitetura (das tabelas de camadas Bronze ⇒ Prata ⇒ Ouro)
- A ingestão acontecerá com leitura e gravação dos dados na camada Bronze. Na camada bronze, os dados são considerados como brutos, pois nenhum tratamento ou validação foram realizados. O dado sai da camada Bronze em formato parquet. 
- Na camada Silver, os dados serão limpos, filtrados e validados. Além disso, já realizamos o particionamento da data da transação em Ano/Mês.
- Na camada Gold, o dado é enriquecido e finalizado para ser liberado para ser utilizado. Nesta camada aplicamos SCD1.


Ao progredir com a análise dos dados de origem, podemos desenhar o seguinte modelo conceitual a seguir:

![modelo_conceitual](https://github.com/user-attachments/assets/13b6de96-5bc9-453c-b2f4-9166234947d7)

Neste modelo identificamos uma tabela Fato de Transação relacionada a três tabelas de dimensões: Condição de Pagamento, Tipo de Documento e Pessoas.

Através do notebook "Pandas_Pipeline_Fluxo_de Caixa" programamos todo este processo desenhado acima e produzimos uma pipeline como saída. 
