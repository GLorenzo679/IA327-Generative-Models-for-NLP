# TP3- Parsing

## Author: Gabriele LORENZO

### Answers:

**Cell E Q1: What do the "dependency" metrics measure? You do not need to explain what precision, recall and F1 are, but you do need to explain what sets they are computed against.**

The dependency metrics evaluate how closely the predicted tree’s dependency links align with those in the gold (reference) tree.

Dependency precision measures the proportion of links in the predicted set that also exist in the gold set, while dependency recall quantifies the proportion of gold set links that are correctly identified in the predicted set. The F1 score is calculated as the harmonic mean of precision and recall.

**Cell F Q2: What is BM25? How does this retriever work?**

BM25 (Best Matching 25) is a ranking function used in information retrieval to score documents based on their relevance to a given query.
The BM25 algorithm is an improved version of the TF-IDF algorithm. It uses TF (Term Frequency), IDF (Inverse Document Frequency) and Document Length Normalization to calculate the relevance of a document to a query.

The FewShotRetriever class is designed to find the most relevant examples from a dataset using BM25.

With the `build_index` method, the retriever creates the corpus: a collection of all the inputs of the dataset. This corpus will be then given to the BM25 algorithm to build the index.

The `get_samples` method is used to find the most relevant examples from the dataset given a query. It returns the top_n examples with the highest BM25 scores.

### Results:

**Model: `Qwen/Qwen2.5-1.5B`**

**0-shot**

| Metric               | Value          |
| -------------------- | -------------- |
| Exact Match          | 0.0            |
| Dependency Precision | 0.0            |
| Dependency Recall    | 0.0            |
| Dependency F1        | 0.0            |
| Subtree Precision    | 0.0            |
| Subtree Recall       | 0.0            |
| Subtree F1           | 0.0            |
| Edit Distance        | 0.9970         |
| Mean                 | 0.997          |
| Interval             | [0.995, 0.999] |
| N                    | 16             |
| GFLOPs               | 94.95          |
| Avg len              | 121            |

**1-shot**

| Metric                   | Value          |
| ------------------------ | -------------- |
| Exact Match              | 0.0            |
| Dependency Precision     | 0.1687         |
| Dependency Recall        | 0.0518         |
| Dependency F1            | 0.0713         |
| Subtree Precision        | 0.0392         |
| Subtree Recall           | 0.0088         |
| Subtree F1               | 0.0129         |
| Edit Distance            | 0.8467         |
| Interval (Edit distance) | [0.801, 0.893] |
| N                        | 48             |
| GFLOPs                   | 856.78         |
| Avg len                  | 986.40         |

**2-shot**

| Metric                   | Value          |
| ------------------------ | -------------- |
| Exact Match              | 0.0            |
| Dependency Precision     | 0.2971         |
| Dependency Recall        | 0.1187         |
| Dependency F1            | 0.1536         |
| Subtree Precision        | 0.0785         |
| Subtree Recall           | 0.0280         |
| Subtree F1               | 0.0392         |
| Edit Distance            | 0.5998         |
| Interval (Edit distance) | [0.559, 0.641] |
| N                        | 16             |
| GFLOPs                   | 1662.16        |
| Avg len                  | 1899.06        |

**4-shot**

| Metric                   | Value          |
| ------------------------ | -------------- |
| Exact Match              | 0.0            |
| Dependency Precision     | 0.3164         |
| Dependency Recall        | 0.0998         |
| Dependency F1            | 0.1339         |
| Subtree Precision        | 0.0847         |
| Subtree Recall           | 0.0191         |
| Subtree F1               | 0.0287         |
| Edit Distance            | 0.6092         |
| Interval (Edit distance) | [0.563, 0.655] |
| N                        | 16             |
| GFLOPs                   | 3040.24        |
| Avg len                  | 3448.94        |

**8-shot**

| Metric                   | Value          |
| ------------------------ | -------------- |
| Exact Match              | 0.0            |
| Dependency Precision     | 0.2779         |
| Dependency Recall        | 0.0985         |
| Dependency F1            | 0.1322         |
| Subtree Precision        | 0.0176         |
| Subtree Recall           | 0.0047         |
| Subtree F1               | 0.0072         |
| Edit Distance            | 0.5909         |
| Interval (Edit distance) | [0.553, 0.629] |
| N                        | 16             |
| GFLOPs                   | 6027.80        |
| Avg len                  | 6833.38        |

**16-shot**

