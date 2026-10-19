# From Matching toward Reasoning: A Critical Survey of Text-to-Video Retrieval

| Convention           | Details                                                                                                                                                  |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Reference numbering  | Bracketed reference numbers, such as [14] or [67], follow the survey bibliography and are not renumbered.                                                |
| Reported information | Publication details, dataset statistics, coverage judgments, and code/project links follow the manuscript; they are not independently updated here.      |
| Table organization   | The 16 manuscript tables are arranged by topic, with an eight-dimensional taxonomy and a paired method overview. Source locations are mapped at the end. |
| Coverage symbols     | ✅, ❌, △, and — retain the meanings specified in the legend accompanying each table.                                                                    |

## 1. Retrieval Tasks and Correspondence Requirements

<!-- Manuscript source: Table 5, p. 12 -->

| Ref.     | Task                                     | Query and Output                                                        | Correspondence Requirement                                                   |
| -------- | ---------------------------------------- | ----------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| [29]     | Sentence-to-video / clip retrieval       | Short description → ranked videos or clips                              | Semantic correspondence at the candidate-item level.                         |
| [30, 31] | Paragraph-to-video retrieval             | Multi-sentence description → ranked videos                              | Local event correspondence together with global description-video alignment. |
| [10]     | Partially relevant video retrieval       | Partial-content description → ranked whole videos                       | Identification of relevant content despite unrelated portions of the video.  |
| [8, 11]  | Temporal grounding / moment localization | Event description and given video → temporal interval                   | Query-conditioned localization and temporal boundary estimation.             |
| [32]     | Video corpus moment retrieval            | Description and video collection → video identity and temporal interval | Joint video identification and temporal localization.                        |
| [24]     | Interactive video retrieval              | Evolving user input → refined videos or segments                        | Query refinement, browsing, and incorporation of interaction or feedback.    |

| Note                | Details                                                                                                                                                              |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Task interpretation | Query length, retrieval target, temporal output, and interaction are separate properties; these tasks are not a strict hierarchy of difficulty (Section 3.2, p. 12). |

## 2. Comparative Analysis of Existing Surveys and Analytical Studies

<!-- Manuscript source: Table 3, p. 8; Section 2.2, pp. 7–9; Section 6.3, p. 36 -->

| Reference                | Primary Scope                             | Main Contributions / Strengths                                                                                                                                                                                                                | Scope and Limitations                                                                                                                                                                                                                |
| ------------------------ | ----------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Perez-Martin et al. [14] | Video-to-text retrieval and captioning    | • Reviews video-to-text methods and historical developments.<br>• Summarizes datasets and evaluation.                                                                                                                                         | Organized around video-to-text correspondence rather than a unified account of retrieval, grounding, and reasoning.                                                                                                                  |
| Zhu et al. [15]          | Deep video-text retrieval                 | • Organizes representations, embeddings, and matching.<br>• Covers objectives and benchmarks.                                                                                                                                                 | Retrieval architectures are central; temporal grounding and foundation-model reasoning are not jointly emphasized.                                                                                                                   |
| Lan et al. [16]          | Temporal sentence grounding               | • Classifies grounding methods and supervision settings.<br>• Reviews datasets and evaluation.                                                                                                                                                | Focuses on within-video grounding; corpus-level moment retrieval is discussed as an extension and research direction.                                                                                                                |
| Liu et al. [17]          | Video moment localization                 | • Reviews supervised, weakly supervised, and unsupervised localization.                                                                                                                                                                       | Centers on moment localization and supervision settings; corpus moment retrieval is discussed as a related task.                                                                                                                     |
| Schiappa et al. [18]     | Self-supervised video learning            | • Analyzes pretext, generative, contrastive, and cross-modal learning.                                                                                                                                                                        | Retrieval is mainly a downstream application of representation learning.                                                                                                                                                             |
| Madan et al. [19]        | Video foundation models                   | • Distinguishes image-based, video-based, and universal models.                                                                                                                                                                               | Organizes foundation models across multiple video tasks, including retrieval, rather than around retrieval-system design.                                                                                                            |
| Nguyen et al. [20]       | Video-language understanding              | • Connects architectures, training, and data.<br>• Covers retrieval, captioning, VideoQA, and LLM-based systems.                                                                                                                              | Provides a cross-task perspective rather than a retrieval-centred analysis of granularity and query difficulty.                                                                                                                      |
| Tang et al. [1]          | Video understanding with LLMs             | • Reviews Vid-LLM architectures, tasks, benchmarks, and methodological challenges.                                                                                                                                                            | Retrieval is one component of broader LLM-enabled video understanding.                                                                                                                                                               |
| Fragomeni et al. [13]    | Auxiliary information in retrieval        | • Analyzes visual, temporal, acoustic, linguistic, and generated evidence.                                                                                                                                                                    | Selects and organizes retrieval methods through their use of auxiliary information.                                                                                                                                                  |
| Pegia et al. [22]        | Empirical retrieval analysis              | • Compares model behavior.<br>• Examines query and dataset effects.                                                                                                                                                                           | Empirical conclusions are bounded by the 14 methods and three datasets evaluated.                                                                                                                                                    |
| Zhao et al. [21]         | Multimodal video understanding            | • Examines alignment, semantic expression, and reasoning.                                                                                                                                                                                     | Organizes broader video-understanding capabilities rather than retrieval as the primary task.                                                                                                                                        |
| Xing et al. [23]         | Video diffusion models                    | • Reviews diffusion-based generation, editing, and related understanding applications.                                                                                                                                                        | Retrieval and localization occupy part of a broader generative-model landscape.                                                                                                                                                      |
| Rossetto et al. [24]     | Interactive retrieval evaluation          | • Evaluates interactive video-search systems and search strategies.<br>• Examines user interactions and retrieval performance.                                                                                                                | Provides empirical insights into interactive search behavior rather than a comprehensive review of retrieval methodologies.                                                                                                          |
| **Our Survey**           | **Retrieval-centred video understanding** | • Connects retrieval granularity, representations, temporal grounding, auxiliary evidence, learning, foundation models, reasoning, and evaluation.<br>• Examines interactions between these dimensions and the evidence supporting their use. | English-language eligibility, indexed-publication availability, selective preprint inclusion, and terminology variation may affect coverage; the survey does not conduct a common controlled experiment across the reviewed methods. |

| Note             | Details                                                                                                                                                                                    |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Comparison scope | Specialist scope boundaries are not rankings of survey quality. Pegia et al. [22] and Rossetto et al. [24] provide empirical analyses rather than literature surveys (Section 2.3, p. 10). |

## 3. Existing Survey Summary of Research-Area Coverage

<!-- Manuscript source: Table 4, p. 9 -->

| Reference                | VTR | TG/VMR | AMR | SSL/VLP | VFM | Vid-LLM | GDR | RDM | QCA | EFF | ICR |
| ------------------------ | :-: | :----: | :-: | :-----: | :-: | :-----: | :-: | :-: | :-: | :-: | :-: |
| Perez-Martin et al. [14] | ✅  |   ❌   | ❌  |   ❌    | ❌  |   ❌    | ❌  | ✅  | ❌  | ❌  | ❌  |
| Zhu et al. [15]          | ✅  |   ❌   | ✅  |   ❌    | ❌  |   ❌    | ❌  | ✅  | ❌  | ✅  | ❌  |
| Lan et al. [16]          | ❌  |   ✅   | ❌  |   ❌    | ❌  |   ❌    | ❌  | ✅  | ❌  | ❌  | ❌  |
| Liu et al. [17]          | ❌  |   ✅   | ❌  |   ❌    | ❌  |   ❌    | ❌  | ✅  | ❌  | ❌  | ❌  |
| Schiappa et al. [18]     | ❌  |   ❌   | ❌  |   ✅    | ❌  |   ❌    | ❌  | ✅  | ❌  | ❌  | ❌  |
| Madan et al. [19]        | ✅  |   ❌   | ❌  |   ✅    | ✅  |   ❌    | ❌  | ✅  | ❌  | ❌  | ❌  |
| Nguyen et al. [20]       | ✅  |   ✅   | ❌  |   ✅    | ❌  |   ✅    | ❌  | ✅  | ❌  | ❌  | ❌  |
| Xing et al. [23]         | ✅  |   ✅   | ❌  |   ❌    | ❌  |   ❌    | ✅  | ❌  | ❌  | ❌  | ❌  |
| Fragomeni et al. [13]    | ✅  |   ❌   | ✅  |   ❌    | ❌  |   ❌    | ❌  | ✅  | ❌  | ❌  | ✅  |
| Tang et al. [1]          | ✅  |   ✅   | ✅  |   ❌    | ❌  |   ✅    | ❌  | ✅  | ❌  | ✅  | ❌  |
| Zhao et al. [21]         | ✅  |   ✅   | ✅  |   ✅    | ✅  |   ✅    | ❌  | ✅  | ❌  | ✅  | ❌  |
| Pegia et al. [22]        | ✅  |   ❌   | ❌  |   ❌    | ❌  |   ❌    | ❌  | ✅  | ✅  | ❌  | ❌  |
| Rossetto et al. [24]     | ✅  |   ❌   | ❌  |   ❌    | ❌  |   ❌    | ❌  | ❌  | ❌  | ✅  | ✅  |
| **Our Survey**           | ✅  |   ✅   | ✅  |   ✅    | ✅  |   ✅    | ✅  | ✅  | ✅  | ✅  | ✅  |

