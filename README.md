# Teste Bioinformática 2023

## Teste técnico para bioinformatas

### Descrição

O teste será composto por duas etapas:

Na primeria etapa você deverá construir um pipeline de bioinformática usando alguma linguagem (shell script, r , python, etc) para detecção e anotação de variantes oriundos de dados brutos de NGS DNASeq.  Os dados são de uma amostra de controle humano de sexo feminino. Neste teste você deverá desenvolver o pipeline seguindo as seguintes etapas:

- Alinhamento das sequências de DNA (FASTQs)
- Chamada e detecção de variantes SNVs e INDELs
- Anotação de Variantes

Na segunda etapa você será responsável por identificar uma espécie de um microorganismo usando alguma(s) inferência filogenética. Neste teste você deverá desenvolver um algoritmo seguindos as seguintes etapas:

- Buscar nos bancos de dados arquivos fasta de espécies próximas
- Montar um arquivo multifasta
- Rodar a(s) inferência(s)

### Instruções etapa 1

- Realize o fork deste projeto para que crie um espelho em seu repositório (ex: https://github.com/UFPE-labbe/bioinfotest) github. Mais instruções de como fazer o fork [aqui](https://docs.github.com/pt/free-pro-team@latest/github/getting-started-with-github/fork-a-repo).
- Os dados brutos das amostras encontram-se no subdiretório `/data`. Elas estão em formato FASTQ.gz.
- Coloque todo o código realizado dentro da pasta `/code` e os resultados coloque numa pasta `/output` (Arquivos BAM, SAM, VCF, Arquivo de respostas).
- Há um questionário de perguntas dentro da pasta `/output` com nome `questões.md` , responda as perguntas dentro do arquivo, salve e commit dentro do seu repositório quando concluído. Estas respostas são obrigatórias e farão parte de sua avaliação técnica.
- Não vamos precisar executar o código aqui localmente do seu pipeline, mas vamos querer ver como você realizou todo o processo desde o alinhamento até a chamada de variantes, portanto fica claro que não serão aceitas soluções em plataformas on-line automatizadas de pipeline como Galaxy, etc. O seu código pode ser colocado em um ou mais arquivos, fica à seu critério de como organizar o código do pipeline.
- Iremos utilizar o genoma de referência da UCSC hg19.fasta para alinhamento e chamada de variantes, para auxiliar o processo deixamos o link aqui dos arquivos necessários para esta etapa.
- Para as etapas de processamento, nossa recomendação de ferramentas são:
  - BWA (http://bio-bwa.sourceforge.net/) para etapa de alinhamento
  - FreeBayes (https://github.com/freebayes/freebayes) para etapas de chamada de variantes. Será necessário enviar um parâmetro com o arquivo das regiões-alvo de interesse (``--target``) , para que ele não rode o algoritmo de detecção em todo o genoma humano. Recomendas que seja criado um arquivo `bed` ou `list`, afim de otimizar o processo.
  - snpeff para anotação funcional das variantes (https://pcingola.github.io/SnpEff/)
- Dica: para rodar todas essas ferramentas recomendamos o uso do Docker/Singularity ou a criação de um ambiente conda, caso opte por usar uma dessas alternativas o dockerfile ou comando usado para a criação do ambiente conda deverá ser upado como parte da resposta.

### Instruções etapa 2

- Adquirindo Dados do GenBank. Vamos usar recursos publicamente disponíveis para recuperar dados de sequência para comparação com dados de sequência que coletamos para os quais temos uma hipótese sobre sua origem (ou seja, gênero).
- A primeira coisa que vamos fazer é certificar-se de que sequenciamos o organismo correto, comparando-o às sequências que foram depositadas no GenBank, que é hospedado pelo *National Center for Biotechnology Information Search database* [NCBI](https://www.ncbi.nlm.nih.gov/).
- O GenBank® é o banco de dados de sequências genéticas do NIH, uma coleção anotada de todas as seqüências de DNA publicamente disponíveis. O GenBank faz parte da Colaboração Internacional de Banco de Dados de Sequência de Nucleotídeos, que compreende o DNA DataBank do Japão (DDBJ), o European Nucleotide Archive (ENA) e o GenBank no NCBI. Essas três organizações trocam dados diariamente. Mais informações [GenBank](https://www.ncbi.nlm.nih.gov/genbank/)
- Usando o BLAST para consultar o Genbank. Para pesquisar o banco de dados do GenBank, precisamos ter alguns meios de comparar nossas sequências com as sequências mais semelhantes.
- O que é o BLAST?. É um algoritmo para comparar sequências.
- A Ferramenta de Pesquisa de Alinhamento Local Básico [BLAST](https://blast.ncbi.nlm.nih.gov/Blast.cgi) localiza regiões de similaridade local entre sequências. O programa compara sequências de nucleotídeos ou proteínas a bancos de dados de sequências e calcula a significância estatística das correspondências. O BLAST pode ser usado para inferir relações funcionais e evolutivas entre sequências, bem como ajudar a identificar membros de famílias de genes.

### Resultados Esperados

#### Etapa 1

- Vamos precisar que sejam enviados os arquivos: `bam` file com os alinhamentos, o arquivo `bai` (arquivo de índice), o arquivo `vcf` (arquivo de variantes) e o arquivo anotado em formato `vcf`.
- O arquivo `questões.txt` dentro da pasta `output` preenchido com as respostas de cada quesito.
- O Arquivo ou comando usando para gerar o ambiente de execução dos scripts.
- Para facilitar ao terminar o seu teste, commit todo o seu projeto no seu respositório forkeado (bifurcado) e nos envie o link.

#### Etapa 2

- Vamos precisar que sejam enviados o arquivo `.tree` com a árvore.
- O arquivo multifasta alinhado.
- O modelo evolutivo calculado. 
- E a lista de softwares que você utilizou para chegar no resultado.
