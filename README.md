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
7. Annotation and Functional Analysis:
   Annotation of detected variations is performed to determine their potential functions and impacts. Annotations can include the genomic location of the variation, amino acid changes, potential functional pathways, etc.
    1. ANNOVAR: ANNOVAR is a tool for annotating genomic variations, providing detailed annotation information from various databases. It supports annotation of various types of variations, including SNPs, indels, structural variations, etc. For more information, please visit the [ANNOVAR official website](https://annovar.openbioinformatics.org/en/latest/).
    2. Variant Effect Predictor (VEP): VEP is a widely used tool for annotating and predicting the functional impacts of variations. It provides detailed annotation information, including gene effects, functional changes, mutation pathogenicity predictions, etc. For more information, please visit the [VEP official website](https://www.ensembl.org/info/docs/tools/vep/index.html).
    3. SnpEff: SnpEff is a tool for annotating and predicting the functional impacts of SNPs and structural variations. It provides annotation of variations, gene effects, functional changes, pathway analysis, etc. For detailed information, please visit the [SnpEff official website](http://snpeff.sourceforge.net/).
    4. dbNSFP: dbNSFP is a database for genomic functional predictions, offering extensive annotation and prediction information. It includes functional prediction results from multiple public databases and provides rich annotation information, such as SIFT, PolyPhen-2, GERP++, etc. For detailed information, please visit the [dbNSFP office website](https://sites.google.com/site/jpopgen/dbNSFP).
    5. DAVID (Database for Annotation, Visualization, and Integrated Discovery): DAVID is a tool for functional annotation and enrichment analysis that helps users understand the functional aspects and related biological processes of genomic variations. It integrates multiple public databases and provides annotation, functional analysis, pathway analysis, etc. For more information, please visit the [DAVID official website](https://david.ncifcrf.gov/).

8. Result Interpretation and Reporting:
   Based on the analysis results, the genomic sequencing data is interpreted, and a report is generated. The report may include information about the genetic risks, potential pathogenic variants, drug sensitivity, and other relevant information pertaining to the sample.

### Standard WGS bioinformatics analysis pipeline
![流程图](https://github.com/flowhub-team/WholeGenomeSequencing/blob/main/asset/WholeGenomeSequencingFlow.png)

### WGS standard workflow online analysis address
[WholeGenomeSequencingFlow](https://www.flowhub.com.cn/repo/flowhub_team/WholeGenomeSequencingFlow)

[https://www.flowhub.com.cn/repo/flowhub_team/WholeGenomeSequencingFlo](https://www.flowhub.com.cn/repo/flowhub_team/WholeGenomeSequencingFlow)

### WGS Standard Workflow Tutorial

#### How to use FlowHub to quickly complete data analysis
+ Step1：Click flow link，Enter FLOWHUB standard subscribe page，click "subscribe" to subscribe to the flow.
  ![step1](https://github.com/flowhub-team/WholeGenomeSequencing/blob/main/asset/tutoral-step1.png)
+ Step2：If you do not log in to the platform in advance, the subscription will not be successful, and you will enter the login interface of the FLOWHUB platform. If you already have an account, you can log in to the platform directly with the account password. If you do not have an account, click "sign up" to complete the registration according to the instructions.

   <img src="https://github.com/flowhub-team/WholeGenomeSequencing/blob/main/asset/tutoral-step2.png" width="400" alt="step2" />

+ Step3：Login to the platform, enter the FLOWHUB standard pipeline subscription interface again, click "subscribe" once more, proceed with the subscription, and click "Sure" to complete the subscription.
  ![step3](https://github.com/flowhub-team/WholeGenomeSequencing/blob/main/asset/tutoral-step3.png)

+ Step4：After completing the subscription, enter the Community-Subscribe Manage interface, add the corresponding standard process to the platform project, follow the instructions, and click "Sure" to create a new project.
  ![step4](https://github.com/flowhub-team/WholeGenomeSequencing/blob/main/asset/tutoral-step4.png)
+ Step5：Complete the new project creation according to the instructions.
  ![step5](https://github.com/flowhub-team/WholeGenomeSequencing/blob/main/asset/tutoral-step5.png)
+ Step6：After completing the creation of the new project, follow the instructions to add a flow again and enter the newly created project.
  ![step6](https://github.com/flowhub-team/WholeGenomeSequencing/blob/main/asset/tutoral-step6.png)
+ Step7：After successful addition, click on "PROJECT" in the upper right corner to display the project list and quickly access the project where the flow is located.
  ![step7](https://github.com/flowhub-team/WholeGenomeSequencing/blob/main/asset/tutoral-step7.png)
+ Step8：Upon entering the project, upload the data file that needs to be processed in the "Files" section. Then, navigate to the job and click on "Create Job" to create a task.
  ![step8](https://github.com/flowhub-team/WholeGenomeSequencing/blob/main/asset/tutoral-step8.png)
+ Step9：Click on "Choose Flow" and follow the instructions to select the flow. Then, click on "Next Step" to proceed with the selection of input files.
  ![step9](https://github.com/flowhub-team/WholeGenomeSequencing/blob/main/asset/tutoral-step9.png)
+ Step10：
1. Specify the root directory for all output files of the task in the "Output folder" field.
2. In the "Input File" section, select the input file based on the endpoint name.
3. In the "Output File" section, rename the output file that needs to be labeled.
   ![step10-1](https://github.com/flowhub-team/WholeGenomeSequencing/blob/main/asset/tutoral-step10-1.png)
4. Check the tools used within the job and make personalized parameter adjustments, such as CPU/GPU settings. If executing the standardization process, no changes are needed.
   ![step10-2](https://github.com/flowhub-team/WholeGenomeSequencing/blob/main/asset/tutoral-step10-2.png)
+ Step11：Once the settings are completed, follow the instructions to submit the job and wait for the computation results. For detailed instructions, please refer to the tutorial.``[https://doc.flowhub.com.cn/en/](https://doc.flowhub.com.cn/en/)。


### Introduction to Fowhub Platform

FlowHub is an innovative cloud-based workflow platform that offers users comprehensive and powerful functionalities. It serves not only as a reliable data management platform but also as a flexible tool development platform, efficient workflow construction platform, intelligent task scheduling platform, and intuitive data visualization platform.

As a data management platform, FlowHub provides robust data storage and processing capabilities, allowing users to securely store and manage various types of data. Through an intuitive interface and user-friendly tools, users can easily perform operations such as data manipulation, import/export, and comprehensive data management.

As a tool development platform, FlowHub offers a rich set of development tools and interfaces, enabling users to customize and extend the platform's functionalities. Users can utilize their preferred programming languages and technologies to develop and integrate various tools, plugins, and extensions to meet their specific needs.

Workflow construction is one of the core features of FlowHub. It provides a visual and intuitive graphical interface that allows users to design and build workflows in a visual manner. Through simple drag-and-drop operations, users can connect different tasks and operations to create complete workflows. This graphical approach not only enhances work efficiency but also reduces the probability of errors.

Task scheduling is another important feature of FlowHub, as it intelligently manages and schedules task execution. Users can set task priorities, dependencies, and scheduling rules, and FlowHub will automatically arrange task execution order and timing based on these settings to ensure the smooth progression of the workflow.

In addition, FlowHub provides powerful data visualization capabilities. Users can transform complex data into understandable and analyzable forms through intuitive charts, graphs, and reports. This enables users to better understand the data, discover potential patterns and trends, and make informed decisions based on the data.

In summary, FlowHub is a feature-rich, user-friendly, and powerful workflow cloud platform that provides comprehensive data management, tool development, workflow construction, task scheduling, and data visualization capabilities. It helps users efficiently handle and analyze data, enhance work efficiency, and improve decision-making abilities.

### To contact us, please use the following contact information:

email: flowhub_team@flowhub.com.cn

Phone: (+86)17399981010

Wechat:

<img src="https://github.com/flowhub-team/WholeGenomeSequencing/blob/main/asset/wechat.jpg" width="250" alt="add my wechat">