| Note    | Details                                                                                       |
| ------- | --------------------------------------------------------------------------------------------- |
| ✅      | Substantive coverage of the corresponding topic.                                              |
| ❌      | The topic is absent or receives only incidental treatment; it does not indicate poor quality. |
| VTR     | Video-text retrieval.                                                                         |
| TG/VMR  | Temporal grounding / video moment retrieval.                                                  |
| AMR     | Auxiliary multimodal retrieval.                                                               |
| SSL/VLP | Self-supervised learning / video-language pretraining.                                        |
| VFM     | Video foundation models.                                                                      |
| Vid-LLM | Video large language models.                                                                  |
| GDR     | Generative / diffusion retrieval.                                                             |
| RDM     | Retrieval datasets and metrics.                                                               |
| QCA     | Query-complexity analysis.                                                                    |
| EFF     | Efficiency and scalability.                                                                   |
| ICR     | Interactive and conversational retrieval.                                                     |

## 4. Survey Streams and Six-Dimension Coverage

<!-- Manuscript source: Table 2, p. 7 -->

| Survey Stream                               | Main Focus                                                                                     | VTR | TG  | RL  | AME | FM  | LLMR |
| ------------------------------------------- | ---------------------------------------------------------------------------------------------- | :-: | :-: | :-: | :-: | :-: | :--: |
| Video-to-text retrieval and captioning [14] | Retrieval, captioning, and cross-modal matching                                                | ✅  |  △  | ✅  |  △  |  —  |  —   |
| Deep video-text retrieval [15]              | Deep representations and matching architectures                                                | ✅  |  △  | ✅  |  △  |  △  |  —   |
| Temporal sentence grounding [16]            | Language-guided temporal localization                                                          |  △  | ✅  |  △  |  △  |  △  |  —   |
| Video moment localization [17]              | Moment localization, supervision, and evaluation                                               |  △  | ✅  |  △  |  △  |  △  |  —   |
| Self-supervised video learning [18]         | Self-supervised representation learning                                                        |  △  |  △  | ✅  | ✅  | ✅  |  △   |
| Video foundation models [19]                | Foundation representations and multimodal pretraining                                          |  △  |  △  | ✅  | ✅  | ✅  |  △   |
| Video understanding with LLMs [1]           | Video-language models and LLM-assisted reasoning                                               |  △  |  △  | ✅  | ✅  | ✅  |  ✅  |
| Auxiliary-information retrieval [13]        | Visual, temporal, and textual auxiliary evidence                                               | ✅  |  △  | ✅  | ✅  |  △  |  △   |
| **Our Survey**                              | Retrieval-centred analysis of temporal, multimodal, pretrained, and reasoning-assisted systems | ✅  | ✅  | ✅  | ✅  | ✅  |  ✅  |

| Note               | Details                                                                                                                                                                                         |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Coverage symbols   | ✅ = substantial coverage; △ = partial or limited coverage; — = outside the principal scope.                                                                                                    |
| Abbreviations      | VTR = video-text retrieval; TG = temporal grounding; RL = representation learning; AME = auxiliary/multimodal evidence; FM = foundation models; LLMR = LLM-assisted reasoning.                  |
| Matrix distinction | This stream-level summary uses the partial-coverage distinctions of manuscript Table 2. The preceding matrix preserves the substantive-versus-incidental classifications of manuscript Table 4. |

## 5. Unified Eight-Dimensional Taxonomy

<!-- Manuscript source: Figure 7, p. 17; Section 4, p. 15 -->

| No. | Design Dimension                       | Components                                                                                                             |
| :-: | -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
|  1  | Video and text representation learning | CNN / 3D CNN; Transformer encoders; CLIP-based representation; video foundation models; LLM-based text understanding.  |
|  2  | Temporal representation                | Pooling; recurrent models; temporal convolution; temporal attention; hierarchical modelling; long-video memory.        |
|  3  | Cross-modal alignment                  | Global matching; global-local alignment; token-frame interaction; multi-granularity matching; cross-encoder fusion.    |
|  4  | Auxiliary information                  | Audio; ASR; OCR; objects/regions; generated captions; query expansion.                                                 |
|  5  | Learning strategies                    | Supervised; weakly supervised; self-supervised; contrastive learning; distillation; efficient adaptation.              |
|  6  | Retrieval granularity                  | Whole-video retrieval; clip-level retrieval; partially relevant retrieval; temporal grounding; video moment retrieval. |
|  7  | Foundation models and LLMs             | Image-based VLMs; video-based VLMs; universal multimodal models; query reasoning; semantic reranking.                  |
|  8  | Emerging generative retrieval          | Diffusion retrieval; generative localization; generative-discriminative learning.                                      |

| Note                    | Details                                                                                                                             |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Taxonomy interpretation | These are overlapping, complementary design dimensions that may be combined in one system, not mutually exclusive model categories. |

## 6. Video and Query Representation Strategies

<!-- Manuscript source: Table 6, p. 18 -->

| Representation                                  | Representative Methods                                              | Principal Value                                              | Main Consideration                                                           |
| ----------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------ | ---------------------------------------------------------------------------- |
| Shared visual-semantic embeddings               | Video-text encoders [26, 36]; VSE++ as an image-text precedent [46] | Compact semantic representations and ranking-based learning. | Temporal detail depends on the video encoder and aggregation.                |
| Spatiotemporal representations                  | C3D [43]                                                            | Joint appearance and short-term motion modeling.             | Temporal coverage and processing cost depend on the input window.            |
| Transformer representations                     | ViViT, TimeSformer, and MMT [12, 47, 48]                            | Flexible contextual and temporal interactions.               | Sequence length affects computation and memory requirements.                 |
| CLIP-derived representations                    | CLIP4Clip and X-CLIP [29, 39]                                       | Transfer of pretrained image-language correspondence.        | Image-language transfer requires appropriate temporal adaptation.            |
| Video and multimodal foundation representations | VideoMAE and VATT [34, 45]                                          | Transferable video features and multimodal representations.  | Visual pretraining and language alignment remain distinct properties.        |
| LLM-assisted query representations              | Vid-LLM and reasoning-assisted retrieval approaches [1, 42]         | Query interpretation and semantic reformulation.             | Generated interpretations require grounding and preservation of user intent. |

| Note                    | Details                                                                |
| ----------------------- | ---------------------------------------------------------------------- |
| Representation families | Families may overlap and be combined within a single retrieval system. |

## 7. Overview of Representative Retrieval and Video-Language Methods

<!-- Manuscript source: Table 7, pp. 23–24; category labels condense its Approach column -->

| Ref.  | Method                   | Approach Category                               | Ref.  | Method                       | Approach Category                            |
| :---: | ------------------------ | ----------------------------------------------- | :---: | ---------------------------- | -------------------------------------------- |
| [67]  | MIL-NCE                  | Multiple-instance contrastive learning          | [34]  | VATT                         | Multimodal self-supervised learning          |
| [77]  | MDMMT                    | Multimodal Transformer                          | [44]  | Frozen in Time               | Joint image-video dual encoding              |
| [78]  | COTS                     | Two-stream pretraining                          | [79]  | CLIP-BNL                     | Negation-aware learning                      |
| [10]  | MS-SL                    | Multi-scale partial-relevance matching          | [80]  | ST-Graph                     | Spatial-temporal graph alignment             |
| [81]  | ViReD                    | Interactive dialogue-based retrieval            | [82]  | HD-VILA                      | High-resolution pretraining                  |
| [83]  | MCQ / BridgeFormer       | MCQ-guided pretraining                          | [84]  | Cali-NCE                     | Calibrated contrastive alignment             |
| [85]  | CLIP2Video               | Temporal-difference alignment                   | [86]  | UCOFIA                       | Coarse-to-fine alignment                     |
| [87]  | T2V2T                    | Cross-attention fusion                          | [88]  | DL-DKD                       | Dual learning and distillation               |
| [68]  | LAVENDER                 | Masked-language-model pretraining               | [89]  | MCKD                         | Multimodal contrastive distillation          |
| [90]  | LLM hard-sample learning | LLM-assisted hard-sample learning               | [91]  | MELTR                        | Meta-learned loss transformation             |
| [92]  | CSL                      | Complementarity-aware space learning            | [93]  | SMAUG                        | Sparse masked pretraining                    |
| [94]  | Me-Retriever             | Multi-event retrieval                           | [58]  | TEFAL                        | Text-conditioned audio-visual alignment      |
| [95]  | TW-BERT                  | Trajectory-word alignment                       | [96]  | SCEM / CVSV                  | Story-context-enhanced retrieval             |
| [74]  | MV-Adapter               | Parameter-efficient multimodal adaptation       | [97]  | Open-VCLIP++                 | Open-vocabulary video transfer               |
| [98]  | DeCMG                    | Cross-modal feature denoising                   | [99]  | TeachCLIP                    | Multi-teacher distillation                   |
| [100] | S3VL                     | Segment-sentence stitching                      | [101] | SDM + ALA                    | Semantic decomposition and local aggregation |
| [52]  | Video-ColBERT            | Multi-vector late interaction                   | [102] | STP                          | Spatial-temporal pooling and fusion          |
| [103] | TC-MGC                   | Text-conditioned multi-grained contrast         | [104] | RE-CVTR / EC-DVG             | Relational retrieval and grounding           |
| [105] | AMDNet                   | Active moment discovery                         | [106] | MS-SL++                      | Length-aware partial-relevance matching      |
| [107] | Multi-Agent Retrieval    | Multi-agent reasoning and reranking             | [108] | Vision-by-Prompt             | Prompt-based composed video retrieval        |
| [109] | SHC                      | Scale-hierarchy hubness control                 | [110] | HTVR                         | Hierarchical relative-similarity retrieval   |
| [111] | CVR-SDGM                 | Diffusion-assisted query enhancement            | [112] | APT                          | Two-stage image-video transfer               |
| [113] | HSP-SA                   | Pose-guided semantic alignment                  | [114] | TV-ProxyNet                  | Text-proxy generation                        |
| [115] | ARL                      | Ambiguity-restrained representation learning    | [116] | HLFormer                     | Euclidean-hyperbolic hierarchical modeling   |
| [117] | ProPy                    | Interactive prompt pyramids                     | [118] | RAL                          | Probabilistic robust alignment               |
| [119] | ReSpec                   | Relevance- and specificity-aware data filtering | [120] | Vid-Group / ReCorrect        | Pseudo-label temporal-grounding pretraining  |
| [121] | KDA                      | Diffusion-assisted temporal grounding           | [122] | TimeExpert                   | Expert-routed temporal grounding             |
| [123] | ED-VTG                   | MLLM-enriched temporal grounding                | [124] | TimeLens                     | Time-encoded temporal grounding              |
| [125] | VideoITG                 | Instruction-guided temporal grounding           | [126] | AdaVTG-LLM                   | Side-tuned temporal grounding                |
| [127] | VITAL                    | Tool-augmented long-video reasoning             | [128] | EagleNet                     | Energy-aware fine-grained alignment          |
| [62]  | VideoAligner             | Text-guided feature decomposition               | [129] | Cross-query Clue Enhancement | Cross-query clue mining and distillation     |