| Metric                   | Value          |
| ------------------------ | -------------- |
| Exact Match              | 0.0            |
| Dependency Precision     | 0.3261         |
| Dependency Recall        | 0.0994         |
| Dependency F1            | 0.1428         |
| Subtree Precision        | 0.0243         |
| Subtree Recall           | 0.0144         |
| Subtree F1               | 0.0158         |
| Edit Distance            | 0.6078         |
| Interval (Edit distance) | [0.571, 0.644] |
| N                        | 32             |
| GFLOPs                   | 12457.19       |
| Avg len                  | 14069.56       |

**Model: `deepseek-ai/DeepSeek-R1-Distill-Qwen-1.5B`**

**0-shot**

| Metric                   | Value          |
| ------------------------ | -------------- |
| Exact Match              | 0.0            |
| Dependency Precision     | 0.0            |
| Dependency Recall        | 0.0            |
| Dependency F1            | 0.0            |
| Subtree Precision        | 0.0            |
| Subtree Recall           | 0.0            |
| Subtree F1               | 0.0            |
| Edit Distance            | 1.0146         |
| Interval (Edit distance) | [0.986, 1.043] |
| N                        | 16             |
| GFLOPs                   | 98.04          |
| Avg len                  | 121.0          |

**1-shot**

| Metric                   | Value          |
| ------------------------ | -------------- |
| Exact Match              | 0.0            |
| Dependency Precision     | 0.0625         |
| Dependency Recall        | 0.0222         |
| Dependency F1            | 0.0317         |
| Subtree Precision        | 0.0114         |
| Subtree Recall           | 0.0032         |
| Subtree F1               | 0.0050         |
| Edit Distance            | 0.9497         |
| Interval (Edit distance) | [0.901, 0.998] |
| N                        | 32             |
| GFLOPs                   | 837.16         |
| Avg len                  | 962.44         |

**2-shot**

| Metric                   | Value          |
| ------------------------ | -------------- |
| Exact Match              | 0.0            |
| Dependency Precision     | 0.1732         |
| Dependency Recall        | 0.0338         |
| Dependency F1            | 0.0513         |
| Subtree Precision        | 0.0189         |
| Subtree Recall           | 0.0028         |
| Subtree F1               | 0.0047         |
| Edit Distance            | 0.8001         |
| Interval (Edit distance) | [0.752, 0.848] |
| N                        | 48             |
| GFLOPs                   | 1617.96        |
| Avg len                  | 1842.88        |

**4-shot**

| Metric                   | Value          |
| ------------------------ | -------------- |
| Exact Match              | 0.0            |
| Dependency Precision     | 0.2968         |
| Dependency Recall        | 0.0838         |
| Dependency F1            | 0.1159         |
| Subtree Precision        | 0.0686         |
| Subtree Recall           | 0.0152         |
| Subtree F1               | 0.0221         |
| Edit Distance            | 0.6179         |
| Interval (Edit distance) | [0.581, 0.655] |
| N                        | 16             |
| GFLOPs                   | 3043.33        |
| Avg len                  | 3448.94        |

**8-shot**

| Metric                   | Value          |
| ------------------------ | -------------- |
| Exact Match              | 0.0            |
| Dependency Precision     | 0.3485         |
| Dependency Recall        | 0.1010         |
| Dependency F1            | 0.1362         |
| Subtree Precision        | 0.0761         |
| Subtree Recall           | 0.0186         |
| Subtree F1               | 0.0241         |
| Edit Distance            | 0.6306         |
| Interval (Edit distance) | [0.587, 0.674] |
| N                        | 48             |
| GFLOPs                   | 6096.63        |
| Avg len                  | 6907.25        |

**16-shot**

| Metric                   | Value          |
| ------------------------ | -------------- |
| Exact Match              | 0.0            |
| Dependency Precision     | 0.3523         |
| Dependency Recall        | 0.0975         |
| Dependency F1            | 0.1319         |
| Subtree Precision        | 0.0702         |
| Subtree Recall           | 0.0188         |
| Subtree F1               | 0.0264         |
| Edit Distance            | 0.6043         |
| Interval (Edit distance) | [0.565, 0.643] |
| N                        | 32             |
| GFLOPs                   | 12460.28       |
| Avg len                  | 14069.56       |

**Model: `HuggingFaceTB/SmolLM-135M`**

**0-shot**

| Metric                   | Value          |
| ------------------------ | -------------- |
| Exact Match              | 0.0            |
| Dependency Precision     | 0.0            |
| Dependency Recall        | 0.0            |
| Dependency F1            | 0.0            |
| Subtree Precision        | 0.0            |
| Subtree Recall           | 0.0            |
| Subtree F1               | 0.0            |
| Edit Distance            | 1.0017         |
| Interval (Edit distance) | [0.999, 1.005] |
| N                        | 16             |
| GFLOPs                   | 8.680          |
| Avg len                  | 121.0          |

