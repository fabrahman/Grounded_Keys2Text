# Grounded_Keys2Text
This is a dataset and codebase for EMNLP'22 paper titled: "Grounded Keys-to-Text Generation: Towards Factual Open-Ended Generation" 

### EntDeGen Dataset

You can download the dataset from [here](https://drive.google.com/drive/folders/1hlL6nHsu-rIkaJh_6TwX49S4BWi-e7ju?usp=share_link).


The dataset contains the following files:
- `[train/test/dev].jsonl` 
- `[train/test/dev]_docs.pt`

The `*.jsonl` files contain the main data including the entity name, section titles, and a set of factual and topical keys. Below are information about main fields in the data:
- `doc_title`: entity name
- `sec_title`: section and subsection title(s)
- `topical_keys`: topical keys
- `infobox_keys`: factual keys (infobbox portion)
- `wikidata_keys`: factual keys (Wikidata portion)
- `text`: description to be generated (section text)

Other meta fields includes:
- `infobox_keyval`: infobox key-value pairs a long with their bertscore wrt to section text. The values will be used for evaluation.
- `wikidata_keyval`: Wikidata key-value pairs a long with their bertscore wrt to section text. The values will be used for evaluation.


The `*_docs.pt` files contain the corresponding grounding documents for each entity in the `*.jsonl` files. Additionally, we include the oracle ranking of the grounding documents based on Rouge2 scores (please refer to paper Sec. 5.1).

To load the grounding `*_docs.pt` files, run:

```
import torch
documents = torch.load('test_docs.pt')

# list fields for each entry
print(documents[0].keys())
```