| Note                | Details                                                                                                                                                         |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Catalogue scope     | All 62 entries from manuscript Table 7 are included. Related video-language tasks are retained; this is not a list of 62 directly comparable retrieval systems. |
| Approach categories | Descriptive labels condense the manuscript’s Approach column and are not exclusive classifications.                                                             |

## 8. Detailed Method Catalogue

<!-- Manuscript source: Table 7, pp. 23–24 -->

| Catalogue Note         | Details                                                                                                                                                                                                                     |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Reference and ordering | Reference numbers follow the manuscript bibliography. Entries are grouped by the publication years reported in manuscript Table 7; order within a year follows that table.                                                  |
| Source fidelity        | Method names, venue/year entries, encoder names, datasets, and metric labels follow Table 7, including differences from the bibliography or other manuscript sections; those differences have not been silently reconciled. |
| Source-code links      | Link targets are extracted from the supplied PDF. — means no code/project URL was established in the reviewed material, not that no implementation exists. Link availability has not been independently checked.            |
| Encoder columns        | Auxiliary non-text encoders are included in the visual/video-side column when applicable; “aux.” denotes an auxiliary component.                                                                                            |
| Comparability          | Datasets and metrics primarily list retrieval-relevant evaluations. Different tasks, candidate pools, supervision, and evaluation protocols are not directly comparable.                                                    |

### 8.1. 2020

