

# Neural Disease Named Entity Extraction with Character-based BiLSTM+CRF in Japanese Medical Text


[Paper](https://arxiv.org/pdf/1806.03648.pdf)


End to end character based recurrent neural network, extract disease named entities from a japanese medical text and simultaneously judges its modality as either positive or negative.



char-based CRF or SVM methods


char-based DNE extraction with its modality judgement by using bidirectional LSTM coupled with CRF, which outperforms the state-of-art methods.

superiority of char-based NE extraction over word-based approaches

It does not require morphological and dependency analysis to come up with effective feature sets for NE extraction

Use the whole sentence to judge the modality of extracted NEs
