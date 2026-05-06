# BERTopicModelling [![License: MIT][License-Badge]](LICENSE.md)

## Introduction

BERTopic is a topic modeling technique that leverages HuggingFace transformers and c-TF-IDF to create dense clusters allowing for easily interpretable topics whilst keeping important words in the topic descriptions.

## Source

- This project is based on the following paper: <https://arxiv.org/abs/2203.05794>
- Repository: <https://maartengr.github.io/BERTopic/index.html>

## Installation

```bash
pip install bertopic
```

## Requirements

- **Python >= 3.6**
- NumPy >= 1.20.0
- pandas >= 1.1.5
- scikit-learn >= 0.22.2
- **Data Corpus File (On which Topic Modelling has to be performed)**

## How to use?

Refer to the [bert.ipynb](bert.ipynb) notebook for the implementation of BERTopic on the dataset.

## Contributing

We welcome contributions! For bug fixes, issues or suggestions.If you find a bug, have a feature request, or want to improve the code, please feel free to open an issue or submit a pull request. Ensure to follow the contribution guidelines specified in the repository under the [LICENSE](LICENSE) section.

## License

BERTopic is developed and maintained by [Maarten Grootendorst](https://github.com/MaartenGr/MaartenGr)

HuggingFace Transformers is developed and maintained by HuggingFace team and the community.

This project is licensed under the MIT License. For details, refer to the [LICENSE](LICENSE) file.

Copyright (c) 2023 [Saksham Kumar](https://github.com/polymath_saksh) and the respective owners.

[License-Badge]:        https://img.shields.io/badge/License-MIT-blue.svg