**1-shot**

| Metric                   | Value          |
| ------------------------ | -------------- |
| Exact Match              | 0.0            |
| Dependency Precision     | 0.0749         |
| Dependency Recall        | 0.0147         |
| Dependency F1            | 0.0214         |
| Subtree Precision        | 0.0104         |
| Subtree Recall           | 0.0004         |
| Subtree F1               | 0.0008         |
| Edit Distance            | 0.9193         |
| Interval (Edit distance) | [0.875, 0.964] |
| N                        | 32             |
| GFLOPs                   | 96.943         |
| Avg len                  | 962.44         |

**2-shot**

| Metric                   | Value          |
| ------------------------ | -------------- |
| Exact Match              | 0.0            |
| Dependency Precision     | 0.2307         |
| Dependency Recall        | 0.0689         |
| Dependency F1            | 0.0984         |
| Subtree Precision        | 0.0382         |
| Subtree Recall           | 0.0101         |
| Subtree F1               | 0.0146         |
| Edit Distance            | 0.7125         |
| Interval (Edit distance) | [0.675, 0.750] |
| N                        | 32             |
| GFLOPs                   | 192.329        |
| Avg len                  | 1863.75        |

**4-shot**

| Metric                   | Value          |
| ------------------------ | -------------- |
| Exact Match              | 0.0            |
| Dependency Precision     | 0.2796         |
| Dependency Recall        | 0.0884         |
| Dependency F1            | 0.1235         |
| Subtree Precision        | 0.0759         |
| Subtree Recall           | 0.0166         |
| Subtree F1               | 0.0254         |
| Edit Distance            | 0.7084         |
| Interval (Edit distance) | [0.670, 0.747] |
| N                        | 32             |
| GFLOPs                   | 372.959        |
| Avg len                  | 3565.06        |

**8-shot**

| Metric                   | Value          |
| ------------------------ | -------------- |
| Exact Match              | 0.0            |
| Dependency Precision     | 0.0765         |
| Dependency Recall        | 0.0270         |
| Dependency F1            | 0.0375         |
| Subtree Precision        | 0.0123         |
| Subtree Recall           | 0.0033         |
| Subtree F1               | 0.0052         |
| Edit Distance            | 0.9286         |
| Interval (Edit distance) | [0.883, 0.975] |
| N                        | 32             |
| GFLOPs                   | 739.358        |
| Avg len                  | 7027.81        |

**16-shot**

| Metric                   | Value          |
| ------------------------ | -------------- |
| Exact Match              | 0.0            |
| Dependency Precision     | 0.0            |
| Dependency Recall        | 0.0            |
| Dependency F1            | 0.0            |
| Subtree Precision        | 0.0            |
| Subtree Recall           | 0.0            |
| Subtree F1               | 0.0            |
| Edit Distance            | 0.9931         |
| Interval (Edit distance) | [0.988, 0.998] |
| N                        | 16             |
| GFLOPs                   | 1449.413       |
| Avg len                  | 13706.31       |

#### Analysis:

The results highlight a clear trade-off between performance and computational cost across different few-shot settings for the evaluated models.

For Qwen/Qwen2.5-1.5B, the 0-shot setting exhibits an edit distance of 0.9970. Introducing few-shot examples improves performance: the 1-shot setting reduces the edit distance to 0.8467, and the 2-shot setting further drops it to 0.5998, meaning substantially fewer modifications are needed. However, beyond 2-shot, the improvements in edit distance (with values around 0.6092, 0.5909, and 0.6078 for 4-, 8-, and 16-shot respectively) plateau, even as computational demands (GFLOPs) and average prompt lengths increase dramatically.

A similar pattern emerges for DeepSeek-R1-Distill-Qwen-1.5B, where the 0-shot edit distance is very poor (1.0146), but few-shot prompting progressively improves performance, reaching an edit distance of 0.6043 at 16-shot.

In contrast SmolLM-135M, a considerably smaller model, starts with a 0-shot edit distance of 1.0017, improves to 0.7125 at 2-shot, but then degrades to nearly 1 at 16-shot. These findings suggest that while few-shot prompting can significantly reduce the edit distance (and hence the number of node changes required), there is an optimal balance to be struck between performance gains and the steep rise in computational cost.

The overall best performance is achieved by Qwen2.5-1.5B at 2-shot, with an edit distance of 0.5998, a dependency F1 of 0.1536. The only exception is the edit distance: Qwen2.5-1.5B at 8-shot has a lower edit distance of 0.5909. However, the computational cost is significantly higher for the 8-shot setting compared to the 2-shot setting, and the performance gains are marginal (even lower if we consider the dependency F1).
