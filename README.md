# Whole Genome Sequencing

### WGS Analysis Process
[中文版](https://github.com/flowhub-team/WholeGenomeSequencing/blob/main/README_cn.md)
1. Experimental Preparation:
   Prior to initiating the analysis, it is necessary to prepare the samples and relevant experimental materials. The samples can be DNA extracts typically obtained from blood, tissue, or cells. Experimental preparation includes quality control checks, DNA library construction, and preparation of sequencing chips.

2. DNA Library Construction:
   Converting DNA fragments from the sample into libraries suitable for sequencing. This typically involves the following steps:
   a. DNA Fragmentation: Cutting long DNA fragments into shorter fragments, usually ranging from a few hundred to a few thousand base pairs.
   b. End Repair: Repairing the ends of DNA fragments to make them compatible for adapter ligation.
   c. Adapter Ligation: Ligating sequencing adapters to the ends of DNA fragments. Adapters contain sequences compatible with the sequencing instrument.
   d. PCR Amplification: Amplifying the adapter-ligated DNA fragments through polymerase chain reaction (PCR) to generate sufficient signals during sequencing.

3. Sequencing:
   Placing the DNA libraries into a sequencing instrument for the purpose of sequencing. There are several different sequencing technologies available, such as Illumina, Ion Torrent, PacBio, and Oxford Nanopore, among others. These technologies employ different principles and methods to read DNA sequences.

4. Data Preprocessing:
   The raw sequencing data generated from the sequencing instrument is referred to as "reads." Before further analysis, it is necessary to preprocess and perform quality control on these data to remove low-quality reads and adapter sequences.
    1. Trimmomatic: Used to remove adapter sequences, low-quality bases, and low-quality reads from sequencing reads. You can find more information and usage instructions on the [Trimmomatic GitHub](https://github.com/timflutre/trimmomatic).

    2. FastQC: Used to assess the quality distribution and other quality metrics of sequencing reads. It helps detect potential issues during the sequencing process, such as decreasing sequencing quality and adapter contamination. For more information, please visit the  [FastQC website](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/).

    3. BWA-MEM: Used to align sequencing reads to a reference genome. BWA-MEM employs a fast seed-and-extend algorithm that efficiently handles longer reads. Detailed documentation and usage instructions can be found on the [BWA-MEM GitHub](https://github.com/lh3/bwa).

    4. Bowtie2: Used to align reads to a reference genome. It combines a fast seed-and-extend algorithm with a maximum-likelihood alignment algorithm, suitable for aligning short sequences. More information can be found on the [Bowtie2 website](http://bowtie-bio.sourceforge.net/bowtie2/index.shtml).

    5. SAMtools: A toolkit for processing alignment results, which can perform operations such as conversion, sorting, indexing, and filtering of SAM/BAM format files. Additionally, it provides a set of command-line tools for statistics on alignment information, SNP/Indel detection, and more. More documentation and download links can be found on the [SAMtools website](http://www.htslib.org/).

    6. GATK (Genome Analysis Toolkit): A toolkit for analyzing and detecting variants in genomic data. It offers various algorithms and tools, including genome re-alignment, SNP/Indel detection, and variant filtering. For detailed information, please visit the [GATK website](https://gatk.broadinstitute.org/hc/en-us).

    7. Picard Tools: A toolkit for processing SAM/BAM files, which can mark PCR duplicates, calculate coverage, create statistical reports, and more. Additional information and usage instructions can be found on the [Picard Tools website](https://broadinstitute.github.io/picard/).

    8. QualiMap: A tool used to assess the quality of sequencing data. It detects quality metrics such as coverage, GC content, error rates of sequencing reads, and generates corresponding statistical charts and reports. For more information, please visit the  [QualiMap website](https://gatk.broadinstitute.org/hc/en-us).
5. Data Alignment and Genome Assembly:
   Aligning or assembling the preprocessed reads with a reference genome is performed. Alignment involves comparing reads to known genomic sequences to determine their positions in the genome. Genome assembly involves combining reads to generate longer contiguous sequences, reconstructing the overall structure of the genome.
    1. Alignment Tools:
        1. BWA-MEM: Used to align sequencing reads to a reference genome. It employs a fast seed-and-extend algorithm and is suitable for handling longer reads. Detailed documentation and usage instructions can be found on the[BWA-MEM GitHub](https://github.com/lh3/bwa).
        2. Bowtie2: Used to align reads to a reference genome. It combines a fast seed-and-extend algorithm with a maximum-likelihood alignment algorithm and is suitable for aligning short sequences. For more information, please visit the[Bowtie2 website](https://www.ebi.ac.uk/~zerbino/velvet/).
    2. Genome Assembly Tools:
        1. SPAdes: Used for genome assembly from sequencing reads, including single-cell sequencing data. It combines de Bruijn graph algorithm with various optimization strategies and is suitable for various types of sequencing data. More information and usage instructions can be found on the [SPAdes GitHub](https://github.com/ablab/spades).
        2. Velvet: A de Bruijn graph-based genome assembly tool suitable for short sequencing data. It reconstructs genome sequences by building k-mer graphs. For detailed information, please visit the [Velvet website](https://www.ebi.ac.uk/~zerbino/velvet/).
        3. SOAPdenovo: A fast and efficient tool for genome assembly. It is based on the de Bruijn graph algorithm and is suitable for large-scale genome assembly. For more information, please visit the [SOAPdenovo website](http://soap.genomics.org.cn/soapdenovo.html).
6. Mutation Detection:
   Mutation detection involves identifying and analyzing genomic variations in the sample using the results from alignment or genome assembly. These variations may include single nucleotide polymorphisms (SNPs), insertions/deletions (indels), gene rearrangements, etc. The methods and tools for mutation detection may vary depending on the research purpose.
    1. GATK (Genome Analysis Toolkit): GATK is a widely used toolset for genomic data analysis and mutation detection. It provides various algorithms and tools, including genome re-alignment, SNP/indel detection, variant filtering, etc. For more information, please visit the [GATK website](https://gatk.broadinstitute.org/).
    2. VarScan: VarScan is a tool for detecting SNPs, indels, and structural variations, particularly suitable for comparative analysis. It can identify variations from alignment data and provides statistical filtering and annotation. For detailed information, please visit the [VarScan website](http://varscan.sourceforge.net/).
    3. FreeBayes: FreeBayes is an open-source tool for SNP and indel detection from sequencing data. It employs Bayesian statistical methods for variant calling and offers high sensitivity and accuracy. For more information, please visit the [FreeBayes GitHub](https://github.com/ekg/freebayes).
    4. MuTect: MuTect is a tool specifically designed for detecting mutations in tumor samples. It analyzes tumor-normal paired data and identifies mutations in the tumor sample. For more information, please visit the [MuTect website](https://software.broadinstitute.org/cancer/cga/mutect).
    5. Samtools: Samtools is a toolkit for handling alignment data (SAM/BAM format) and also provides some mutation detection functionalities. It can perform SNP/indel detection, filtering, annotation, etc. For detailed information, please visit the [Samtools website](http://www.htslib.org/).
    6. Platypus: Platypus is a flexible mutation detection tool capable of detecting SNPs, indels, and structural variations from WGS data. It offers high configurability and supports multi-sample analysis. For more information, please visit the [Platypus GitHub](https://github.com/andyrimmer/Platypus).
7. 注释和功能分析：
   对检测到的变异进行注释，确定其可能的功能和影响。注释可以包括变异在基因区域的位置、氨基酸改变的影响、潜在的功能通路等。
    1. ANNOVAR：ANNOVAR是一个用于注释基因组变异的工具，可以根据各种数据库提供详细的注释信息。它支持多种变异类型的注释，包括SNP、Indel、结构变异等。了解更多信息，请访问[ANNOVAR官方网站](https://annovar.openbioinformatics.org/en/latest/)。
    2. Variant Effect Predictor (VEP)：VEP是一个广泛使用的工具，用于注释和预测变异的功能影响。它能够提供详细的注释信息，包括变异的基因影响、功能改变、突变致病性预测等。了解更多信息，请访问[VEP官方网站](https://www.ensembl.org/info/docs/tools/vep/index.html)。
    3. SnpEff：SnpEff是一个用于注释和预测SNP和结构变异的功能影响的工具。它能够提供变异的注释、基因影响、功能改变以及通路分析等。有关详细信息，请访问[SnpEff官方网站](http://snpeff.sourceforge.net/)。
    4. dbNSFP：dbNSFP是一个基因组功能预测数据库，提供了大量的注释和预测信息。它包含了来自多个公共数据库的功能预测结果，并提供了丰富的注释信息，如SIFT、PolyPhen-2、GERP++等。有关详细信息，请访问[dbNSFP官方网站](https://sites.google.com/site/jpopgen/dbNSFP)。
    5. DAVID：DAVID（Database for Annotation, Visualization, and Integrated Discovery）是一个功能注释和富集分析工具，可以帮助用户理解基因组变异的功能和相关的生物学过程。它整合了多个公共数据库，提供了注释、功能分析和通路分析等功能。了解更多信息，请访问[DAVID官方网站](https://david.ncifcrf.gov/)。

8. 结果解读和报告：
   根据分析的结果，对基因组测序数据进行解读，并形成报告。报告可能涵盖样本的遗传风险、潜在的致病变异、药物敏感性等信息。

### 标准WGS生物信息分析流程
![流程图](https://github.com/flowhub-team/WholeGenomeSequencing/blob/main/asset/WholeGenomeSequencingFlow.png)

### WGS标准流程在线分析地址
[WholeGenomeSequencingFlow](https://www.flowhub.com.cn/repo/flowhub_team/WholeGenomeSequencingFlow)

[https://www.flowhub.com.cn/repo/flowhub_team/WholeGenomeSequencingFlo](https://www.flowhub.com.cn/repo/flowhub_team/WholeGenomeSequencingFlow)

### WGS标准流程使用教程


### Fowhub平台介绍

FlowHub 是一种创新的工作流云平台，为用户提供了全面而强大的功能。它不仅是一个可靠的数据管理平台，还是一个灵活的工具开发平台，一个高效的流程构建平台，一个智能的任务调度平台以及一个直观的数据可视化平台。

作为数据管理平台，FlowHub 提供了强大的数据存储和处理能力，用户可以安全地存储和管理各种类型的数据。通过直观的界面和易于使用的工具，用户可以轻松地对数据进行增删改查、导入导出等操作，实现对数据的全面管理。

作为工具开发平台，FlowHub 提供了丰富的开发工具和接口，使用户能够自定义和扩展平台的功能。用户可以使用自己熟悉的编程语言和技术，开发和集成各种工具、插件和扩展，以满足自己特定的需求。

流程构建是 FlowHub 的核心特性之一。它提供了直观的图形化界面，使用户能够以可视化的方式设计和构建工作流程。通过简单的拖放操作，用户可以将不同的任务和操作连接起来，形成完整的工作流程。这种图形化的方式不仅提高了工作效率，还降低了错误发生的概率。

任务调度是 FlowHub 的另一个重要功能，它能够智能地管理和调度任务的执行。用户可以设置任务的优先级、依赖关系和调度规则，FlowHub 将自动根据这些设置来合理安排任务的执行顺序和时间，以确保工作流程的顺利进行。

除此之外，FlowHub 还提供了强大的数据可视化功能。用户可以通过直观的图表、图形和报表，将复杂的数据转化为可理解和易于分析的形式。这使得用户能够更好地理解数据、发现潜在的模式和趋势，并做出基于数据的明智决策。

总之，FlowHub 是一个功能丰富、易用而强大的工作流云平台，为用户提供了全面的数据管理、工具开发、流程构建、任务调度和数据可视化能力，帮助用户更高效地处理和分析数据，提升工作效率和决策能力。

### 联系我们
email: flowhub_team@flowhub.com.cn

电话: 17399981010

微信: 