| Ref. | Method  | Venue, Year | Visual / Video-Side Encoder | Text Encoder | Approach                               | Dataset(s)           | Evaluation Metric(s)          |                          Code                          |
| :--: | ------- | ----------- | --------------------------- | ------------ | -------------------------------------- | -------------------- | ----------------------------- | :----------------------------------------------------: |
| [67] | MIL-NCE | CVPR, 2020  | I3D / S3D                   | word2vec     | Multiple-instance contrastive learning | YouCook2;<br>MSR-VTT | R@1;<br>R@5;<br>R@10;<br>MedR | [Link](https://www.di.ens.fr/willow/research/mil-nce/) |

### 8.2. 2021

| Ref. | Method         | Venue, Year   | Visual / Video-Side Encoder             | Text Encoder     | Approach                                  | Dataset(s)                        | Evaluation Metric(s)                 |                                    Code                                     |
| :--: | -------------- | ------------- | --------------------------------------- | ---------------- | ----------------------------------------- | --------------------------------- | ------------------------------------ | :-------------------------------------------------------------------------: |
| [34] | VATT           | NeurIPS, 2021 | Video Transformer;<br>audio Transformer | Text Transformer | Self-supervised video-audio-text learning | YouCook2;<br>MSR-VTT              | R@10;<br>MedR                        | [Link](https://github.com/google-research/google-research/tree/master/vatt) |
| [77] | MDMMT          | CVPRW, 2021   | CLIP ViT-B/32;<br>irCSN-152;<br>VGGish  | BERT             | Multidomain multimodal Transformer        | ActivityNet;<br>MSR-VTT;<br>LSMDC | R@1;<br>R@5;<br>R@10;<br>MnR;<br>MdR |                [Link](https://github.com/papermsucode/mdmmt)                |
| [44] | Frozen in Time | ICCV, 2021    | Space-Time Transformer                  | DistilBERT       | Joint image-video dual encoding           | MSR-VTT;<br>MSVD;<br>DiDeMo       | R@1;<br>R@5;<br>R@10;<br>MedR        |                                      —                                      |

### 8.3. 2022

| Ref. | Method             | Venue, Year  | Visual / Video-Side Encoder             | Text Encoder                     | Approach                                   | Dataset(s)                                            | Evaluation Metric(s)                       |                               Code                               |
| :--: | ------------------ | ------------ | --------------------------------------- | -------------------------------- | ------------------------------------------ | ----------------------------------------------------- | ------------------------------------------ | :--------------------------------------------------------------: |
| [78] | COTS               | CVPR, 2022   | ViT-B/16;<br>dVAE                       | BERT-base                        | Collaborative two-stream pretraining       | MSR-VTT                                               | R@1;<br>R@5;<br>R@10;<br>MR                |                                —                                 |
| [79] | CLIP-BNL           | ACM MM, 2022 | CLIP ViT-B/32                           | CLIP text encoder                | Bidirectional negation learning            | MSR-VTT-1K;<br>MSR-VTT-3K                             | R@1;<br>R@5;<br>R@10;<br>MIR               |          [Link](https://github.com/ruc-aimc-lab/nT2VR)           |
| [10] | MS-SL              | ACM MM, 2022 | ResNet-152;<br>I3D                      | RoBERTa                          | Multi-scale similarity learning for PRVR   | TVR;<br>ActivityNet Captions;<br>Charades-STA         | R@1;<br>R@5;<br>R@10;<br>R@100;<br>SumR    |             [Link](http://danieljf24.github.io/prvr)             |
| [80] | ST-Graph           | TMM, 2022    | ResNet-152;<br>scene graph;<br>GCN      | BERT                             | Spatial-temporal object-graph alignment    | MSR-VTT;<br>LSMDC                                     | R@1;<br>R@5;<br>R@10;<br>MedR;<br>SoR      |                                —                                 |
| [81] | ViReD              | ACM MM, 2022 | Frozen-in-Time video Transformer / CLIP | DistilBERT;<br>BART-Large (aux.) | Interactive dialog-based retrieval         | AVSD                                                  | R@1;<br>R@5;<br>R@10;<br>MedianR;<br>MeanR |                                —                                 |
| [82] | HD-VILA            | CVPR, 2022   | ResNet-50;<br>temporal Transformer      | BERT-large                       | High-resolution video-language pretraining | MSR-VTT;<br>DiDeMo;<br>LSMDC;<br>ActivityNet Captions | R@1;<br>R@5;<br>R@10;<br>R@50;<br>MedR     | [Link](https://github.com/microsoft/XPretrain/tree/main/hd-vila) |
| [83] | MCQ / BridgeFormer | CVPR, 2022   | VideoFormer (ViT-B/16)                  | DistilBERT                       | MCQ-guided video-language pretraining      | MSR-VTT;<br>MSVD;<br>LSMDC;<br>DiDeMo;<br>HowTo100M   | R@1;<br>R@5;<br>R@10;<br>R@50;<br>MedR     |            [Link](https://github.com/TencentARC/MCQ)             |

### 8.4. 2023

| Ref. | Method                   | Venue, Year | Visual / Video-Side Encoder            | Text Encoder                     | Approach                                           | Dataset(s)                                            | Evaluation Metric(s)                    |                      Code                       |
| :--: | ------------------------ | ----------- | -------------------------------------- | -------------------------------- | -------------------------------------------------- | ----------------------------------------------------- | --------------------------------------- | :---------------------------------------------: |
| [84] | Cali-NCE                 | CVPRW, 2023 | S3D / CLIP ViT-B/32                    | word2vec / CLIP text encoder     | Calibrated contrastive alignment                   | MSR-VTT;<br>MSVD                                      | R@1;<br>R@5;<br>R@10;<br>MedR           | [Link](https://github.com/nanxuanzhao/Cali-NCE) |
| [85] | CLIP2Video               | TMM, 2023   | CLIP ViT-B/32;<br>temporal Transformer | CLIP text encoder                | Temporal-difference and alignment learning         | MSR-VTT;<br>MSVD;<br>VATEX;<br>LSMDC                  | R@1;<br>R@5;<br>R@10;<br>MdR;<br>MnR    |                        —                        |
| [86] | UCOFIA                   | ICCV, 2023  | CLIP ViT-B/32                          | CLIP text encoder                | Unified coarse-to-fine alignment                   | MSR-VTT;<br>ActivityNet;<br>DiDeMo;<br>MSVD;<br>VATEX | R@1;<br>R@5;<br>R@10;<br>MnR            |   [Link](https://github.com/Ziyang412/UCoFiA)   |
| [87] | T2V2T                    | CVPRW, 2023 | BEiT;<br>temporal attention            | BERT-base                        | Bypass cross-attention fusion                      | MSR-VTT;<br>DiDeMo;<br>ActivityNet Captions           | R@1;<br>R@5;<br>R@10;<br>Avg. Recall    |                        —                        |
| [88] | DL-DKD                   | ICCV, 2023  | MS-SL visual features;<br>CLIP teacher | RoBERTa;<br>CLIP teacher         | Dual learning with dynamic distillation            | ActivityNet;<br>TVR                                   | R@1;<br>R@5;<br>R@10;<br>R@100;<br>SumR |  [Link](https://github.com/HuiGuanLab/DL-DKD)   |
| [68] | LAVENDER                 | CVPR, 2023  | Video Swin-B                           | BERT                             | Unified MLM video-language pretraining             | MSR-VTT;<br>DiDeMo;<br>MSVD;<br>LSMDC                 | R@1;<br>R@5;<br>R@10                    |  [Link](https://github.com/microsoft/LAVENDER)  |
| [89] | MCKD                     | TCSVT, 2023 | ResNet / I3D                           | GloVe                            | Multimodal contrastive knowledge distillation      | MSR-VTT;<br>TGIF;<br>VATEX                            | R@1;<br>R@5;<br>R@10;<br>MedR;<br>MnR   |                        —                        |
| [90] | LLM hard-sample learning | arXiv, 2023 | X-CLIP / Moment-DETR / QD-DETR         | X-CLIP / DETR text encoder       | LLM hard-sample generation and component weighting | MSVD;<br>QVHighlights                                 | R@1;<br>R@5;<br>MnR;<br>R@1@IoU;<br>mAP |                        —                        |
| [91] | MELTR                    | CVPR, 2023  | Host-model dependent                   | Host-model dependent             | Meta-learned loss transformation                   | YouCook2;<br>MSR-VTT                                  | R@1;<br>R@5;<br>R@10;<br>MedR           |     [Link](https://github.com/mlvlab/MELTR)     |
| [92] | CSL                      | TCSVT, 2023 | Memory-based video encoder             | Text encoder;<br>latent selector | Complementarity-aware dual-space learning          | MSR-VTT;<br>TGIF;<br>VATEX                            | R@1;<br>R@5;<br>R@10;<br>MedR           |    [Link](https://github.com/NovaMind-Z/CSL)    |
| [93] | SMAUG                    | ICCV, 2023  | CLIP ViT-B/16;<br>masked autoencoder   | BERT                             | Sparse masked video-language pretraining           | MSR-VTT;<br>DiDeMo;<br>ActivityNet Captions           | R@1;<br>R@5;<br>R@10                    |                        —                        |
| [94] | Me-Retriever             | ICCV, 2023  | CLIP visual encoder                    | CLIP text encoder                | Key-event modeling for multi-event retrieval       | ActivityNet Captions;<br>Charades-Event               | R@K (Avg./One-/All-Hit);<br>MedR        |  [Link](https://github.com/gengyuanmax/MeVTR)   |
| [58] | TEFAL                    | ICCV, 2023  | CLIP ViT-B/16 or B/32;<br>AST          | CLIP text encoder                | Text-conditioned audio-visual alignment            | MSR-VTT;<br>LSMDC;<br>VATEX;<br>Charades              | R@1;<br>R@5;<br>R@10;<br>MdR;<br>MnR    |                        —                        |
| [95] | TW-BERT                  | ICCV, 2023  | TimeSformer (ViT-B/16)                 | BERT                             | Trajectory-word alignment                          | DiDeMo;<br>LSMDC;<br>MSR-VTT;<br>ActivityNet Captions | R@1;<br>R@5;<br>R@10;<br>R@A;<br>MedR   |                        —                        |

### 8.5. 2024

| Ref.  | Method       | Venue, Year | Visual / Video-Side Encoder             | Text Encoder                         | Approach                                | Dataset(s)                                                     | Evaluation Metric(s)                            |                       Code                        |
| :---: | ------------ | ----------- | --------------------------------------- | ------------------------------------ | --------------------------------------- | -------------------------------------------------------------- | ----------------------------------------------- | :-----------------------------------------------: |
| [96]  | SCEM / CVSV  | TMM, 2024   | CLIP ViT-B/32;<br>temporal encoder      | CLIP text encoder                    | Story-context-enhanced retrieval        | CVSV;<br>CMD;<br>LSMDC                                         | R@1;<br>R@5;<br>R@10;<br>MedR;<br>MeanR;<br>AOP |  [Link](https://nfy-dot.github.io/CVSV-dataset/)  |
| [74]  | MV-Adapter   | CVPR, 2024  | CLIP ViT-B/16 (ViT-L/14 scale)          | CLIP text encoder                    | Parameter-efficient multimodal adapters | MSR-VTT;<br>MSVD;<br>LSMDC;<br>DiDeMo;<br>ActivityNet          | R@1;<br>R@5;<br>R@10                            |                         —                         |
| [97]  | Open-VCLIP++ | TPAMI, 2024 | CLIP ViT-B/16 or L/14;<br>BLIP-2 (aux.) | CLIP text encoder;<br>Llama-2 (aux.) | Open-vocabulary video-CLIP transfer     | MSR-VTT                                                        | R@1;<br>R@5;<br>R@10                            | [Link](https://github.com/wengzejia1/Open-VCLIP)  |
| [98]  | DeCMG        | ICME, 2024  | X-CLIP / X-Pool visual encoder          | X-CLIP / X-Pool text encoder         | Cross-modal feature denoising           | MSR-VTT;<br>MSVD;<br>ActivityNet;<br>DiDeMo                    | R@1;<br>R@5;<br>R@10;<br>MdR;<br>MnR            |                         —                         |
| [99]  | TeachCLIP    | CVPR, 2024  | CLIP ViT-B/32;<br>AFA                   | CLIP text encoder                    | Multi-teacher knowledge distillation    | MSR-VTT;<br>MSVD;<br>VATEX;<br>ActivityNet Captions;<br>DiDeMo | R@1;<br>R@5;<br>SumR                            | [Link](https://github.com/ruc-aimc-lab/TeachCLIP) |
| [100] | S3VL         | AAAI, 2024  | Video Swin                              | BERT                                 | Segment-sentence stitching pretraining  | MSR-VTT;<br>DiDeMo;<br>LSMDC                                   | R@1;<br>R@5;<br>R@10                            |                         —                         |

### 8.6. 2025

| Ref.  | Method                | Venue, Year          | Visual / Video-Side Encoder                  | Text Encoder                               | Approach                                                                    | Dataset(s)                                                                           | Evaluation Metric(s)                                                     |                             Code                             |
| :---: | --------------------- | -------------------- | -------------------------------------------- | ------------------------------------------ | --------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------ | :----------------------------------------------------------: |
| [101] | SDM + ALA             | AAAI, 2025           | ResNet / I3D host features                   | RoBERTa                                    | Semantic decomposition and local aggregation                                | TVR;<br>ActivityNet                                                                  | R@1;<br>R@5;<br>R@10;<br>R@100;<br>SumR                                  |                              —                               |
| [52]  | Video-ColBERT         | CVPR, 2025           | CLIP / SigLIP;<br>temporal Transformer       | CLIP / SigLIP text encoder                 | Contextualized multi-vector late interaction                                | MSR-VTT;<br>MSVD;<br>VATEX;<br>DiDeMo;<br>ActivityNet                                | R@1;<br>R@5;<br>R@10;<br>nDCG@10                                         |                              —                               |
| [102] | STP                   | ICME, 2025           | CLIP ViT-B/32                                | CLIP text/tag encoder                      | Spatial-temporal pooling and adaptive fusion                                | MSR-VTT;<br>MSVD;<br>VATEX                                                           | R@1;<br>R@5;<br>R@10;<br>MnR                                             |                              —                               |
| [103] | TC-MGC                | Inf. Fusion, 2025    | CLIP ViT-B/16 or B/32                        | CLIP text encoder                          | Text-conditioned multi-grained contrast                                     | MSR-VTT;<br>DiDeMo;<br>VATEX                                                         | R@1;<br>R@5;<br>R@10;<br>MdR;<br>MnR                                     |        [Link](https://github.com/JingXiaolun/TC-MGC)         |
| [104] | RE-CVTR / EC-DVG      | TIP, 2025            | C3D;<br>Transformer                          | Word2Vec;<br>LSTM;<br>Transformer          | Inter-/intra-video relational retrieval and grounding                       | ActivityNet Captions;<br>Charades-STA                                                | R@1/5/10/100;<br>SumR;<br>R@K@IoU                                        |           [Link](https://github.com/X7J92/MVT-RG)            |
| [105] | AMDNet                | TMM, 2025            | CLIP ViT-B/32;<br>temporal Transformer       | CLIP text encoder                          | Active moment discovery for PRVR                                            | ActivityNet Captions;<br>TVR                                                         | R@1;<br>R@5;<br>R@10;<br>R@100;<br>SumR                                  |                              —                               |
| [114] | TV-ProxyNet           | AAAI, 2025           | CLIP-ViP (ViT-B/32 or B/16)                  | CLIP text encoder                          | Text-proxy generation for N one-to-one text-video relationships             | MSR-VTT;<br>DiDeMo;<br>ActivityNet Captions                                          | R@1;<br>R@5;<br>R@10;<br>MdR;<br>MnR                                     | [Link](https://github.com/musicman217/Text-Proxy/tree/main)  |
| [115] | ARL                   | AAAI, 2025           | ResNet + I3D / CLIP-L/14                     | RoBERTa / CLIP text encoder                | Ambiguity-restrained representation learning for PRVR                       | TVR;<br>ActivityNet Captions                                                         | R@1;<br>R@5;<br>R@10;<br>R@100;<br>SumR                                  |                              —                               |
| [116] | HLFormer              | ICCV, 2025           | 2D/3D CNN host features                      | RoBERTa                                    | Hybrid Euclidean-hyperbolic hierarchical modeling for PRVR                  | ActivityNet Captions;<br>Charades-STA;<br>TVR                                        | R@1;<br>R@5;<br>R@10;<br>R@100;<br>SumR                                  |     [Link](https://github.com/lijun2005/ICCV25-HLFormer)     |
| [117] | ProPy                 | Findings EMNLP, 2025 | CLIP-B/32;<br>temporal adapters              | CLIP text encoder;<br>text prompts         | Interactive prompt pyramid with ancestor-descendant event interaction       | TVR;<br>ActivityNet Captions;<br>Charades-STA;<br>QVHighlights                       | R@1;<br>R@5;<br>R@10;<br>R@100;<br>SumR                                  |           [Link](https://github.com/BUAAPY/ProPy)            |
| [118] | RAL                   | Findings EMNLP, 2025 | ResNet + I3D host features                   | RoBERTa                                    | Probabilistic robust alignment with confidence-aware set matching           | TVR;<br>ActivityNet Captions                                                         | R@1;<br>R@5;<br>R@10;<br>R@100;<br>SumR                                  |                              —                               |
| [119] | ReSpec                | CVPR, 2025           | LanguageBind;<br>BT-Adapter                  | LanguageBind text encoder                  | Relevance- and specificity-aware online video-text data filtering           | WebVid2M;<br>VideoCC3M;<br>MSR-VTT;<br>DiDeMo;<br>LSMDC;<br>ActivityNet;<br>YouCook2 | R@1;<br>R@5;<br>R@10;<br>Avg. Recall                                     |           [Link](https://github.com/cdjkim/ReSpec)           |
| [120] | Vid-Group / ReCorrect | ICCV, 2025           | CLIP visual features;<br>SimBase             | CLIP text features                         | Pseudo-label refinement and memory-consensus correction for TVG pretraining | Vid-Group;<br>Charades-STA;<br>ActivityNet Captions                                  | R@0.3;<br>R@0.5;<br>R@0.7;<br>mIoU                                       |          [Link](https://github.com/baopj/Vid-Group)          |
| [121] | KDA                   | ICCV, 2025           | SlowFast + CLIP;<br>VGG (Charades-STA)       | CLIP text encoder;<br>GloVe (Charades-STA) | Diffusion-generated moment knowledge for temporal grounding                 | QVHighlights;<br>Charades-STA;<br>TACoS                                              | R@1@IoU 0.5/0.7;<br>mAP                                                  |                              —                               |
| [122] | TimeExpert            | ICCV, 2025           | ARIA ViT visual encoder;<br>slot compression | ARIA MoE Video-LLM                         | Dynamic expert routing for multi-task video temporal grounding              | YouCook2;<br>Charades-STA;<br>QVHighlights;<br>ActivityNet Captions                  | SODAc;<br>CIDEr;<br>METEOR;<br>F1;<br>R@1@IoU;<br>mIoU;<br>mAP;<br>HIT@1 | [Link](https://mwxely.github.io/projects/yang2025time/index) |
| [123] | ED-VTG                | ICCV, 2025           | EVA-CLIP ViT-G/14;<br>image/video Q-Former   | Video-LLaMA-7B                             | MLLM query enrichment with lightweight interval decoding                    | Charades-STA;<br>ActivityNet Captions;<br>TACoS                                      | R@0.3;<br>R@0.5;<br>R@0.7;<br>mIoU                                       |                              —                               |

### 8.7. 2026

| Ref.  | Method                       | Venue, Year                     | Visual / Video-Side Encoder                        | Text Encoder                            | Approach                                                                   | Dataset(s)                                                           | Evaluation Metric(s)                                     |                             Code                             |
| :---: | ---------------------------- | ------------------------------- | -------------------------------------------------- | --------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------- | :----------------------------------------------------------: |
| [106] | MS-SL++                      | TPAMI, 2026                     | ResNet-152 / I3D or CLIP ViT-B/32                  | RoBERTa / CLIP text encoder             | Length-aware multi-scale PRVR                                              | TVR;<br>ActivityNet Captions;<br>Charades-STA                        | R@1;<br>R@5;<br>R@10;<br>R@100;<br>SumR;<br>MedR         |        [Link](https://github.com/HuiGuanLab/ms-sl-pp)        |
| [107] | Multi-Agent Retrieval        | ICMR, 2026                      | IITV retrieval component;<br>Qwen3-VL              | IITV text component;<br>Qwen3-VL        | Multi-agent reasoning and iterative reranking                              | TRECVid AVS (tv16-tv23)                                              | Mean xinfAP                                              | [Link](https://github.com/nikkiwoo-gh/multi-agent-retrieval) |
| [108] | Vision-by-Prompt             | PR, 2026                        | BLIP-2 ViT-G                                       | Q-Former / prompt text branch           | Context-aware dual prompts for CoVR                                        | WebVid-CoVR                                                          | R@1;<br>R@5;<br>R@10;<br>R@50;<br>MeanR@K                |                              —                               |
| [109] | SHC                          | ICMR, 2026                      | CLIP;<br>temporal Transformer                      | CLIP text encoder                       | Scale-hierarchy hubness control                                            | MSR-VTT;<br>DiDeMo;<br>ActivityNet Captions                          | R@1;<br>R@5;<br>R@10;<br>MdR;<br>MnR;<br>hubness metrics |                              —                               |
| [110] | HTVR                         | PR, 2026                        | CLIP ViT-B/32                                      | CLIP text encoder                       | Hierarchical relative-similarity retrieval                                 | MSR-VTT;<br>MSVD;<br>DiDeMo                                          | R@1;<br>R@5;<br>R@10;<br>MdR;<br>MeanR;<br>MnR           |            [Link](https://github.com/junmaZ/HTVR)            |
| [111] | CVR-SDGM                     | PR, 2026                        | ResNeXt-ResNet / I3D;<br>FLUX-ResNet50 (aux.)      | BoW;<br>BiGRU;<br>1D CNN                | Diffusion-generated visual query enhancement                               | MSR-VTT;<br>VATEX;<br>MSVD;<br>DiDeMo                                | R@1;<br>R@5;<br>R@10;<br>MedR;<br>mAP;<br>SumR           |         [Link](https://github.com/MoliviaM/CVR-SDGM)         |
| [112] | APT                          | TMM, 2026                       | CLIP-based host;<br>STMA                           | Host CLIP text encoder                  | Two-stage image-video transfer                                             | MSR-VTT;<br>LSMDC;<br>MSVD                                           | R@1;<br>R@5;<br>R@10;<br>MeanR                           |           [Link](https://github.com/kang7734/APT)            |
| [113] | HSP-SA                       | Inf. Sci., 2026                 | CLIP ViT-B/32;<br>pose estimator                   | CLIP text encoder;<br>POS parser        | Pose-guided spatio-temporal semantic alignment                             | T-MARS                                                               | R@1;<br>R@5;<br>R@10;<br>mAP                             |                              —                               |
| [124] | TimeLens                     | CVPR, 2026                      | Qwen2.5-VL / Qwen3-VL visual stack                 | Qwen2.5-VL-7B / Qwen3-VL-8B             | Interleaved time encoding and thinking-free RLVR for VTG                   | Charades-TimeLens;<br>ActivityNet-TimeLens;<br>QVHighlights-TimeLens | R@1@IoU 0.3/0.5/0.7;<br>mIoU                             |         [Link](https://timelens-arc-lab.github.io/)          |
| [125] | VideoITG                     | CVPR, 2026                      | SigLIP                                             | Qwen2 / Video-LLM                       | Instruction-guided temporal grounding for adaptive frame selection         | VideoITG-40K;<br>LongVideoBench;<br>MLVU;<br>VideoMME                | Accuracy / benchmark score                               |          [Link](https://nvlabs.github.io/VideoITG/)          |
| [126] | AdaVTG-LLM                   | CVPRW, 2026                     | Video-LLaMA 3 visual encoder;<br>visual compressor | Frozen Video-LLaMA 3 + side-tuner       | Dual side-tuning with query-enriched MIL and token compression             | Charades-STA;<br>ActivityNet Captions;<br>TACoS                      | R@1@IoU 0.3/0.5/0.7;<br>mIoU                             |                              —                               |
| [127] | VITAL                        | CVPR, 2026                      | Qwen2.5-VL-7B visual encoder                       | Qwen2.5-VL-7B                           | Tool-augmented multimodal CoT with difficulty-aware GRPO                   | VUE-TR;<br>Charades-STA;<br>ActivityNet-MR;<br>NExT-GQA;<br>ReXTime  | Acc;<br>mIoU;<br>Recall@IoU                              |                              —                               |
| [128] | EagleNet                     | arXiv, 2026                     | CLIP ViT-B/16 or B/32                              | CLIP text encoder                       | Energy-aware fine-grained text-frame relationship learning                 | MSR-VTT;<br>DiDeMo;<br>MSVD;<br>VATEX                                | R@1;<br>R@5;<br>R@10;<br>MdR;<br>MnR;<br>Rsum            |         [Link](https://github.com/draym28/EagleNet)          |
| [62]  | VideoAligner                 | Pattern Recognit., 2026         | CLIP ViT-B/32                                      | CLIP text encoder;<br>POS-guided tokens | Text-guided global/object/event feature decomposition and alignment        | MSR-VTT;<br>DiDeMo;<br>MSVD                                          | R@1;<br>R@5;<br>R@10;<br>MdR;<br>MnR                     |                              —                               |
| [129] | Cross-query Clue Enhancement | Eng. Appl. Artif. Intell., 2026 | I3D + ResNet-152 / I3D                             | RoBERTa                                 | Cross-query contextual clue mining with dynamic clue distillation for PRVR | TVR;<br>ActivityNet Captions;<br>Charades-STA                        | R@1;<br>R@5;<br>R@10;<br>R@100;<br>SumR                  |                              —                               |

## 9. Retrieval and Temporal Localization Settings

<!-- Manuscript source: Table 8, p. 25 -->

| Setting                             | Objective                                             | Required Capability                                  | Main Difficulty                                                   |
| ----------------------------------- | ----------------------------------------------------- | ---------------------------------------------------- | ----------------------------------------------------------------- |
| Whole-video retrieval [57]          | Rank videos matching a textual description.           | Video-level semantic correspondence.                 | Preserving query-relevant detail within a global representation.  |
| Partially relevant retrieval [10]   | Retrieve videos containing locally relevant content.  | Local relevance estimation.                          | Preventing unrelated content from dominating the retrieval score. |
| Clip retrieval [29]                 | Retrieve relevant temporally restricted clips.        | Discrimination among candidate clips.                | Dependence on the available temporal boundaries.                  |
| Temporal sentence grounding [8, 11] | Locate the interval corresponding to a query.         | Semantic alignment and temporal boundary prediction. | Separating the target event from surrounding content.             |
| Video moment retrieval [17]         | Return the temporal moment matching a description.    | Query-conditioned interval selection.                | Ambiguity among related or repeated events.                       |
| Corpus moment retrieval [32]        | Return both the relevant video and temporal interval. | Video selection and temporal localization.           | Searching across videos and competing temporal candidates.        |

| Note                    | Details                                                                                                                                                                                                                                                     |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Overlapping terminology | Temporal sentence grounding and video moment retrieval often describe overlapping localization formulations; the separate rows preserve the manuscript’s terminology. Event-level reasoning is a cross-cutting capability, not a separate retrieval output. |

## 10. Temporal Localization Mechanisms and Supervision

<!-- Manuscript source: Table 9, p. 26 -->

| Dimension              | Category                     | Mechanism and Examples                                                 | Principal Value                                            | Main Consideration                                                   |
| ---------------------- | ---------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------- | -------------------------------------------------------------------- |
| Localization mechanism | Candidate-based localization | Segment scoring or temporal maps: CTRL, TGN, and 2D-TAN [8, 136, 137]. | Explicit comparison of candidate moments.                  | Candidate coverage, temporal resolution, and redundancy.             |
| Localization mechanism | Direct boundary prediction   | Attention-based coordinate regression: ABLR [138].                     | Direct estimation without a separate sliding-window stage. | Accurate learning of temporal boundaries from joint representations. |
| Localization mechanism | Sequential search            | Policy-based boundary adjustment: Read, Watch, and Move [139].         | Adaptive exploration of temporal content.                  | Reward design, exploration, and policy stability.                    |
| Localization mechanism | Transformer set prediction   | Joint moment and saliency prediction: Moment-DETR [141].               | End-to-end prediction of relevant intervals.               | Temporal resolution and discrimination among similar events.         |
| Localization mechanism | Generative localization      | Denoising-based temporal refinement: MomentDiff [41].                  | Progressive refinement of candidate intervals.             | Denoising cost and temporal boundary reliability.                    |
| Supervision setting    | Weakly supervised learning   | Latent video-text alignment: Text-Guided Attention [140].              | Learning without sentence-level boundary annotations.      | Ambiguity in locating the query-relevant interval.                   |
| Supervision setting    | Unsupervised localization    | Pretrained alignment or pseudo-supervision [17].                       | Reduced dependence on paired temporal annotations.         | Dependence on pretrained representations and alignment assumptions.  |

| Note                     | Details                                                                                                                         |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------- |
| Complementary dimensions | A localization architecture can be combined with different supervision settings; the two dimensions are not mutually exclusive. |

## 11. Representative Foundation Models and LLM-Assisted Approaches

<!-- Manuscript source: Table 10, pp. 29–30 -->

| Model / Resource     |   Year    | Category                        | Core Mechanism                                                                               | Retrieval Relevance                                                                               | Retrieval-Specific Qualification                                                                           |
| -------------------- | :-------: | ------------------------------- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| HowTo100M [3]        |   2019    | Pretraining resource            | Learning from large-scale narrated instructional videos.                                     | Provides weakly aligned video-language supervision for transferable representation learning.      | Narration and visible events may be temporally or semantically misaligned.                                 |
| VideoBERT [37]       |   2019    | Video-language model            | Joint modeling of discretized visual and linguistic tokens.                                  | Supports transferable video-language representation learning.                                     | Visual detail depends on the discretization and tokenization strategy.                                     |
| CLIP [4]             |   2021    | Image-language foundation model | Large-scale image-text contrastive learning.                                                 | Provides transferable semantic representations widely adapted to video retrieval.                 | Does not explicitly model temporal structure.                                                              |
| VideoCLIP [38]       |   2021    | Video-language pretraining      | Contrastive learning from video-text pairs with challenging negatives.                       | Provides transferable representations for video-text retrieval and related tasks.                 | Performance depends on pretraining scale and video-text pair construction.                                 |
| CLIP4Clip [29]       | 2021/2022 | CLIP-based retrieval model      | Temporal aggregation and matching of pretrained CLIP frame features.                         | Directly adapts image-language representations to video-text retrieval.                           | Temporal aggregation alone does not establish explicit temporal reasoning.                                 |
| X-CLIP [39]          |   2022    | CLIP-based retrieval model      | Multi-grained video-text alignment.                                                          | Strengthens correspondence across multiple semantic granularities.                                | Additional interaction increases matching complexity.                                                      |
| VideoMAE [45]        |   2022    | Video representation model      | Masked video modeling for self-supervised representation learning.                           | Provides transferable temporally informed visual features.                                        | Does not inherently provide language grounding.                                                            |
| BLIP-2 [157]         |   2023    | Vision-language model           | Q-Former interface between frozen visual and language models.                                | Provides transferable visual-language representations and query interaction.                      | Original architecture is primarily image-centred.                                                          |
| Video-ChatGPT [158]  | 2023/2024 | Video-LLM                       | Instruction-tuned conversational generation from video representations.                      | Supports video description, question answering, and language-guided interpretation.               | Does not independently demonstrate scalable corpus-level retrieval.                                        |
| InternVideo2 [150]   |   2024    | Video foundation model          | Progressive masked, contrastive, and generative multimodal pretraining.                      | Supports video-text retrieval and transferable video understanding.                               | Large-scale pretraining imposes substantial computational requirements.                                    |
| VideoAgent [155]     |   2024    | Multimodal video agent          | Structured temporal and object memory with tool-based access.                                | Supports evidence retrieval and reasoning over long videos.                                       | Multi-stage tool use increases inference complexity and latency.                                           |
| VideoMamba [159]     |   2024    | Video architecture              | State-space modeling for efficient long-range video processing.                              | Supports efficient video representation learning and has been evaluated for video-text retrieval. | Retrieval evaluation does not establish explicit verification of temporal or relational query constraints. |
| PLLaVA [160]         |   2024    | Video vision-language model     | Pooling-based adaptation of image-language representations to video.                         | Provides video-language representations relevant to candidate understanding.                      | Primarily evaluated on captioning and question-answering rather than corpus retrieval.                     |
| Apollo [6]           |   2025    | Video multimodal LLM            | Video-specific architecture and training for long-context perception.                        | Supports long-context candidate understanding and language-based interaction.                     | Retrieval requires additional task-specific system integration.                                            |
| InternVideo2.5 [161] |   2025    | Video multimodal LLM            | Hierarchical token compression for long and information-rich video contexts.                 | Supports fine-grained temporal interpretation and long-video understanding.                       | Long-context processing remains computationally demanding.                                                 |
| VideoLLaMA 3 [162]   |   2025    | Multimodal foundation model     | Video-oriented vision-language alignment and fine-tuning.                                    | Supports video interpretation and query understanding.                                            | Not designed as a dedicated corpus-level retrieval architecture.                                           |
| Qwen3-VL [163]       |   2025    | Multimodal LLM                  | Enhanced interleaved-MRoPE, DeepStack visual integration, and text-based temporal alignment. | Supports long-video understanding, temporal grounding, and multimodal reasoning.                  | Does not independently establish scalable corpus-level video indexing and ranking.                         |
| ViLL-E [164]         |   2026    | Retrieval-oriented Video-LLM    | Adaptive embedding generation with joint generative and contrastive learning.                | Directly supports text-to-video and video moment retrieval.                                       | Embedding generation introduces additional inference complexity.                                           |

| Note                  | Details                                                                                                                                                                                                                          |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Role-based comparison | The 18 entries include resources, representation models, retrieval models, and reasoning systems. Their tasks, modalities, objectives, and evaluation settings differ; the table does not imply directly comparable performance. |

## 12. Dataset Categories and Research Roles

<!-- Manuscript source: Table 11, p. 31 -->

| Category                      | Primary Role                                         | Representative Datasets                                 | Evaluation Focus                                                   |
| ----------------------------- | ---------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------------------ |
| Pretraining resources         | Learning transferable representations.               | HowTo100M [3]; Ego4D narrations [169].                  | Scale and diversity of supervision, together with alignment noise. |
| Retrieval benchmarks          | Ranking videos or clips from textual descriptions.   | MSVD, MSR-VTT, LSMDC, and VATEX [170–173].              | Semantic correspondence under a specified candidate pool.          |
| Temporal grounding benchmarks | Localizing language-relevant video content.          | DiDeMo, ActivityNet Captions, and TACoS [11, 174, 175]. | Temporal boundary estimation and event localization.               |
| Domain-specific datasets      | Evaluating specialized visual and temporal settings. | YouCook2, EPIC-KITCHENS-100, and Ego4D [169, 176, 177]. | Procedural, egocentric, and long-context understanding.            |
| Multilingual datasets         | Evaluating correspondence across languages.          | VATEX [173].                                            | Language coverage and cross-lingual transfer.                      |

| Note          | Details                                                                                                   |
| ------------- | --------------------------------------------------------------------------------------------------------- |
| Dataset roles | Categories overlap; individual datasets may support more than one research purpose or evaluation setting. |

## 13. Datasets and Benchmark Characteristics

<!-- Manuscript source: Table 12, p. 32; Section 6.1, pp. 33–34 -->

|   Ref.   | Dataset              | Domain                          | Scale                                        | Language / Query Annotations                   | Duration                      |
| :------: | -------------------- | ------------------------------- | -------------------------------------------- | ---------------------------------------------- | ----------------------------- |
|  [170]   | MSVD                 | Web videos                      | 1,970 clips                                  | Approximately 80.8K descriptions               | 1–62 s/clip                   |
|  [171]   | MSR-VTT              | Open-domain web                 | 10,000 clips                                 | 200K captions                                  | 41.2 h                        |
|  [178]   | TGIF                 | Animated GIFs                   | Approximately 100K GIFs                      | Approximately 120K descriptions                | Approximately 3.1 s/GIF       |
|  [172]   | LSMDC                | Movies                          | 128,085 clips                                | 128,118 sentences                              | Approximately 147 h           |
|  [173]   | VATEX                | Open-domain actions             | 41,269 clips                                 | 825,380 bilingual captions                     | Approximately 10 s/clip       |
|   [11]   | DiDeMo               | Flickr videos                   | 10,464 videos                                | 40,543 descriptions; 26,892 moments            | At most 30 s/video            |
|  [174]   | ActivityNet Captions | Activity videos                 | Approximately 20K videos                     | Approximately 100K localized descriptions      | 849 h                         |
|  [175]   | TACoS                | Cooking activities              | 127 videos                                   | 17,334 description instances                   | Approximately 287 s/video     |
| [8, 179] | Charades family      | Indoor activities               | 9,848 videos                                 | 27,847 descriptions; 16,128 STA pairs          | 82.3 h                        |
|   [32]   | TVR                  | TV shows                        | 21,793 videos                                | Approximately 109K query-moment pairs          | Approximately 76.2 s/video    |
|  [141]   | QVHighlights         | YouTube vlogs and news          | 10,148 videos                                | 10,310 queries; 18,367 relevant moments        | Approximately 150 s/video     |
|  [176]   | YouCook2             | Instructional cooking           | 2,000 videos                                 | Approximately 14K segment-text pairs           | 175.6 h                       |
|  [177]   | EPIC-KITCHENS-100    | Egocentric kitchens             | 700 videos                                   | 20,580 unique narrations                       | 100 h                         |
|  [169]   | Ego4D-NLQ            | Egocentric video                | 1,659 NLQ clips                              | Approximately 19.2K NLQ queries                | Approximately 227 h           |
|   [3]    | HowTo100M            | Instructional video             | Approximately 1.22M videos                   | Approximately 136M clip-text pairs             | Approximately 134,472 h       |
|  [180]   | AVSD                 | Indoor activities               | More than 11K videos                         | Multi-turn dialogues and summaries             | Approximately 30 s/video      |
|  [181]   | TRECVid AVS          | Open-domain web                 | 7,475 V3C1; 9,760 V3C2 videos                | Edition-specific natural-language topics       | Approximately 1,000 / 1,300 h |
|  [182]   | CMD                  | Movies                          | More than 30K clips from more than 3K movies | More than 30K scene descriptions               | More than 1K h                |
|   [96]   | CVSV                 | Movie-recap stories             | 85K story-video pairs                        | 60 aligned sentence-clip pairs per story       | —                             |
|  [183]   | WebVid-CoVR          | Open-domain web                 | Derived from WebVid2M                        | Approximately 1.6M composed-retrieval triplets | —                             |
|  [113]   | T-MARS               | Surveillance / person retrieval | 20,472 clips; 1,261 identities               | Descriptions collected from 17 annotators      | —                             |

| Note                         | Details                                                                                                                                                                                                         |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Units                        | K = thousands; M = millions; s = seconds; h = hours. Videos, clips, moments, narrations, dialogues, and composed-retrieval triplets are distinct units and must not be treated as equivalent measures of scale. |
| Duration                     | — means a directly comparable duration is not reported or is not meaningful for the corresponding setting.                                                                                                      |
| Dataset families and subsets | Charades family combines the original dataset with retrieval-oriented extensions. Ego4D-NLQ is a task-specific Ego4D subset. TRECVid collections vary by evaluation edition.                                    |
| AVSD                         | Video counts and dialogue instances refer to different units and must be distinguished when defining a retrieval split.                                                                                         |
| Protocol dependence          | Release, split, candidate pool, relevance definition, and task formulation must be controlled; a shared dataset name does not establish a shared evaluation setting.                                            |

## 14. Retrieval and Temporal Localization Metrics

<!-- Manuscript source: Table 13, p. 36; Section 6.2, pp. 34–35 -->

| Metric            | What It Measures                                              | Interpretive Limitation                                                                | Typical Setting                                        |
| ----------------- | ------------------------------------------------------------- | -------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| Recall@1/5/10     | Top-ranked retrieval success.                                 | Does not describe the full ranking or all relevant items under a hit-based definition. | Paired video-text retrieval [26, 29].                  |
| Median rank       | Median position of the relevant item.                         | Can hide poorly retrieved queries and changes with the candidate pool.                 | Video-text ranking [36].                               |
| Mean rank         | Average position of the relevant item.                        | Sensitive to large errors and candidate-pool size.                                     | Video-text ranking [36].                               |
| mAP               | Precision across relevant retrieval positions.                | Depends on relevance judgments, truncation, and the treatment of unjudged items.       | Multi-instance retrieval; moment retrieval [141, 177]. |
| Temporal IoU      | Overlap between predicted and annotated intervals.            | Boundary agreement alone does not verify all query semantics.                          | Temporal grounding [8, 11].                            |
| Recall@K, IoU ≥ α | Localization success among the top-K predictions.             | Depends on threshold, annotation rules, and video-identity requirements.               | Within-video and corpus moment retrieval [32].         |
| mIoU              | Average temporal overlap under a stated matching rule.        | Averages can conceal failures on short or ambiguous events.                            | Moment localization [11, 17].                          |
| nDCG              | Rank quality with graded relevance.                           | Requires a defined gain function and relevance scale.                                  | EPIC-KITCHENS-100 [177].                               |
| Mean xinfAP       | Estimated average precision with sampled relevance judgments. | Not interchangeable with fully judged mAP.                                             | TRECVid AVS [181].                                     |

| Note                 | Details                                                                                                                                                                                                                    |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Comparison condition | Scores are comparable only under matching relevance definitions, candidate sets, and evaluation protocols. Ranking and temporal overlap do not by themselves verify every semantic, compositional, or ordering constraint. |

## 15. Representation Trade-offs

<!-- Manuscript source: Table 14, p. 38 -->

| Representation            | Information Source                                       | Principal Value                                        | Main Qualification                                                             | Examples                                              |
| ------------------------- | -------------------------------------------------------- | ------------------------------------------------------ | ------------------------------------------------------------------------------ | ----------------------------------------------------- |
| Image-based encoder       | Sampled frames and text.                                 | Transferable image-language semantics.                 | Temporal relations depend on adaptation and aggregation.                       | CLIP, CLIP4Clip [4, 29].                              |
| Video-specific encoder    | Spatiotemporal observations.                             | Direct temporal representation learning.               | Language alignment and computational cost depend on training and architecture. | VideoMAE [45].                                        |
| RGB-only representation   | Visual frames or clips.                                  | A simpler input pipeline without auxiliary extraction. | Cannot directly access speech or other nonvisual evidence.                     | Frozen in Time [44].                                  |
| Multimodal representation | Visual, acoustic, transcript, OCR, or metadata features. | Complementary query-relevant evidence.                 | Missing modalities, extraction errors, and fusion overhead.                    | MMT, TEFAL [12, 58]; HowTo100M-based pretraining [3]. |

| Note                     | Details                                                                             |
| ------------------------ | ----------------------------------------------------------------------------------- |
| Trade-off interpretation | These entries describe design implications, not a numerical ranking across studies. |

## 16. Applications and Deployment Requirements

<!-- Manuscript source: Table 15, p. 41 -->

| Application                             | Retrieval Requirement                  | Key Capability                                      | Main Constraint                                  |
| --------------------------------------- | -------------------------------------- | --------------------------------------------------- | ------------------------------------------------ |
| Multimedia search and archives [26, 38] | Search heterogeneous collections.      | Semantic matching and indexing.                     | Collection scale and latency.                    |
| Recommendation systems                  | Relate content to expressed interests. | Intent-sensitive semantic matching.                 | Personalization beyond content similarity.       |
| Education and training [3, 176]         | Find concepts, explanations, or steps. | Temporal localization with context.                 | Long recordings and related procedural stages.   |
| Egocentric video search [169]           | Locate previously recorded activities. | Long-context evidence retrieval.                    | Sparse events and processing cost.               |
| Industrial / surveillance systems [113] | Discover domain-specific events.       | Reliable localization and discrimination.           | Domain shift and unfamiliar activities.          |
| Conversational video search [1, 24, 81] | Refine results through interaction.    | Dialogue context, feedback, and grounded responses. | Intent preservation, latency, and hallucination. |

| Note                 | Details                                                                                                        |
| -------------------- | -------------------------------------------------------------------------------------------------------------- |
| Application evidence | Entries summarize potential uses and associated requirements, not evidence of completed real-world deployment. |

## 17. Challenges, Evaluation Evidence, and Future Research Directions

<!-- Manuscript source: Table 16, pp. 42–43 -->

| No. | Challenge                                | Limitations in Existing Methods                                                                                                    | Evaluation Evidence                                                                                                                              | Future Research Objective                                                                                                |
| :-: | ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ |
|  1  | Compositional and temporal understanding | Concept matching and localization do not verify event relationships, temporal order, or complete query satisfaction.               | Query analysis [22] identifies semantic and temporal difficulties; multi-event retrieval [94] does not establish verification of query ordering. | Verify event identity, relations, temporal order, and dependencies against localized video evidence.                     |
|  2  | Partial relevance and localization       | Whole-video representations can dilute relevant events. Local matching does not necessarily provide accurate temporal boundaries.  | MS-SL [10] evaluates ranking; TVR [32] requires video selection and localization; QVHighlights [141] assesses multiple moments and saliency.     | Combine retrieval and localization; separately assess ranking, temporal boundaries, and relevant-moment coverage.        |
|  3  | Long-video evidence retention            | Sampling and compression can discard sparse events and distant context, even when longer inputs are supported.                     | Ego4D [169] supports sparse-event localization; LongVideoBench [167] evaluates long-context understanding, a related task.                       | Retain events and context using adaptive sampling, hierarchical representations, and resource-bounded memory.            |
|  4  | Multimodal reliability                   | Auxiliary modalities may be missing, noisy, or irrelevant; extraction errors can weaken multimodal fusion.                         | TEFAL [58] evaluates audio alignment; MissRAG [198] examines missing modalities in related tasks, not retrieval.                                 | Weight modalities by relevance and reliability; distinguish evidence sources and represent uncertainty.                  |
|  5  | Hallucination and evidence grounding     | Generated descriptions can invent events or omit details; language priors may distort reranking and explanations.                  | ARGUS [149], VidHalluc [199], and WildVideo [200] diagnose hallucination, omission, or grounding errors in video-language tasks.                 | Ground descriptions, explanations, and reranking in video evidence; assess omissions and unsupported claims.             |
|  6  | Cross-domain and multilingual transfer   | Short-video performance does not establish transfer across domains, durations, viewpoints, languages, or annotation settings.      | MSR-VTT, ActivityNet Captions, Ego4D, and VATEX [169, 171, 173, 174] define varied domains and language settings, not controlled transfer tests. | Test domain and language transfer under controlled supervision, pretraining, and adaptation settings.                    |
|  7  | Evaluation and reproducibility           | Aggregate scores conceal failures; inconsistent annotations, candidate pools, inputs, and inference settings confound comparisons. | Query analysis [22] and stress tests [192] expose hidden failures; annotation cleaning [188] demonstrates captioning changes only.               | Standardize protocols, disclose training and inference settings, and report capability-specific results and uncertainty. |
|  8  | Scalability and efficiency               | Fine-grained matching and LLM reranking increase costs; fewer trainable parameters do not guarantee faster inference.              | Complexity yields inconsistent gains within evaluated methods [22]; Vote-in-Context [195] examines accuracy–latency trade-offs.                  | Use efficient indexing and selective reasoning; report preprocessing, storage, latency, throughput, and memory.          |
|  9  | Interactive and conversational retrieval | Offline ranking overlooks interaction effort and latency; generated query refinements may alter user intent.                       | Video Browser Showdown [24] evaluates user-in-the-loop search; AVSD-based retrieval [81] examines dialogue-guided refinement.                    | Evaluate grounded dialogue through retrieval success, refinement time, user effort, and intent preservation.             |

## 18. Study Selection: Inclusion and Exclusion Criteria

<!-- Manuscript source: Table 1, p. 5 -->

| Criterion                   | Inclusion Criteria                                                                                                                 | Exclusion Criteria                                                                                               |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| Research relevance          | Text-video retrieval, semantic matching, temporal grounding, moment retrieval, or directly supporting methods.                     | No substantive relationship to language-conditioned video retrieval.                                             |
| Task scope                  | Whole-video, clip-level, partially relevant, and temporal moment retrieval.                                                        | Classification, action recognition, detection, tracking, or segmentation without language-conditioned retrieval. |
| Methodological contribution | Representation learning, temporal modeling, alignment, fusion, retrieval objectives, auxiliary evidence, adaptation, or reasoning. | Peripheral discussion without a substantive methodological or analytical contribution.                           |
| Evaluation quality          | Recognized datasets, clearly documented experiments, meaningful benchmark analysis, or rigorous analytical contribution.           | Insufficient methodological or experimental detail to support interpretation and comparison.                     |
| Publication type            | Peer-reviewed journal and conference papers, together with selected recent preprints without an equivalent peer-reviewed version.  | Non-scholarly webpages, opinion articles, tutorials, and redundant publication versions.                         |
| Language                    | English-language scholarly publications.                                                                                           | No available English scholarly version.                                                                          |
| Duplicate studies           | The most complete and authoritative publication retained.                                                                          | Redundant preprint, conference, or journal versions of the same study.                                           |
| Video generation            | Generative mechanisms contributing to retrieval, matching, or temporal localization.                                               | Text-to-video generation without a retrieval contribution.                                                       |
| Image retrieval             | Directly transferable cross-modal alignment or fusion concepts.                                                                    | Image-only retrieval without methodological relevance to video.                                                  |
| Foundation models and LLMs  | Contributions to retrieval, temporal understanding, query interpretation, multimodal evidence, or semantic reranking.              | General-purpose studies without a clear text-video retrieval connection.                                         |

## Source Mapping

| README Section | Table Group                                                     | Source in the Supplied Manuscript                                |
| -------------- | --------------------------------------------------------------- | ---------------------------------------------------------------- |
| 1              | Retrieval Tasks and Correspondence Requirements                 | Table 5, p. 12                                                   |
| 2              | Comparative Analysis of Existing Surveys and Analytical Studies | Table 3, p. 8; Section 2.2, pp. 7–9; Section 6.3, p. 36          |
| 3              | Existing Survey Summary of Research-Area Coverage               | Table 4, p. 9                                                    |
| 4              | Survey Streams and Six-Dimension Coverage                       | Table 2, p. 7                                                    |
| 5              | Unified Eight-Dimensional Taxonomy                              | Figure 7, p. 17; Section 4, p. 15                                |
| 6              | Video and Query Representation Strategies                       | Table 6, p. 18                                                   |
| 7              | Overview of Representative Retrieval and Video-Language Methods | Table 7, pp. 23–24; category labels condense its Approach column |
| 8              | Detailed Method Catalogue                                       | Table 7, pp. 23–24; embedded PDF code/project hyperlinks         |
| 9              | Retrieval and Temporal Localization Settings                    | Table 8, p. 25                                                   |
| 10             | Temporal Localization Mechanisms and Supervision                | Table 9, p. 26                                                   |
| 11             | Representative Foundation Models and LLM-Assisted Approaches    | Table 10, pp. 29–30                                              |
| 12             | Dataset Categories and Research Roles                           | Table 11, p. 31                                                  |
| 13             | Datasets and Benchmark Characteristics                          | Table 12, p. 32; Section 6.1, pp. 33–34                          |
| 14             | Retrieval and Temporal Localization Metrics                     | Table 13, p. 36; Section 6.2, pp. 34–35                          |
| 15             | Representation Trade-offs                                       | Table 14, p. 38                                                  |
| 16             | Applications and Deployment Requirements                        | Table 15, p. 41                                                  |
| 17             | Challenges, Evaluation Evidence, and Future Research Directions | Table 16, pp. 42–43                                              |
| 18             | Study Selection: Inclusion and Exclusion Criteria               | Table 1, p. 5                                                    |
