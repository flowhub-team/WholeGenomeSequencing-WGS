# Whole Genome Sequencing

### WGS Analysis Process

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
5. 数据比对和基因组装：
   将预处理后的reads与参考基因组进行比对或基因组装。比对是将reads与已知基因组序列进行比较，确定每个read在基因组中的位置。基因组装是将reads组合成更长的连续序列，以重建基因组的整体结构。
    1. 比对工具：
        1. BWA-MEM：用于将测序reads比对到参考基因组上。它采用快速的seed-and-extend算法，适用于处理较长的reads。你可以在[BWA-MEM GitHub](https://github.com/lh3/bwa)上获取详细的文档和使用说明。
        2. Bowtie2：用于将reads比对到参考基因组。它结合了快速的seed-and-extend算法和最大可信权值路径算法，适用于短序列的比对。了解更多信息，请访问[Bowtie2官方网站](https://www.ebi.ac.uk/~zerbino/velvet/)。
    2. 基因组装工具：
        1. SPAdes：用于从测序reads中进行基因组组装，包括单细胞测序数据。它结合了de Bruijn图算法和多种优化策略，适用于各种类型的测序数据。你可以在[SPAdes GitHub](https://github.com/ablab/spades)上找到更多信息和使用说明。
        2. Velvet：基于de Bruijn图的基因组组装工具，适用于短序列测序数据。它通过构建k-mer图来重建基因组序列。有关详细信息，请访问[Velvet官方网站](https://www.ebi.ac.uk/~zerbino/velvet/)。
        3. SOAPdenovo：一个用于基因组组装的快速和高效的工具。它基于de Bruijn图算法，适用于大规模基因组的组装。了解更多信息，请访问[SOAPdenovo官方网站](http://soap.genomics.org.cn/soapdenovo.html)。
6. 变异检测：
   使用比对或基因组装的结果，识别和分析样本中的基因组变异。这些变异可能包括单核苷酸多态性（SNPs）、插入/缺失（indels）、基因重排等。变异检测的方法和工具会根据研究目的而有所不同。
    1. GATK（Genome Analysis Toolkit）：GATK是一个广泛使用的工具集，用于基因组数据的分析和变异检测。它提供了多种算法和工具，包括基因组重比对、SNP/Indel检测、变异过滤等。了解更多信息，请访问[GATK官方网站](https://gatk.broadinstitute.org/)。
    2. VarScan：VarScan是一种用于检测SNPs、Indels和结构变异的工具，特别适用于对比分析。它能够从比对数据中识别变异，并提供统计学过滤和注释。有关详细信息，请访问[VarScan官方网站](http://varscan.sourceforge.net/)。
    3. FreeBayes：FreeBayes是一个开源的SNP和Indel检测工具，能够从测序数据中检测变异。它采用贝叶斯统计方法进行变异检测，并提供了高灵敏度和准确性。了解更多信息，请访问[FreeBayes GitHub](https://github.com/ekg/freebayes)。
    4. MuTect：MuTect是一个专门用于检测肿瘤样本中的突变的工具。它可以分析肿瘤-正常对比数据，并鉴定出肿瘤样本中的突变。了解更多信息，请访问[MuTect官方网站](https://software.broadinstitute.org/cancer/cga/mutect)。
    5. Samtools：Samtools是一个用于处理比对数据（SAM/BAM格式）的工具集，同时也提供了一些变异检测功能。它可以进行SNP/Indel检测、过滤和注释等。有关详细信息，请访问[Samtools官方网站](http://www.htslib.org/)。
    6. Platypus：Platypus是一个灵活的变异检测工具，可以从WGS数据中检测SNPs、Indels和结构变异。它具有高度可配置性，并且支持多样本分析。了解更多信息，请访问[Platypus GitHub](https://github.com/andyrimmer/Platypus)。
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
