# Notes

## 2026-10-03 söndag

Part 3 evaluation: vocab allocation:

```text
Tokenizer:  char
Stats:  dict_items([('unused', 6), ('en', 98), ('zh', 8846), ('tr', 123), ('shared', 375)])
Examples: 
en ['h', 'w', 'q', 'า', '¢', 'ą', 'Ó', 'ก', 'ส', 'ṟ', 'ň', 'ż', 'Й', 'ร', 'ồ', 'ش', 'দ', 'া', '্', 'ạ']
zh ['，', '的', '。', '、', '在', '年', '一', '人', '有', '中', '是', '）', '（', '為', '大', '以', '了', '和', '不', '他']
tr ['k', 'ı', 'ü', 'ş', 'z', 'ç', 'ğ', 'ö', 'İ', '’', 'Ş', 'Ç', 'â', 'Ö', 'Ü', 'î', 'û', 'ი', 'ე', 'ა']
Tokenizer:  bpe_small
Stats:  dict_items([('unused', 32), ('en', 698), ('zh', 9352), ('tr', 854), ('shared', 1064)])
Examples: 
en ['w', '¡', '¢', 'Ó', 'ą', 'Ć', 'Ľ', 'ľ', 'ņ', 'ň', 'ŷ', 'Ż', 'ż', 'ǎ', 'ǚ', 'ʊ', '̈', 'Θ', 'Е', 'Й']
zh [';', '~', '¶', '·', '¹', 'À', 'Ô', 'Ċ', 'ċ', 'ĸ', 'Ļ', 'ŋ', 'Ź', 'ɑ', 'ɕ', 'ɛ', 'ɪ', 'ɿ', 'ʃ', 'ʉ']
tr ["'", '¼', 'Ç', 'Í', 'Ö', 'Ú', 'Ü', 'â', 'ç', 'î', 'ö', 'û', 'ü', 'Ā', 'ĉ', 'ė', 'Ğ', 'ğ', 'Ġ', 'ĥ']
Tokenizer:  bpe_large
Stats:  dict_items([('unused', 79), ('en', 2372), ('zh', 12254), ('tr', 2876), ('shared', 2419)])
Examples: 
en ['w', '¡', '¢', 'Ó', 'ą', 'Ć', 'Ľ', 'ľ', 'ņ', 'ň', 'ŷ', 'Ż', 'ż', 'ǎ', 'ǚ', 'ʊ', '̈', 'Θ', 'Е', 'Й']
zh [' ', '+', '1', '2', '3', '4', '5', '6', '8', ';', '~', '¶', '·', '¹', 'À', 'Ô', 'Ċ', 'ċ', 'ĸ', 'Ļ']
tr ["'", '¼', 'Ç', 'Í', 'Ö', 'Ú', 'Ü', 'â', 'ç', 'î', 'ö', 'û', 'ü', 'Ā', 'ĉ', 'ė', 'Ğ', 'ğ', 'Ġ', 'ĥ']

```

Part 3 evaluation BPC:

```text
Tokenizer:  char
Language:  en
/tmp/ipykernel_2287783/3570648520.py:9: UserWarning: enable_nested_tensor is True, but self.use_nested_tensor is False because encoder_layer.self_attn.batch_first was not True(use batch_first for better inference performance)
  self.transformer_encoder = TransformerEncoder(encoder_layers, nlayers)
BPC:  2.983023556486434
Language:  tr
BPC:  2.994630528787764
Language:  zh
BPC:  6.905701523321692
Overall BPC:  4.2943090631204255
--------------------------------------------------
Tokenizer:  bpe_small
Language:  en
BPC:  2.233810526882721
Language:  tr
BPC:  2.2704544428454407
Language:  zh
BPC:  6.5886987352322075
Overall BPC:  3.697496815561104
--------------------------------------------------
Tokenizer:  bpe_large
Language:  en
BPC:  2.066602076453999
Language:  tr
BPC:  2.1075152312655647
Language:  zh
BPC:  6.374066419840653
Overall BPC:  3.5159053625742906
--------------------------------------------------
```

Part 2:
- Your report should briefly explain:

  - the architecture you used;

  - your training-control policy;

  - important hyperparameters;

  - problems or failed choices you encountered;

  - any changes you made and why.

Utgick från tutorial:en på Pytorch-hemsidan. Upptäckte att 

```text
Tokenizer:  char
/tmp/ipykernel_2128857/4010154156.py:9: UserWarning: enable_nested_tensor is True, but self.use_nested_tensor is False because encoder_layer.self_attn.batch_first was not True(use batch_first for better inference performance)
  self.transformer_encoder = TransformerEncoder(encoder_layers, nlayers)
| epoch   1 |   200/ 3452 batches | lr 5.00 | ms/batch 10.78 | loss  5.50 | ppl   245.41
| epoch   1 |   400/ 3452 batches | lr 5.00 | ms/batch 10.47 | loss  4.20 | ppl    66.87
| epoch   1 |   600/ 3452 batches | lr 5.00 | ms/batch 10.40 | loss  3.92 | ppl    50.19
| epoch   1 |   800/ 3452 batches | lr 5.00 | ms/batch 10.37 | loss  3.62 | ppl    37.27
| epoch   1 |  1000/ 3452 batches | lr 5.00 | ms/batch 10.38 | loss  2.91 | ppl    18.44
| epoch   1 |  1200/ 3452 batches | lr 5.00 | ms/batch 10.39 | loss  2.50 | ppl    12.19
| epoch   1 |  1400/ 3452 batches | lr 5.00 | ms/batch 10.40 | loss  2.30 | ppl     9.96
| epoch   1 |  1600/ 3452 batches | lr 5.00 | ms/batch 10.40 | loss  2.08 | ppl     8.04
| epoch   1 |  1800/ 3452 batches | lr 5.00 | ms/batch 10.41 | loss  1.96 | ppl     7.12
| epoch   1 |  2000/ 3452 batches | lr 5.00 | ms/batch 10.42 | loss  1.83 | ppl     6.26
| epoch   1 |  2200/ 3452 batches | lr 5.00 | ms/batch 10.44 | loss  1.79 | ppl     5.99
| epoch   1 |  2400/ 3452 batches | lr 5.00 | ms/batch 10.44 | loss  1.72 | ppl     5.58
| epoch   1 |  2600/ 3452 batches | lr 5.00 | ms/batch 10.45 | loss  1.69 | ppl     5.42
| epoch   1 |  2800/ 3452 batches | lr 5.00 | ms/batch 10.45 | loss  1.65 | ppl     5.18
| epoch   1 |  3000/ 3452 batches | lr 5.00 | ms/batch 10.46 | loss  1.62 | ppl     5.05
| epoch   1 |  3200/ 3452 batches | lr 5.00 | ms/batch 10.46 | loss  1.57 | ppl     4.82
| epoch   1 |  3400/ 3452 batches | lr 5.00 | ms/batch 10.46 | loss  1.54 | ppl     4.68
-----------------------------------------------------------------------------------------
| end of epoch   1 | time: 37.56s | valid loss  0.88 | valid ppl     2.42
-----------------------------------------------------------------------------------------
| epoch   2 |   200/ 3452 batches | lr 4.75 | ms/batch 10.51 | loss  1.42 | ppl     4.12
| epoch   2 |   400/ 3452 batches | lr 4.75 | ms/batch 10.47 | loss  1.35 | ppl     3.86
| epoch   2 |   600/ 3452 batches | lr 4.75 | ms/batch 10.48 | loss  1.31 | ppl     3.71
| epoch   2 |   800/ 3452 batches | lr 4.75 | ms/batch 10.48 | loss  1.27 | ppl     3.56
| epoch   2 |  1000/ 3452 batches | lr 4.75 | ms/batch 10.49 | loss  1.22 | ppl     3.37
| epoch   2 |  1200/ 3452 batches | lr 4.75 | ms/batch 10.49 | loss  1.17 | ppl     3.21
| epoch   2 |  1400/ 3452 batches | lr 4.75 | ms/batch 10.50 | loss  1.11 | ppl     3.04
| epoch   2 |  1600/ 3452 batches | lr 4.75 | ms/batch 10.50 | loss  1.01 | ppl     2.76
| epoch   2 |  1800/ 3452 batches | lr 4.75 | ms/batch 10.50 | loss  0.91 | ppl     2.48
| epoch   2 |  2000/ 3452 batches | lr 4.75 | ms/batch 10.50 | loss  0.83 | ppl     2.28
| epoch   2 |  2200/ 3452 batches | lr 4.75 | ms/batch 10.51 | loss  0.78 | ppl     2.18
| epoch   2 |  2400/ 3452 batches | lr 4.75 | ms/batch 10.52 | loss  0.74 | ppl     2.10
| epoch   2 |  2600/ 3452 batches | lr 4.75 | ms/batch 10.52 | loss  0.72 | ppl     2.04
| epoch   2 |  2800/ 3452 batches | lr 4.75 | ms/batch 10.52 | loss  0.70 | ppl     2.01
| epoch   2 |  3000/ 3452 batches | lr 4.75 | ms/batch 10.52 | loss  0.69 | ppl     1.99
| epoch   2 |  3200/ 3452 batches | lr 4.75 | ms/batch 10.52 | loss  0.69 | ppl     1.99
| epoch   2 |  3400/ 3452 batches | lr 4.75 | ms/batch 10.52 | loss  0.67 | ppl     1.95
-----------------------------------------------------------------------------------------
| end of epoch   2 | time: 37.78s | valid loss  0.26 | valid ppl     1.30
-----------------------------------------------------------------------------------------
| epoch   3 |   200/ 3452 batches | lr 4.51 | ms/batch 10.57 | loss  0.63 | ppl     1.89
| epoch   3 |   400/ 3452 batches | lr 4.51 | ms/batch 10.53 | loss  0.62 | ppl     1.86
| epoch   3 |   600/ 3452 batches | lr 4.51 | ms/batch 10.53 | loss  0.62 | ppl     1.86
| epoch   3 |   800/ 3452 batches | lr 4.51 | ms/batch 10.53 | loss  0.63 | ppl     1.88
| epoch   3 |  1000/ 3452 batches | lr 4.51 | ms/batch 10.54 | loss  0.60 | ppl     1.82
| epoch   3 |  1200/ 3452 batches | lr 4.51 | ms/batch 10.54 | loss  0.60 | ppl     1.82
| epoch   3 |  1400/ 3452 batches | lr 4.51 | ms/batch 10.54 | loss  0.61 | ppl     1.84
| epoch   3 |  1600/ 3452 batches | lr 4.51 | ms/batch 10.55 | loss  0.60 | ppl     1.83
| epoch   3 |  1800/ 3452 batches | lr 4.51 | ms/batch 10.56 | loss  0.62 | ppl     1.86
| epoch   3 |  2000/ 3452 batches | lr 4.51 | ms/batch 10.57 | loss  0.60 | ppl     1.83
| epoch   3 |  2200/ 3452 batches | lr 4.51 | ms/batch 10.57 | loss  0.60 | ppl     1.83
| epoch   3 |  2400/ 3452 batches | lr 4.51 | ms/batch 10.57 | loss  0.60 | ppl     1.83
| epoch   3 |  2600/ 3452 batches | lr 4.51 | ms/batch 10.57 | loss  0.60 | ppl     1.82
| epoch   3 |  2800/ 3452 batches | lr 4.51 | ms/batch 10.58 | loss  0.62 | ppl     1.85
| epoch   3 |  3000/ 3452 batches | lr 4.51 | ms/batch 10.58 | loss  0.59 | ppl     1.81
| epoch   3 |  3200/ 3452 batches | lr 4.51 | ms/batch 10.57 | loss  0.62 | ppl     1.85
| epoch   3 |  3400/ 3452 batches | lr 4.51 | ms/batch 10.57 | loss  0.60 | ppl     1.82
-----------------------------------------------------------------------------------------
| end of epoch   3 | time: 37.96s | valid loss  0.28 | valid ppl     1.33
-----------------------------------------------------------------------------------------
Tokenizer:  bpe_small
| epoch   1 |   200/ 1823 batches | lr 5.00 | ms/batch 12.40 | loss  7.95 | ppl  2840.15
| epoch   1 |   400/ 1823 batches | lr 5.00 | ms/batch 12.00 | loss  6.94 | ppl  1031.81
| epoch   1 |   600/ 1823 batches | lr 5.00 | ms/batch 12.00 | loss  6.36 | ppl   575.97
| epoch   1 |   800/ 1823 batches | lr 5.00 | ms/batch 12.00 | loss  5.82 | ppl   335.89
| epoch   1 |  1000/ 1823 batches | lr 5.00 | ms/batch 12.01 | loss  4.11 | ppl    60.95
| epoch   1 |  1200/ 1823 batches | lr 5.00 | ms/batch 12.01 | loss  2.70 | ppl    14.83
| epoch   1 |  1400/ 1823 batches | lr 5.00 | ms/batch 12.02 | loss  2.07 | ppl     7.95
| epoch   1 |  1600/ 1823 batches | lr 5.00 | ms/batch 12.02 | loss  1.82 | ppl     6.17
| epoch   1 |  1800/ 1823 batches | lr 5.00 | ms/batch 12.02 | loss  1.70 | ppl     5.49
-----------------------------------------------------------------------------------------
| end of epoch   1 | time: 22.86s | valid loss  0.83 | valid ppl     2.30
-----------------------------------------------------------------------------------------
| epoch   2 |   200/ 1823 batches | lr 4.75 | ms/batch 12.09 | loss  1.50 | ppl     4.48
| epoch   2 |   400/ 1823 batches | lr 4.75 | ms/batch 12.03 | loss  1.43 | ppl     4.19
| epoch   2 |   600/ 1823 batches | lr 4.75 | ms/batch 12.03 | loss  1.38 | ppl     3.96
| epoch   2 |   800/ 1823 batches | lr 4.75 | ms/batch 12.04 | loss  1.38 | ppl     3.99
| epoch   2 |  1000/ 1823 batches | lr 4.75 | ms/batch 12.03 | loss  1.35 | ppl     3.84
| epoch   2 |  1200/ 1823 batches | lr 4.75 | ms/batch 12.04 | loss  1.33 | ppl     3.77
| epoch   2 |  1400/ 1823 batches | lr 4.75 | ms/batch 12.04 | loss  1.30 | ppl     3.67
| epoch   2 |  1600/ 1823 batches | lr 4.75 | ms/batch 12.04 | loss  1.30 | ppl     3.66
| epoch   2 |  1800/ 1823 batches | lr 4.75 | ms/batch 12.04 | loss  1.30 | ppl     3.66
-----------------------------------------------------------------------------------------
| end of epoch   2 | time: 22.84s | valid loss  0.48 | valid ppl     1.62
-----------------------------------------------------------------------------------------
| epoch   3 |   200/ 1823 batches | lr 4.51 | ms/batch 12.09 | loss  1.21 | ppl     3.34
| epoch   3 |   400/ 1823 batches | lr 4.51 | ms/batch 12.04 | loss  1.18 | ppl     3.26
| epoch   3 |   600/ 1823 batches | lr 4.51 | ms/batch 12.04 | loss  1.18 | ppl     3.27
| epoch   3 |   800/ 1823 batches | lr 4.51 | ms/batch 12.04 | loss  1.22 | ppl     3.38
| epoch   3 |  1000/ 1823 batches | lr 4.51 | ms/batch 12.04 | loss  1.20 | ppl     3.33
| epoch   3 |  1200/ 1823 batches | lr 4.51 | ms/batch 12.04 | loss  1.21 | ppl     3.36
| epoch   3 |  1400/ 1823 batches | lr 4.51 | ms/batch 12.05 | loss  1.20 | ppl     3.33
| epoch   3 |  1600/ 1823 batches | lr 4.51 | ms/batch 12.04 | loss  1.22 | ppl     3.38
| epoch   3 |  1800/ 1823 batches | lr 4.51 | ms/batch 12.05 | loss  1.20 | ppl     3.33
-----------------------------------------------------------------------------------------
| end of epoch   3 | time: 22.86s | valid loss  0.40 | valid ppl     1.49
-----------------------------------------------------------------------------------------
Tokenizer:  bpe_large
| epoch   1 |   200/ 1505 batches | lr 5.00 | ms/batch 17.08 | loss  8.90 | ppl  7326.12
| epoch   1 |   400/ 1505 batches | lr 5.00 | ms/batch 16.79 | loss  8.07 | ppl  3181.23
| epoch   1 |   600/ 1505 batches | lr 5.00 | ms/batch 16.80 | loss  7.75 | ppl  2310.07
| epoch   1 |   800/ 1505 batches | lr 5.00 | ms/batch 16.83 | loss  7.46 | ppl  1738.15
| epoch   1 |  1000/ 1505 batches | lr 5.00 | ms/batch 16.83 | loss  7.23 | ppl  1376.36
| epoch   1 |  1200/ 1505 batches | lr 5.00 | ms/batch 16.80 | loss  6.88 | ppl   974.48
| epoch   1 |  1400/ 1505 batches | lr 5.00 | ms/batch 16.81 | loss  6.19 | ppl   486.54
-----------------------------------------------------------------------------------------
| end of epoch   1 | time: 26.37s | valid loss  4.42 | valid ppl    83.45
-----------------------------------------------------------------------------------------
| epoch   2 |   200/ 1505 batches | lr 4.75 | ms/batch 16.89 | loss  4.86 | ppl   129.34
| epoch   2 |   400/ 1505 batches | lr 4.75 | ms/batch 16.83 | loss  4.19 | ppl    65.77
| epoch   2 |   600/ 1505 batches | lr 4.75 | ms/batch 16.83 | loss  3.64 | ppl    38.24
| epoch   2 |   800/ 1505 batches | lr 4.75 | ms/batch 16.83 | loss  3.19 | ppl    24.40
| epoch   2 |  1000/ 1505 batches | lr 4.75 | ms/batch 16.85 | loss  2.78 | ppl    16.05
| epoch   2 |  1200/ 1505 batches | lr 4.75 | ms/batch 16.84 | loss  2.51 | ppl    12.35
| epoch   2 |  1400/ 1505 batches | lr 4.75 | ms/batch 16.85 | loss  2.31 | ppl    10.04
-----------------------------------------------------------------------------------------
| end of epoch   2 | time: 26.38s | valid loss  0.77 | valid ppl     2.16
-----------------------------------------------------------------------------------------
| epoch   3 |   200/ 1505 batches | lr 4.51 | ms/batch 16.91 | loss  1.99 | ppl     7.31
| epoch   3 |   400/ 1505 batches | lr 4.51 | ms/batch 16.84 | loss  1.87 | ppl     6.49
| epoch   3 |   600/ 1505 batches | lr 4.51 | ms/batch 16.84 | loss  1.80 | ppl     6.04
| epoch   3 |   800/ 1505 batches | lr 4.51 | ms/batch 16.86 | loss  1.73 | ppl     5.61
| epoch   3 |  1000/ 1505 batches | lr 4.51 | ms/batch 16.85 | loss  1.65 | ppl     5.19
| epoch   3 |  1200/ 1505 batches | lr 4.51 | ms/batch 16.86 | loss  1.62 | ppl     5.05
| epoch   3 |  1400/ 1505 batches | lr 4.51 | ms/batch 16.85 | loss  1.57 | ppl     4.81
-----------------------------------------------------------------------------------------
| end of epoch   3 | time: 26.40s | valid loss  0.48 | valid ppl     1.61
-----------------------------------------------------------------------------------------
```

Tillägg:

if src_mask is None:
    """Generate a square causal mask for the sequence. The masked positions are filled with float('-inf').
    Unmasked positions are filled with float(0.0).
    """
    src_mask = nn.Transformer.generate_square_subsequent_mask(len(src)).to(device)


Efter tillägg:

```text
Tokenizer:  char
/tmp/ipykernel_2128857/388721432.py:9: UserWarning: enable_nested_tensor is True, but self.use_nested_tensor is False because encoder_layer.self_attn.batch_first was not True(use batch_first for better inference performance)
  self.transformer_encoder = TransformerEncoder(encoder_layers, nlayers)
| epoch   1 |   200/ 3452 batches | lr 5.00 | ms/batch 10.85 | loss  5.59 | ppl   268.09
| epoch   1 |   400/ 3452 batches | lr 5.00 | ms/batch 10.49 | loss  4.23 | ppl    68.53
| epoch   1 |   600/ 3452 batches | lr 5.00 | ms/batch 10.50 | loss  3.90 | ppl    49.60
| epoch   1 |   800/ 3452 batches | lr 5.00 | ms/batch 10.51 | loss  3.78 | ppl    43.68
| epoch   1 |  1000/ 3452 batches | lr 5.00 | ms/batch 10.51 | loss  3.68 | ppl    39.66
| epoch   1 |  1200/ 3452 batches | lr 5.00 | ms/batch 10.52 | loss  3.64 | ppl    38.09
| epoch   1 |  1400/ 3452 batches | lr 5.00 | ms/batch 10.53 | loss  3.70 | ppl    40.65
| epoch   1 |  1600/ 3452 batches | lr 5.00 | ms/batch 10.58 | loss  3.64 | ppl    37.95
| epoch   1 |  1800/ 3452 batches | lr 5.00 | ms/batch 10.58 | loss  3.60 | ppl    36.55
| epoch   1 |  2000/ 3452 batches | lr 5.00 | ms/batch 10.57 | loss  3.56 | ppl    35.32
| epoch   1 |  2200/ 3452 batches | lr 5.00 | ms/batch 10.58 | loss  3.53 | ppl    34.27
| epoch   1 |  2400/ 3452 batches | lr 5.00 | ms/batch 10.59 | loss  3.52 | ppl    33.64
| epoch   1 |  2600/ 3452 batches | lr 5.00 | ms/batch 10.64 | loss  3.50 | ppl    33.09
| epoch   1 |  2800/ 3452 batches | lr 5.00 | ms/batch 10.65 | loss  3.48 | ppl    32.32
| epoch   1 |  3000/ 3452 batches | lr 5.00 | ms/batch 10.65 | loss  3.47 | ppl    32.10
| epoch   1 |  3200/ 3452 batches | lr 5.00 | ms/batch 10.66 | loss  3.46 | ppl    31.94
| epoch   1 |  3400/ 3452 batches | lr 5.00 | ms/batch 10.67 | loss  3.44 | ppl    31.30
-----------------------------------------------------------------------------------------
| end of epoch   1 | time: 38.21s | valid loss  3.33 | valid ppl    27.83
-----------------------------------------------------------------------------------------
| epoch   2 |   200/ 3452 batches | lr 4.75 | ms/batch 10.71 | loss  3.32 | ppl    27.57
| epoch   2 |   400/ 3452 batches | lr 4.75 | ms/batch 10.67 | loss  3.30 | ppl    27.05
| epoch   2 |   600/ 3452 batches | lr 4.75 | ms/batch 10.66 | loss  3.29 | ppl    26.80
| epoch   2 |   800/ 3452 batches | lr 4.75 | ms/batch 10.67 | loss  3.29 | ppl    26.94
| epoch   2 |  1000/ 3452 batches | lr 4.75 | ms/batch 10.67 | loss  3.30 | ppl    27.03
| epoch   2 |  1200/ 3452 batches | lr 4.75 | ms/batch 10.67 | loss  3.33 | ppl    27.82
| epoch   2 |  1400/ 3452 batches | lr 4.75 | ms/batch 10.68 | loss  3.44 | ppl    31.25
| epoch   2 |  1600/ 3452 batches | lr 4.75 | ms/batch 10.67 | loss  3.44 | ppl    31.21
| epoch   2 |  1800/ 3452 batches | lr 4.75 | ms/batch 10.68 | loss  3.45 | ppl    31.42
| epoch   2 |  2000/ 3452 batches | lr 4.75 | ms/batch 10.69 | loss  3.45 | ppl    31.41
| epoch   2 |  2200/ 3452 batches | lr 4.75 | ms/batch 10.68 | loss  3.46 | ppl    31.73
| epoch   2 |  2400/ 3452 batches | lr 4.75 | ms/batch 10.67 | loss  3.45 | ppl    31.65
| epoch   2 |  2600/ 3452 batches | lr 4.75 | ms/batch 10.67 | loss  3.46 | ppl    31.68
| epoch   2 |  2800/ 3452 batches | lr 4.75 | ms/batch 10.69 | loss  3.44 | ppl    31.06
| epoch   2 |  3000/ 3452 batches | lr 4.75 | ms/batch 10.68 | loss  3.43 | ppl    30.91
| epoch   2 |  3200/ 3452 batches | lr 4.75 | ms/batch 10.70 | loss  3.43 | ppl    30.92
| epoch   2 |  3400/ 3452 batches | lr 4.75 | ms/batch 10.70 | loss  3.41 | ppl    30.34
-----------------------------------------------------------------------------------------
| end of epoch   2 | time: 38.52s | valid loss  3.29 | valid ppl    26.90
-----------------------------------------------------------------------------------------
| epoch   3 |   200/ 3452 batches | lr 4.51 | ms/batch 10.74 | loss  3.29 | ppl    26.82
| epoch   3 |   400/ 3452 batches | lr 4.51 | ms/batch 10.69 | loss  3.27 | ppl    26.37
| epoch   3 |   600/ 3452 batches | lr 4.51 | ms/batch 10.70 | loss  3.26 | ppl    25.95
| epoch   3 |   800/ 3452 batches | lr 4.51 | ms/batch 10.70 | loss  3.25 | ppl    25.91
| epoch   3 |  1000/ 3452 batches | lr 4.51 | ms/batch 10.70 | loss  3.25 | ppl    25.80
| epoch   3 |  1200/ 3452 batches | lr 4.51 | ms/batch 10.70 | loss  3.27 | ppl    26.23
| epoch   3 |  1400/ 3452 batches | lr 4.51 | ms/batch 10.70 | loss  3.37 | ppl    29.22
| epoch   3 |  1600/ 3452 batches | lr 4.51 | ms/batch 10.71 | loss  3.36 | ppl    28.75
| epoch   3 |  1800/ 3452 batches | lr 4.51 | ms/batch 10.71 | loss  3.36 | ppl    28.84
| epoch   3 |  2000/ 3452 batches | lr 4.51 | ms/batch 10.72 | loss  3.35 | ppl    28.38
| epoch   3 |  2200/ 3452 batches | lr 4.51 | ms/batch 10.73 | loss  3.35 | ppl    28.50
| epoch   3 |  2400/ 3452 batches | lr 4.51 | ms/batch 10.72 | loss  3.34 | ppl    28.20
| epoch   3 |  2600/ 3452 batches | lr 4.51 | ms/batch 10.71 | loss  3.35 | ppl    28.40
| epoch   3 |  2800/ 3452 batches | lr 4.51 | ms/batch 10.71 | loss  3.33 | ppl    27.93
| epoch   3 |  3000/ 3452 batches | lr 4.51 | ms/batch 10.71 | loss  3.33 | ppl    27.99
| epoch   3 |  3200/ 3452 batches | lr 4.51 | ms/batch 10.72 | loss  3.33 | ppl    27.95
| epoch   3 |  3400/ 3452 batches | lr 4.51 | ms/batch 10.72 | loss  3.32 | ppl    27.70
-----------------------------------------------------------------------------------------
| end of epoch   3 | time: 38.63s | valid loss  3.15 | valid ppl    23.25
-----------------------------------------------------------------------------------------
Tokenizer:  bpe_small
| epoch   1 |   200/ 1823 batches | lr 5.00 | ms/batch 12.40 | loss  7.97 | ppl  2900.70
| epoch   1 |   400/ 1823 batches | lr 5.00 | ms/batch 12.14 | loss  6.99 | ppl  1082.42
| epoch   1 |   600/ 1823 batches | lr 5.00 | ms/batch 12.14 | loss  6.37 | ppl   585.63
| epoch   1 |   800/ 1823 batches | lr 5.00 | ms/batch 12.14 | loss  6.19 | ppl   486.63
| epoch   1 |  1000/ 1823 batches | lr 5.00 | ms/batch 12.15 | loss  5.94 | ppl   378.14
| epoch   1 |  1200/ 1823 batches | lr 5.00 | ms/batch 12.14 | loss  5.78 | ppl   323.50
| epoch   1 |  1400/ 1823 batches | lr 5.00 | ms/batch 12.17 | loss  5.67 | ppl   288.99
| epoch   1 |  1600/ 1823 batches | lr 5.00 | ms/batch 12.16 | loss  5.60 | ppl   270.08
| epoch   1 |  1800/ 1823 batches | lr 5.00 | ms/batch 12.15 | loss  5.53 | ppl   253.14
-----------------------------------------------------------------------------------------
| end of epoch   1 | time: 23.15s | valid loss  5.42 | valid ppl   225.30
-----------------------------------------------------------------------------------------
| epoch   2 |   200/ 1823 batches | lr 4.75 | ms/batch 12.19 | loss  5.43 | ppl   228.57
| epoch   2 |   400/ 1823 batches | lr 4.75 | ms/batch 12.14 | loss  5.37 | ppl   214.49
| epoch   2 |   600/ 1823 batches | lr 4.75 | ms/batch 12.15 | loss  5.33 | ppl   205.88
| epoch   2 |   800/ 1823 batches | lr 4.75 | ms/batch 12.15 | loss  5.35 | ppl   211.12
| epoch   2 |  1000/ 1823 batches | lr 4.75 | ms/batch 12.15 | loss  5.33 | ppl   205.47
| epoch   2 |  1200/ 1823 batches | lr 4.75 | ms/batch 12.15 | loss  5.30 | ppl   199.80
| epoch   2 |  1400/ 1823 batches | lr 4.75 | ms/batch 12.15 | loss  5.26 | ppl   193.08
| epoch   2 |  1600/ 1823 batches | lr 4.75 | ms/batch 12.16 | loss  5.25 | ppl   191.37
| epoch   2 |  1800/ 1823 batches | lr 4.75 | ms/batch 12.15 | loss  5.23 | ppl   187.37
-----------------------------------------------------------------------------------------
| end of epoch   2 | time: 23.11s | valid loss  5.16 | valid ppl   173.58
-----------------------------------------------------------------------------------------
| epoch   3 |   200/ 1823 batches | lr 4.51 | ms/batch 12.21 | loss  5.18 | ppl   178.05
| epoch   3 |   400/ 1823 batches | lr 4.51 | ms/batch 12.16 | loss  5.15 | ppl   171.76
| epoch   3 |   600/ 1823 batches | lr 4.51 | ms/batch 12.16 | loss  5.12 | ppl   168.09
| epoch   3 |   800/ 1823 batches | lr 4.51 | ms/batch 12.16 | loss  5.16 | ppl   174.92
| epoch   3 |  1000/ 1823 batches | lr 4.51 | ms/batch 12.17 | loss  5.16 | ppl   173.33
| epoch   3 |  1200/ 1823 batches | lr 4.51 | ms/batch 12.17 | loss  5.15 | ppl   171.62
| epoch   3 |  1400/ 1823 batches | lr 4.51 | ms/batch 12.17 | loss  5.12 | ppl   167.10
| epoch   3 |  1600/ 1823 batches | lr 4.51 | ms/batch 12.17 | loss  5.12 | ppl   167.07
| epoch   3 |  1800/ 1823 batches | lr 4.51 | ms/batch 12.16 | loss  5.11 | ppl   164.92
-----------------------------------------------------------------------------------------
| end of epoch   3 | time: 23.13s | valid loss  5.05 | valid ppl   156.53
-----------------------------------------------------------------------------------------
Tokenizer:  bpe_large
| epoch   1 |   200/ 1505 batches | lr 5.00 | ms/batch 17.16 | loss  8.94 | ppl  7601.17
| epoch   1 |   400/ 1505 batches | lr 5.00 | ms/batch 16.98 | loss  8.13 | ppl  3386.09
| epoch   1 |   600/ 1505 batches | lr 5.00 | ms/batch 16.93 | loss  7.77 | ppl  2379.90
| epoch   1 |   800/ 1505 batches | lr 5.00 | ms/batch 16.93 | loss  7.45 | ppl  1712.47
| epoch   1 |  1000/ 1505 batches | lr 5.00 | ms/batch 16.93 | loss  7.23 | ppl  1377.36
| epoch   1 |  1200/ 1505 batches | lr 5.00 | ms/batch 16.96 | loss  7.10 | ppl  1214.02
| epoch   1 |  1400/ 1505 batches | lr 5.00 | ms/batch 16.94 | loss  6.95 | ppl  1046.59
-----------------------------------------------------------------------------------------
| end of epoch   1 | time: 26.61s | valid loss  6.68 | valid ppl   796.89
-----------------------------------------------------------------------------------------
| epoch   2 |   200/ 1505 batches | lr 4.75 | ms/batch 17.03 | loss  6.71 | ppl   819.39
| epoch   2 |   400/ 1505 batches | lr 4.75 | ms/batch 16.94 | loss  6.57 | ppl   712.63
| epoch   2 |   600/ 1505 batches | lr 4.75 | ms/batch 16.96 | loss  6.47 | ppl   647.26
| epoch   2 |   800/ 1505 batches | lr 4.75 | ms/batch 16.95 | loss  6.40 | ppl   601.95
| epoch   2 |  1000/ 1505 batches | lr 4.75 | ms/batch 16.94 | loss  6.32 | ppl   554.42
| epoch   2 |  1200/ 1505 batches | lr 4.75 | ms/batch 16.96 | loss  6.30 | ppl   542.21
| epoch   2 |  1400/ 1505 batches | lr 4.75 | ms/batch 16.95 | loss  6.25 | ppl   518.41
-----------------------------------------------------------------------------------------
| end of epoch   2 | time: 26.59s | valid loss  6.09 | valid ppl   441.89
-----------------------------------------------------------------------------------------
| epoch   3 |   200/ 1505 batches | lr 4.51 | ms/batch 17.03 | loss  6.14 | ppl   462.02
| epoch   3 |   400/ 1505 batches | lr 4.51 | ms/batch 16.97 | loss  6.06 | ppl   428.44
| epoch   3 |   600/ 1505 batches | lr 4.51 | ms/batch 16.96 | loss  6.02 | ppl   411.78
| epoch   3 |   800/ 1505 batches | lr 4.51 | ms/batch 16.97 | loss  6.00 | ppl   402.76
| epoch   3 |  1000/ 1505 batches | lr 4.51 | ms/batch 16.99 | loss  5.96 | ppl   386.63
| epoch   3 |  1200/ 1505 batches | lr 4.51 | ms/batch 17.02 | loss  5.96 | ppl   388.95
| epoch   3 |  1400/ 1505 batches | lr 4.51 | ms/batch 17.01 | loss  5.95 | ppl   384.29
-----------------------------------------------------------------------------------------
| end of epoch   3 | time: 26.65s | valid loss  5.88 | valid ppl   357.28
-----------------------------------------------------------------------------------------
```

Efter 10 epochs
```text
Tokenizer:  char
/tmp/ipykernel_2272576/388721432.py:9: UserWarning: enable_nested_tensor is True, but self.use_nested_tensor is False because encoder_layer.self_attn.batch_first was not True(use batch_first for better inference performance)
  self.transformer_encoder = TransformerEncoder(encoder_layers, nlayers)
Total num parameters:  6426344
| epoch   1 |   200/ 3452 batches | lr 5.00 | ms/batch 12.09 | loss  5.63 | ppl   278.21
| epoch   1 |   400/ 3452 batches | lr 5.00 | ms/batch 10.52 | loss  4.21 | ppl    67.62
| epoch   1 |   600/ 3452 batches | lr 5.00 | ms/batch 10.51 | loss  3.92 | ppl    50.36
| epoch   1 |   800/ 3452 batches | lr 5.00 | ms/batch 10.52 | loss  3.76 | ppl    42.76
| epoch   1 |  1000/ 3452 batches | lr 5.00 | ms/batch 10.52 | loss  3.68 | ppl    39.48
| epoch   1 |  1200/ 3452 batches | lr 5.00 | ms/batch 10.53 | loss  3.65 | ppl    38.31
| epoch   1 |  1400/ 3452 batches | lr 5.00 | ms/batch 10.55 | loss  3.71 | ppl    40.98
| epoch   1 |  1600/ 3452 batches | lr 5.00 | ms/batch 10.56 | loss  3.64 | ppl    38.25
| epoch   1 |  1800/ 3452 batches | lr 5.00 | ms/batch 10.56 | loss  3.60 | ppl    36.77
| epoch   1 |  2000/ 3452 batches | lr 5.00 | ms/batch 10.57 | loss  3.56 | ppl    35.30
| epoch   1 |  2200/ 3452 batches | lr 5.00 | ms/batch 10.57 | loss  3.54 | ppl    34.49
| epoch   1 |  2400/ 3452 batches | lr 5.00 | ms/batch 10.59 | loss  3.52 | ppl    33.63
| epoch   1 |  2600/ 3452 batches | lr 5.00 | ms/batch 10.58 | loss  3.50 | ppl    33.08
| epoch   1 |  2800/ 3452 batches | lr 5.00 | ms/batch 10.59 | loss  3.48 | ppl    32.47
| epoch   1 |  3000/ 3452 batches | lr 5.00 | ms/batch 10.59 | loss  3.46 | ppl    31.95
| epoch   1 |  3200/ 3452 batches | lr 5.00 | ms/batch 10.61 | loss  3.46 | ppl    31.85
| epoch   1 |  3400/ 3452 batches | lr 5.00 | ms/batch 10.60 | loss  3.44 | ppl    31.24
-----------------------------------------------------------------------------------------
| end of epoch   1 | time: 38.40s | valid loss  3.30 | valid ppl    27.09
-----------------------------------------------------------------------------------------
| epoch   2 |   200/ 3452 batches | lr 4.75 | ms/batch 10.68 | loss  3.31 | ppl    27.34
| epoch   2 |   400/ 3452 batches | lr 4.75 | ms/batch 10.62 | loss  3.29 | ppl    26.83
| epoch   2 |   600/ 3452 batches | lr 4.75 | ms/batch 10.62 | loss  3.28 | ppl    26.51
| epoch   2 |   800/ 3452 batches | lr 4.75 | ms/batch 10.62 | loss  3.28 | ppl    26.62
| epoch   2 |  1000/ 3452 batches | lr 4.75 | ms/batch 10.63 | loss  3.29 | ppl    26.84
| epoch   2 |  1200/ 3452 batches | lr 4.75 | ms/batch 10.64 | loss  3.32 | ppl    27.67
| epoch   2 |  1400/ 3452 batches | lr 4.75 | ms/batch 10.64 | loss  3.44 | ppl    31.14
| epoch   2 |  1600/ 3452 batches | lr 4.75 | ms/batch 10.64 | loss  3.44 | ppl    31.09
| epoch   2 |  1800/ 3452 batches | lr 4.75 | ms/batch 10.64 | loss  3.45 | ppl    31.38
| epoch   2 |  2000/ 3452 batches | lr 4.75 | ms/batch 10.64 | loss  3.44 | ppl    31.34
| epoch   2 |  2200/ 3452 batches | lr 4.75 | ms/batch 10.64 | loss  3.45 | ppl    31.54
| epoch   2 |  2400/ 3452 batches | lr 4.75 | ms/batch 10.65 | loss  3.45 | ppl    31.56
| epoch   2 |  2600/ 3452 batches | lr 4.75 | ms/batch 10.65 | loss  3.45 | ppl    31.39
| epoch   2 |  2800/ 3452 batches | lr 4.75 | ms/batch 10.65 | loss  3.43 | ppl    30.91
| epoch   2 |  3000/ 3452 batches | lr 4.75 | ms/batch 10.65 | loss  3.43 | ppl    30.94
| epoch   2 |  3200/ 3452 batches | lr 4.75 | ms/batch 10.66 | loss  3.43 | ppl    30.93
| epoch   2 |  3400/ 3452 batches | lr 4.75 | ms/batch 10.67 | loss  3.41 | ppl    30.41
-----------------------------------------------------------------------------------------
| end of epoch   2 | time: 38.39s | valid loss  3.33 | valid ppl    28.02
-----------------------------------------------------------------------------------------
| epoch   3 |   200/ 3452 batches | lr 4.51 | ms/batch 10.71 | loss  3.29 | ppl    26.92
| epoch   3 |   400/ 3452 batches | lr 4.51 | ms/batch 10.67 | loss  3.27 | ppl    26.28
| epoch   3 |   600/ 3452 batches | lr 4.51 | ms/batch 10.67 | loss  3.26 | ppl    26.05
| epoch   3 |   800/ 3452 batches | lr 4.51 | ms/batch 10.67 | loss  3.27 | ppl    26.19
| epoch   3 |  1000/ 3452 batches | lr 4.51 | ms/batch 10.67 | loss  3.25 | ppl    25.89
| epoch   3 |  1200/ 3452 batches | lr 4.51 | ms/batch 10.67 | loss  3.27 | ppl    26.25
| epoch   3 |  1400/ 3452 batches | lr 4.51 | ms/batch 10.68 | loss  3.38 | ppl    29.26
| epoch   3 |  1600/ 3452 batches | lr 4.51 | ms/batch 10.68 | loss  3.36 | ppl    28.65
| epoch   3 |  1800/ 3452 batches | lr 4.51 | ms/batch 10.68 | loss  3.36 | ppl    28.70
| epoch   3 |  2000/ 3452 batches | lr 4.51 | ms/batch 10.68 | loss  3.35 | ppl    28.50
| epoch   3 |  2200/ 3452 batches | lr 4.51 | ms/batch 10.69 | loss  3.35 | ppl    28.53
| epoch   3 |  2400/ 3452 batches | lr 4.51 | ms/batch 10.69 | loss  3.34 | ppl    28.32
| epoch   3 |  2600/ 3452 batches | lr 4.51 | ms/batch 10.69 | loss  3.34 | ppl    28.24
| epoch   3 |  2800/ 3452 batches | lr 4.51 | ms/batch 10.70 | loss  3.34 | ppl    28.17
| epoch   3 |  3000/ 3452 batches | lr 4.51 | ms/batch 10.70 | loss  3.34 | ppl    28.23
| epoch   3 |  3200/ 3452 batches | lr 4.51 | ms/batch 10.70 | loss  3.36 | ppl    28.91
| epoch   3 |  3400/ 3452 batches | lr 4.51 | ms/batch 10.71 | loss  3.32 | ppl    27.78
-----------------------------------------------------------------------------------------
| end of epoch   3 | time: 38.53s | valid loss  3.21 | valid ppl    24.77
-----------------------------------------------------------------------------------------
| epoch   4 |   200/ 3452 batches | lr 4.29 | ms/batch 10.75 | loss  3.21 | ppl    24.76
| epoch   4 |   400/ 3452 batches | lr 4.29 | ms/batch 10.70 | loss  3.18 | ppl    24.03
| epoch   4 |   600/ 3452 batches | lr 4.29 | ms/batch 10.71 | loss  3.18 | ppl    23.94
| epoch   4 |   800/ 3452 batches | lr 4.29 | ms/batch 10.70 | loss  3.17 | ppl    23.89
| epoch   4 |  1000/ 3452 batches | lr 4.29 | ms/batch 10.70 | loss  3.17 | ppl    23.77
| epoch   4 |  1200/ 3452 batches | lr 4.29 | ms/batch 10.70 | loss  3.23 | ppl    25.30
| epoch   4 |  1400/ 3452 batches | lr 4.29 | ms/batch 10.70 | loss  3.31 | ppl    27.40
| epoch   4 |  1600/ 3452 batches | lr 4.29 | ms/batch 10.71 | loss  3.30 | ppl    27.00
| epoch   4 |  1800/ 3452 batches | lr 4.29 | ms/batch 10.71 | loss  3.29 | ppl    26.87
| epoch   4 |  2000/ 3452 batches | lr 4.29 | ms/batch 10.71 | loss  3.29 | ppl    26.74
| epoch   4 |  2200/ 3452 batches | lr 4.29 | ms/batch 10.73 | loss  3.30 | ppl    27.06
| epoch   4 |  2400/ 3452 batches | lr 4.29 | ms/batch 10.73 | loss  3.29 | ppl    26.91
| epoch   4 |  2600/ 3452 batches | lr 4.29 | ms/batch 10.73 | loss  3.29 | ppl    26.81
| epoch   4 |  2800/ 3452 batches | lr 4.29 | ms/batch 10.74 | loss  3.30 | ppl    27.19
| epoch   4 |  3000/ 3452 batches | lr 4.29 | ms/batch 10.74 | loss  3.30 | ppl    27.08
| epoch   4 |  3200/ 3452 batches | lr 4.29 | ms/batch 10.75 | loss  3.28 | ppl    26.66
| epoch   4 |  3400/ 3452 batches | lr 4.29 | ms/batch 10.74 | loss  3.29 | ppl    26.90
-----------------------------------------------------------------------------------------
| end of epoch   4 | time: 38.66s | valid loss  3.12 | valid ppl    22.67
-----------------------------------------------------------------------------------------
| epoch   5 |   200/ 3452 batches | lr 4.07 | ms/batch 10.79 | loss  3.16 | ppl    23.57
| epoch   5 |   400/ 3452 batches | lr 4.07 | ms/batch 10.75 | loss  3.14 | ppl    23.19
| epoch   5 |   600/ 3452 batches | lr 4.07 | ms/batch 10.75 | loss  3.14 | ppl    23.07
| epoch   5 |   800/ 3452 batches | lr 4.07 | ms/batch 10.75 | loss  3.13 | ppl    22.95
| epoch   5 |  1000/ 3452 batches | lr 4.07 | ms/batch 10.75 | loss  3.14 | ppl    23.10
| epoch   5 |  1200/ 3452 batches | lr 4.07 | ms/batch 10.75 | loss  3.17 | ppl    23.80
| epoch   5 |  1400/ 3452 batches | lr 4.07 | ms/batch 10.74 | loss  3.28 | ppl    26.56
| epoch   5 |  1600/ 3452 batches | lr 4.07 | ms/batch 10.75 | loss  3.27 | ppl    26.27
| epoch   5 |  1800/ 3452 batches | lr 4.07 | ms/batch 10.75 | loss  3.28 | ppl    26.67
| epoch   5 |  2000/ 3452 batches | lr 4.07 | ms/batch 10.77 | loss  3.26 | ppl    25.99
| epoch   5 |  2200/ 3452 batches | lr 4.07 | ms/batch 10.75 | loss  3.28 | ppl    26.54
| epoch   5 |  2400/ 3452 batches | lr 4.07 | ms/batch 10.75 | loss  3.33 | ppl    28.07
| epoch   5 |  2600/ 3452 batches | lr 4.07 | ms/batch 10.76 | loss  3.31 | ppl    27.25
| epoch   5 |  2800/ 3452 batches | lr 4.07 | ms/batch 10.75 | loss  3.28 | ppl    26.61
| epoch   5 |  3000/ 3452 batches | lr 4.07 | ms/batch 10.76 | loss  3.29 | ppl    26.77
| epoch   5 |  3200/ 3452 batches | lr 4.07 | ms/batch 10.76 | loss  3.31 | ppl    27.37
| epoch   5 |  3400/ 3452 batches | lr 4.07 | ms/batch 10.76 | loss  3.28 | ppl    26.46
-----------------------------------------------------------------------------------------
| end of epoch   5 | time: 38.78s | valid loss  3.10 | valid ppl    22.28
-----------------------------------------------------------------------------------------
| epoch   6 |   200/ 3452 batches | lr 3.87 | ms/batch 10.79 | loss  3.15 | ppl    23.30
| epoch   6 |   400/ 3452 batches | lr 3.87 | ms/batch 10.75 | loss  3.16 | ppl    23.48
| epoch   6 |   600/ 3452 batches | lr 3.87 | ms/batch 10.75 | loss  3.16 | ppl    23.49
| epoch   6 |   800/ 3452 batches | lr 3.87 | ms/batch 10.74 | loss  3.17 | ppl    23.72
| epoch   6 |  1000/ 3452 batches | lr 3.87 | ms/batch 10.74 | loss  3.14 | ppl    23.12
| epoch   6 |  1200/ 3452 batches | lr 3.87 | ms/batch 10.75 | loss  3.17 | ppl    23.92
| epoch   6 |  1400/ 3452 batches | lr 3.87 | ms/batch 10.75 | loss  3.25 | ppl    25.88
| epoch   6 |  1600/ 3452 batches | lr 3.87 | ms/batch 10.75 | loss  3.25 | ppl    25.70
| epoch   6 |  1800/ 3452 batches | lr 3.87 | ms/batch 10.75 | loss  3.26 | ppl    26.16
| epoch   6 |  2000/ 3452 batches | lr 3.87 | ms/batch 10.75 | loss  3.26 | ppl    25.96
| epoch   6 |  2200/ 3452 batches | lr 3.87 | ms/batch 10.76 | loss  3.26 | ppl    26.02
| epoch   6 |  2400/ 3452 batches | lr 3.87 | ms/batch 10.76 | loss  3.26 | ppl    26.16
| epoch   6 |  2600/ 3452 batches | lr 3.87 | ms/batch 10.76 | loss  3.30 | ppl    27.23
| epoch   6 |  2800/ 3452 batches | lr 3.87 | ms/batch 10.76 | loss  3.26 | ppl    26.04
| epoch   6 |  3000/ 3452 batches | lr 3.87 | ms/batch 10.75 | loss  3.24 | ppl    25.56
| epoch   6 |  3200/ 3452 batches | lr 3.87 | ms/batch 10.76 | loss  3.24 | ppl    25.61
| epoch   6 |  3400/ 3452 batches | lr 3.87 | ms/batch 10.76 | loss  3.24 | ppl    25.66
-----------------------------------------------------------------------------------------
| end of epoch   6 | time: 38.78s | valid loss  3.05 | valid ppl    21.03
-----------------------------------------------------------------------------------------
| epoch   7 |   200/ 3452 batches | lr 3.68 | ms/batch 10.80 | loss  3.16 | ppl    23.60
| epoch   7 |   400/ 3452 batches | lr 3.68 | ms/batch 10.77 | loss  3.13 | ppl    22.96
| epoch   7 |   600/ 3452 batches | lr 3.68 | ms/batch 10.77 | loss  3.12 | ppl    22.58
| epoch   7 |   800/ 3452 batches | lr 3.68 | ms/batch 10.76 | loss  3.13 | ppl    22.82
| epoch   7 |  1000/ 3452 batches | lr 3.68 | ms/batch 10.76 | loss  3.12 | ppl    22.64
| epoch   7 |  1200/ 3452 batches | lr 3.68 | ms/batch 10.75 | loss  3.17 | ppl    23.79
| epoch   7 |  1400/ 3452 batches | lr 3.68 | ms/batch 10.76 | loss  3.24 | ppl    25.55
| epoch   7 |  1600/ 3452 batches | lr 3.68 | ms/batch 10.76 | loss  3.21 | ppl    24.75
| epoch   7 |  1800/ 3452 batches | lr 3.68 | ms/batch 10.76 | loss  3.24 | ppl    25.53
| epoch   7 |  2000/ 3452 batches | lr 3.68 | ms/batch 10.76 | loss  3.23 | ppl    25.21
| epoch   7 |  2200/ 3452 batches | lr 3.68 | ms/batch 10.76 | loss  3.23 | ppl    25.34
| epoch   7 |  2400/ 3452 batches | lr 3.68 | ms/batch 10.76 | loss  3.24 | ppl    25.57
| epoch   7 |  2600/ 3452 batches | lr 3.68 | ms/batch 10.76 | loss  3.23 | ppl    25.27
| epoch   7 |  2800/ 3452 batches | lr 3.68 | ms/batch 10.76 | loss  3.25 | ppl    25.83
| epoch   7 |  3000/ 3452 batches | lr 3.68 | ms/batch 10.76 | loss  3.26 | ppl    26.05
| epoch   7 |  3200/ 3452 batches | lr 3.68 | ms/batch 10.76 | loss  3.24 | ppl    25.64
| epoch   7 |  3400/ 3452 batches | lr 3.68 | ms/batch 10.76 | loss  3.24 | ppl    25.50
-----------------------------------------------------------------------------------------
| end of epoch   7 | time: 38.81s | valid loss  3.08 | valid ppl    21.77
-----------------------------------------------------------------------------------------
| epoch   8 |   200/ 3452 batches | lr 3.49 | ms/batch 10.82 | loss  3.13 | ppl    22.84
| epoch   8 |   400/ 3452 batches | lr 3.49 | ms/batch 10.76 | loss  3.09 | ppl    22.02
| epoch   8 |   600/ 3452 batches | lr 3.49 | ms/batch 10.77 | loss  3.11 | ppl    22.33
| epoch   8 |   800/ 3452 batches | lr 3.49 | ms/batch 10.76 | loss  3.06 | ppl    21.29
| epoch   8 |  1000/ 3452 batches | lr 3.49 | ms/batch 10.76 | loss  3.08 | ppl    21.86
| epoch   8 |  1200/ 3452 batches | lr 3.49 | ms/batch 10.77 | loss  3.12 | ppl    22.69
| epoch   8 |  1400/ 3452 batches | lr 3.49 | ms/batch 10.76 | loss  3.20 | ppl    24.57
| epoch   8 |  1600/ 3452 batches | lr 3.49 | ms/batch 10.76 | loss  3.21 | ppl    24.73
| epoch   8 |  1800/ 3452 batches | lr 3.49 | ms/batch 10.76 | loss  3.25 | ppl    25.81
| epoch   8 |  2000/ 3452 batches | lr 3.49 | ms/batch 10.76 | loss  3.19 | ppl    24.17
| epoch   8 |  2200/ 3452 batches | lr 3.49 | ms/batch 10.77 | loss  3.18 | ppl    24.08
| epoch   8 |  2400/ 3452 batches | lr 3.49 | ms/batch 10.76 | loss  3.18 | ppl    24.03
| epoch   8 |  2600/ 3452 batches | lr 3.49 | ms/batch 10.79 | loss  3.21 | ppl    24.74
| epoch   8 |  2800/ 3452 batches | lr 3.49 | ms/batch 10.77 | loss  3.19 | ppl    24.32
| epoch   8 |  3000/ 3452 batches | lr 3.49 | ms/batch 10.77 | loss  3.20 | ppl    24.54
| epoch   8 |  3200/ 3452 batches | lr 3.49 | ms/batch 10.77 | loss  3.19 | ppl    24.37
| epoch   8 |  3400/ 3452 batches | lr 3.49 | ms/batch 10.76 | loss  3.23 | ppl    25.31
-----------------------------------------------------------------------------------------
| end of epoch   8 | time: 38.83s | valid loss  3.04 | valid ppl    20.90
-----------------------------------------------------------------------------------------
| epoch   9 |   200/ 3452 batches | lr 3.32 | ms/batch 10.79 | loss  3.07 | ppl    21.51
| epoch   9 |   400/ 3452 batches | lr 3.32 | ms/batch 10.76 | loss  3.06 | ppl    21.33
| epoch   9 |   600/ 3452 batches | lr 3.32 | ms/batch 10.75 | loss  3.04 | ppl    20.87
| epoch   9 |   800/ 3452 batches | lr 3.32 | ms/batch 10.76 | loss  3.07 | ppl    21.59
| epoch   9 |  1000/ 3452 batches | lr 3.32 | ms/batch 10.76 | loss  3.09 | ppl    22.04
| epoch   9 |  1200/ 3452 batches | lr 3.32 | ms/batch 10.76 | loss  3.12 | ppl    22.54
| epoch   9 |  1400/ 3452 batches | lr 3.32 | ms/batch 10.76 | loss  3.21 | ppl    24.67
| epoch   9 |  1600/ 3452 batches | lr 3.32 | ms/batch 10.76 | loss  3.18 | ppl    23.99
| epoch   9 |  1800/ 3452 batches | lr 3.32 | ms/batch 10.76 | loss  3.17 | ppl    23.88
| epoch   9 |  2000/ 3452 batches | lr 3.32 | ms/batch 10.76 | loss  3.18 | ppl    24.01
| epoch   9 |  2200/ 3452 batches | lr 3.32 | ms/batch 10.76 | loss  3.19 | ppl    24.28
| epoch   9 |  2400/ 3452 batches | lr 3.32 | ms/batch 10.76 | loss  3.17 | ppl    23.92
| epoch   9 |  2600/ 3452 batches | lr 3.32 | ms/batch 10.76 | loss  3.19 | ppl    24.25
| epoch   9 |  2800/ 3452 batches | lr 3.32 | ms/batch 10.76 | loss  3.17 | ppl    23.75
| epoch   9 |  3000/ 3452 batches | lr 3.32 | ms/batch 10.76 | loss  3.16 | ppl    23.64
| epoch   9 |  3200/ 3452 batches | lr 3.32 | ms/batch 10.76 | loss  3.23 | ppl    25.41
| epoch   9 |  3400/ 3452 batches | lr 3.32 | ms/batch 10.76 | loss  3.16 | ppl    23.51
-----------------------------------------------------------------------------------------
| end of epoch   9 | time: 38.79s | valid loss  2.98 | valid ppl    19.76
-----------------------------------------------------------------------------------------
| epoch  10 |   200/ 3452 batches | lr 3.15 | ms/batch 10.80 | loss  3.04 | ppl    20.92
| epoch  10 |   400/ 3452 batches | lr 3.15 | ms/batch 10.75 | loss  3.04 | ppl    20.86
| epoch  10 |   600/ 3452 batches | lr 3.15 | ms/batch 10.77 | loss  3.04 | ppl    20.87
| epoch  10 |   800/ 3452 batches | lr 3.15 | ms/batch 10.76 | loss  3.05 | ppl    21.04
| epoch  10 |  1000/ 3452 batches | lr 3.15 | ms/batch 10.76 | loss  3.08 | ppl    21.82
| epoch  10 |  1200/ 3452 batches | lr 3.15 | ms/batch 10.78 | loss  3.07 | ppl    21.57
| epoch  10 |  1400/ 3452 batches | lr 3.15 | ms/batch 10.75 | loss  3.17 | ppl    23.79
| epoch  10 |  1600/ 3452 batches | lr 3.15 | ms/batch 10.76 | loss  3.15 | ppl    23.36
| epoch  10 |  1800/ 3452 batches | lr 3.15 | ms/batch 10.75 | loss  3.16 | ppl    23.60
| epoch  10 |  2000/ 3452 batches | lr 3.15 | ms/batch 10.75 | loss  3.14 | ppl    23.05
| epoch  10 |  2200/ 3452 batches | lr 3.15 | ms/batch 10.76 | loss  3.20 | ppl    24.47
| epoch  10 |  2400/ 3452 batches | lr 3.15 | ms/batch 10.75 | loss  3.15 | ppl    23.32
| epoch  10 |  2600/ 3452 batches | lr 3.15 | ms/batch 10.75 | loss  3.15 | ppl    23.25
| epoch  10 |  2800/ 3452 batches | lr 3.15 | ms/batch 10.75 | loss  3.17 | ppl    23.76
| epoch  10 |  3000/ 3452 batches | lr 3.15 | ms/batch 10.76 | loss  3.17 | ppl    23.72
| epoch  10 |  3200/ 3452 batches | lr 3.15 | ms/batch 10.75 | loss  3.14 | ppl    23.03
| epoch  10 |  3400/ 3452 batches | lr 3.15 | ms/batch 10.75 | loss  3.17 | ppl    23.70
-----------------------------------------------------------------------------------------
| end of epoch  10 | time: 38.79s | valid loss  2.98 | valid ppl    19.63
-----------------------------------------------------------------------------------------
Tokenizer:  bpe_small
/tmp/ipykernel_2272576/388721432.py:9: UserWarning: enable_nested_tensor is True, but self.use_nested_tensor is False because encoder_layer.self_attn.batch_first was not True(use batch_first for better inference performance)
  self.transformer_encoder = TransformerEncoder(encoder_layers, nlayers)
Total num parameters:  7735520
| epoch   1 |   200/ 1823 batches | lr 5.00 | ms/batch 12.57 | loss  8.02 | ppl  3034.16
| epoch   1 |   400/ 1823 batches | lr 5.00 | ms/batch 12.20 | loss  6.91 | ppl  1005.51
| epoch   1 |   600/ 1823 batches | lr 5.00 | ms/batch 12.20 | loss  6.34 | ppl   569.04
| epoch   1 |   800/ 1823 batches | lr 5.00 | ms/batch 12.19 | loss  6.15 | ppl   468.34
| epoch   1 |  1000/ 1823 batches | lr 5.00 | ms/batch 12.20 | loss  5.92 | ppl   372.13
| epoch   1 |  1200/ 1823 batches | lr 5.00 | ms/batch 12.19 | loss  5.77 | ppl   321.15
| epoch   1 |  1400/ 1823 batches | lr 5.00 | ms/batch 12.19 | loss  5.66 | ppl   286.45
| epoch   1 |  1600/ 1823 batches | lr 5.00 | ms/batch 12.20 | loss  5.59 | ppl   267.13
| epoch   1 |  1800/ 1823 batches | lr 5.00 | ms/batch 12.19 | loss  5.53 | ppl   251.87
-----------------------------------------------------------------------------------------
| end of epoch   1 | time: 23.26s | valid loss  5.40 | valid ppl   221.65
-----------------------------------------------------------------------------------------
| epoch   2 |   200/ 1823 batches | lr 4.75 | ms/batch 12.25 | loss  5.43 | ppl   228.44
| epoch   2 |   400/ 1823 batches | lr 4.75 | ms/batch 12.19 | loss  5.37 | ppl   214.56
| epoch   2 |   600/ 1823 batches | lr 4.75 | ms/batch 12.19 | loss  5.32 | ppl   205.12
| epoch   2 |   800/ 1823 batches | lr 4.75 | ms/batch 12.20 | loss  5.35 | ppl   210.13
| epoch   2 |  1000/ 1823 batches | lr 4.75 | ms/batch 12.19 | loss  5.32 | ppl   205.39
| epoch   2 |  1200/ 1823 batches | lr 4.75 | ms/batch 12.19 | loss  5.30 | ppl   199.98
| epoch   2 |  1400/ 1823 batches | lr 4.75 | ms/batch 12.20 | loss  5.27 | ppl   193.47
| epoch   2 |  1600/ 1823 batches | lr 4.75 | ms/batch 12.20 | loss  5.26 | ppl   191.76
| epoch   2 |  1800/ 1823 batches | lr 4.75 | ms/batch 12.20 | loss  5.23 | ppl   187.71
-----------------------------------------------------------------------------------------
| end of epoch   2 | time: 23.20s | valid loss  5.16 | valid ppl   174.04
-----------------------------------------------------------------------------------------
| epoch   3 |   200/ 1823 batches | lr 4.51 | ms/batch 12.26 | loss  5.19 | ppl   178.66
| epoch   3 |   400/ 1823 batches | lr 4.51 | ms/batch 12.21 | loss  5.15 | ppl   171.88
| epoch   3 |   600/ 1823 batches | lr 4.51 | ms/batch 12.21 | loss  5.13 | ppl   168.25
| epoch   3 |   800/ 1823 batches | lr 4.51 | ms/batch 12.21 | loss  5.17 | ppl   175.29
| epoch   3 |  1000/ 1823 batches | lr 4.51 | ms/batch 12.22 | loss  5.16 | ppl   173.86
| epoch   3 |  1200/ 1823 batches | lr 4.51 | ms/batch 12.21 | loss  5.15 | ppl   171.79
| epoch   3 |  1400/ 1823 batches | lr 4.51 | ms/batch 12.20 | loss  5.12 | ppl   167.92
| epoch   3 |  1600/ 1823 batches | lr 4.51 | ms/batch 12.21 | loss  5.12 | ppl   167.48
| epoch   3 |  1800/ 1823 batches | lr 4.51 | ms/batch 12.21 | loss  5.11 | ppl   165.49
-----------------------------------------------------------------------------------------
| end of epoch   3 | time: 23.22s | valid loss  5.05 | valid ppl   155.57
-----------------------------------------------------------------------------------------
| epoch   4 |   200/ 1823 batches | lr 4.29 | ms/batch 12.27 | loss  5.07 | ppl   159.84
| epoch   4 |   400/ 1823 batches | lr 4.29 | ms/batch 12.21 | loss  5.04 | ppl   155.07
| epoch   4 |   600/ 1823 batches | lr 4.29 | ms/batch 12.20 | loss  5.03 | ppl   152.54
| epoch   4 |   800/ 1823 batches | lr 4.29 | ms/batch 12.21 | loss  5.07 | ppl   159.39
| epoch   4 |  1000/ 1823 batches | lr 4.29 | ms/batch 12.20 | loss  5.07 | ppl   159.22
| epoch   4 |  1200/ 1823 batches | lr 4.29 | ms/batch 12.20 | loss  5.06 | ppl   158.24
| epoch   4 |  1400/ 1823 batches | lr 4.29 | ms/batch 12.21 | loss  5.04 | ppl   154.59
| epoch   4 |  1600/ 1823 batches | lr 4.29 | ms/batch 12.20 | loss  5.04 | ppl   155.22
| epoch   4 |  1800/ 1823 batches | lr 4.29 | ms/batch 12.20 | loss  5.04 | ppl   154.11
-----------------------------------------------------------------------------------------
| end of epoch   4 | time: 23.22s | valid loss  4.99 | valid ppl   146.74
-----------------------------------------------------------------------------------------
| epoch   5 |   200/ 1823 batches | lr 4.07 | ms/batch 12.30 | loss  5.01 | ppl   149.41
| epoch   5 |   400/ 1823 batches | lr 4.07 | ms/batch 12.21 | loss  4.98 | ppl   145.58
| epoch   5 |   600/ 1823 batches | lr 4.07 | ms/batch 12.20 | loss  4.97 | ppl   143.78
| epoch   5 |   800/ 1823 batches | lr 4.07 | ms/batch 12.20 | loss  5.01 | ppl   150.42
| epoch   5 |  1000/ 1823 batches | lr 4.07 | ms/batch 12.21 | loss  5.01 | ppl   150.59
| epoch   5 |  1200/ 1823 batches | lr 4.07 | ms/batch 12.21 | loss  5.01 | ppl   150.04
| epoch   5 |  1400/ 1823 batches | lr 4.07 | ms/batch 12.21 | loss  4.99 | ppl   146.71
| epoch   5 |  1600/ 1823 batches | lr 4.07 | ms/batch 12.21 | loss  4.99 | ppl   147.63
| epoch   5 |  1800/ 1823 batches | lr 4.07 | ms/batch 12.21 | loss  4.99 | ppl   146.45
-----------------------------------------------------------------------------------------
| end of epoch   5 | time: 23.23s | valid loss  4.96 | valid ppl   143.18
-----------------------------------------------------------------------------------------
| epoch   6 |   200/ 1823 batches | lr 3.87 | ms/batch 12.28 | loss  4.96 | ppl   142.98
| epoch   6 |   400/ 1823 batches | lr 3.87 | ms/batch 12.22 | loss  4.94 | ppl   139.40
| epoch   6 |   600/ 1823 batches | lr 3.87 | ms/batch 12.22 | loss  4.93 | ppl   138.00
| epoch   6 |   800/ 1823 batches | lr 3.87 | ms/batch 12.22 | loss  4.97 | ppl   144.43
| epoch   6 |  1000/ 1823 batches | lr 3.87 | ms/batch 12.22 | loss  4.98 | ppl   144.97
| epoch   6 |  1200/ 1823 batches | lr 3.87 | ms/batch 12.22 | loss  4.97 | ppl   144.19
| epoch   6 |  1400/ 1823 batches | lr 3.87 | ms/batch 12.23 | loss  4.95 | ppl   141.34
| epoch   6 |  1600/ 1823 batches | lr 3.87 | ms/batch 12.23 | loss  4.96 | ppl   142.10
| epoch   6 |  1800/ 1823 batches | lr 3.87 | ms/batch 12.23 | loss  4.95 | ppl   140.99
-----------------------------------------------------------------------------------------
| end of epoch   6 | time: 23.25s | valid loss  4.93 | valid ppl   138.33
-----------------------------------------------------------------------------------------
| epoch   7 |   200/ 1823 batches | lr 3.68 | ms/batch 12.27 | loss  4.93 | ppl   138.03
| epoch   7 |   400/ 1823 batches | lr 3.68 | ms/batch 12.23 | loss  4.90 | ppl   134.81
| epoch   7 |   600/ 1823 batches | lr 3.68 | ms/batch 12.22 | loss  4.89 | ppl   133.39
| epoch   7 |   800/ 1823 batches | lr 3.68 | ms/batch 12.21 | loss  4.94 | ppl   139.41
| epoch   7 |  1000/ 1823 batches | lr 3.68 | ms/batch 12.21 | loss  4.94 | ppl   139.93
| epoch   7 |  1200/ 1823 batches | lr 3.68 | ms/batch 12.21 | loss  4.94 | ppl   139.72
| epoch   7 |  1400/ 1823 batches | lr 3.68 | ms/batch 12.24 | loss  4.92 | ppl   137.12
| epoch   7 |  1600/ 1823 batches | lr 3.68 | ms/batch 12.21 | loss  4.92 | ppl   137.58
| epoch   7 |  1800/ 1823 batches | lr 3.68 | ms/batch 12.22 | loss  4.92 | ppl   137.23
-----------------------------------------------------------------------------------------
| end of epoch   7 | time: 23.24s | valid loss  4.91 | valid ppl   135.73
-----------------------------------------------------------------------------------------
| epoch   8 |   200/ 1823 batches | lr 3.49 | ms/batch 12.26 | loss  4.90 | ppl   133.89
| epoch   8 |   400/ 1823 batches | lr 3.49 | ms/batch 12.21 | loss  4.87 | ppl   130.96
| epoch   8 |   600/ 1823 batches | lr 3.49 | ms/batch 12.21 | loss  4.86 | ppl   129.65
| epoch   8 |   800/ 1823 batches | lr 3.49 | ms/batch 12.21 | loss  4.91 | ppl   135.50
| epoch   8 |  1000/ 1823 batches | lr 3.49 | ms/batch 12.21 | loss  4.91 | ppl   136.17
| epoch   8 |  1200/ 1823 batches | lr 3.49 | ms/batch 12.21 | loss  4.91 | ppl   135.75
| epoch   8 |  1400/ 1823 batches | lr 3.49 | ms/batch 12.21 | loss  4.89 | ppl   133.28
| epoch   8 |  1600/ 1823 batches | lr 3.49 | ms/batch 12.21 | loss  4.90 | ppl   133.84
| epoch   8 |  1800/ 1823 batches | lr 3.49 | ms/batch 12.21 | loss  4.89 | ppl   132.99
-----------------------------------------------------------------------------------------
| end of epoch   8 | time: 23.23s | valid loss  4.89 | valid ppl   133.06
-----------------------------------------------------------------------------------------
| epoch   9 |   200/ 1823 batches | lr 3.32 | ms/batch 12.26 | loss  4.87 | ppl   130.49
| epoch   9 |   400/ 1823 batches | lr 3.32 | ms/batch 12.21 | loss  4.85 | ppl   127.48
| epoch   9 |   600/ 1823 batches | lr 3.32 | ms/batch 12.21 | loss  4.84 | ppl   126.50
| epoch   9 |   800/ 1823 batches | lr 3.32 | ms/batch 12.21 | loss  4.88 | ppl   132.02
| epoch   9 |  1000/ 1823 batches | lr 3.32 | ms/batch 12.21 | loss  4.89 | ppl   132.41
| epoch   9 |  1200/ 1823 batches | lr 3.32 | ms/batch 12.22 | loss  4.88 | ppl   132.13
| epoch   9 |  1400/ 1823 batches | lr 3.32 | ms/batch 12.21 | loss  4.87 | ppl   129.98
| epoch   9 |  1600/ 1823 batches | lr 3.32 | ms/batch 12.21 | loss  4.87 | ppl   130.28
| epoch   9 |  1800/ 1823 batches | lr 3.32 | ms/batch 12.21 | loss  4.86 | ppl   129.61
-----------------------------------------------------------------------------------------
| end of epoch   9 | time: 23.23s | valid loss  4.88 | valid ppl   131.12
-----------------------------------------------------------------------------------------
| epoch  10 |   200/ 1823 batches | lr 3.15 | ms/batch 12.28 | loss  4.85 | ppl   127.47
| epoch  10 |   400/ 1823 batches | lr 3.15 | ms/batch 12.22 | loss  4.82 | ppl   124.25
| epoch  10 |   600/ 1823 batches | lr 3.15 | ms/batch 12.26 | loss  4.81 | ppl   123.28
| epoch  10 |   800/ 1823 batches | lr 3.15 | ms/batch 12.23 | loss  4.86 | ppl   128.83
| epoch  10 |  1000/ 1823 batches | lr 3.15 | ms/batch 12.23 | loss  4.86 | ppl   129.29
| epoch  10 |  1200/ 1823 batches | lr 3.15 | ms/batch 12.22 | loss  4.86 | ppl   129.08
| epoch  10 |  1400/ 1823 batches | lr 3.15 | ms/batch 12.21 | loss  4.84 | ppl   126.70
| epoch  10 |  1600/ 1823 batches | lr 3.15 | ms/batch 12.21 | loss  4.85 | ppl   127.17
| epoch  10 |  1800/ 1823 batches | lr 3.15 | ms/batch 12.22 | loss  4.84 | ppl   126.30
-----------------------------------------------------------------------------------------
| end of epoch  10 | time: 23.25s | valid loss  4.85 | valid ppl   127.94
-----------------------------------------------------------------------------------------
Tokenizer:  bpe_large
/tmp/ipykernel_2272576/388721432.py:9: UserWarning: enable_nested_tensor is True, but self.use_nested_tensor is False because encoder_layer.self_attn.batch_first was not True(use batch_first for better inference performance)
  self.transformer_encoder = TransformerEncoder(encoder_layers, nlayers)
Total num parameters:  11839520
| epoch   1 |   200/ 1505 batches | lr 5.00 | ms/batch 17.45 | loss  8.95 | ppl  7675.50
| epoch   1 |   400/ 1505 batches | lr 5.00 | ms/batch 17.01 | loss  8.11 | ppl  3334.56
| epoch   1 |   600/ 1505 batches | lr 5.00 | ms/batch 17.03 | loss  7.76 | ppl  2342.96
| epoch   1 |   800/ 1505 batches | lr 5.00 | ms/batch 17.04 | loss  7.46 | ppl  1743.35
| epoch   1 |  1000/ 1505 batches | lr 5.00 | ms/batch 17.04 | loss  7.25 | ppl  1405.40
| epoch   1 |  1200/ 1505 batches | lr 5.00 | ms/batch 17.05 | loss  7.13 | ppl  1245.41
| epoch   1 |  1400/ 1505 batches | lr 5.00 | ms/batch 17.03 | loss  6.97 | ppl  1066.14
-----------------------------------------------------------------------------------------
| end of epoch   1 | time: 26.79s | valid loss  6.74 | valid ppl   848.04
-----------------------------------------------------------------------------------------
| epoch   2 |   200/ 1505 batches | lr 4.75 | ms/batch 17.11 | loss  6.72 | ppl   827.09
| epoch   2 |   400/ 1505 batches | lr 4.75 | ms/batch 17.03 | loss  6.57 | ppl   714.15
| epoch   2 |   600/ 1505 batches | lr 4.75 | ms/batch 17.03 | loss  6.47 | ppl   647.36
| epoch   2 |   800/ 1505 batches | lr 4.75 | ms/batch 17.02 | loss  6.40 | ppl   601.42
| epoch   2 |  1000/ 1505 batches | lr 4.75 | ms/batch 17.02 | loss  6.31 | ppl   551.38
| epoch   2 |  1200/ 1505 batches | lr 4.75 | ms/batch 17.04 | loss  6.30 | ppl   542.17
| epoch   2 |  1400/ 1505 batches | lr 4.75 | ms/batch 17.04 | loss  6.25 | ppl   516.06
-----------------------------------------------------------------------------------------
| end of epoch   2 | time: 26.72s | valid loss  6.15 | valid ppl   467.61
-----------------------------------------------------------------------------------------
| epoch   3 |   200/ 1505 batches | lr 4.51 | ms/batch 17.11 | loss  6.13 | ppl   460.77
| epoch   3 |   400/ 1505 batches | lr 4.51 | ms/batch 17.04 | loss  6.06 | ppl   427.64
| epoch   3 |   600/ 1505 batches | lr 4.51 | ms/batch 17.03 | loss  6.02 | ppl   410.42
| epoch   3 |   800/ 1505 batches | lr 4.51 | ms/batch 17.04 | loss  6.00 | ppl   402.36
| epoch   3 |  1000/ 1505 batches | lr 4.51 | ms/batch 17.03 | loss  5.95 | ppl   384.88
| epoch   3 |  1200/ 1505 batches | lr 4.51 | ms/batch 17.03 | loss  5.96 | ppl   389.23
| epoch   3 |  1400/ 1505 batches | lr 4.51 | ms/batch 17.04 | loss  5.95 | ppl   383.33
-----------------------------------------------------------------------------------------
| end of epoch   3 | time: 26.73s | valid loss  5.90 | valid ppl   366.51
-----------------------------------------------------------------------------------------
| epoch   4 |   200/ 1505 batches | lr 4.29 | ms/batch 17.11 | loss  5.88 | ppl   357.48
| epoch   4 |   400/ 1505 batches | lr 4.29 | ms/batch 17.04 | loss  5.83 | ppl   339.39
| epoch   4 |   600/ 1505 batches | lr 4.29 | ms/batch 17.04 | loss  5.80 | ppl   330.57
| epoch   4 |   800/ 1505 batches | lr 4.29 | ms/batch 17.04 | loss  5.79 | ppl   328.12
| epoch   4 |  1000/ 1505 batches | lr 4.29 | ms/batch 17.05 | loss  5.77 | ppl   319.15
| epoch   4 |  1200/ 1505 batches | lr 4.29 | ms/batch 17.04 | loss  5.78 | ppl   325.00
| epoch   4 |  1400/ 1505 batches | lr 4.29 | ms/batch 17.02 | loss  5.78 | ppl   322.53
-----------------------------------------------------------------------------------------
| end of epoch   4 | time: 26.74s | valid loss  5.78 | valid ppl   324.00
-----------------------------------------------------------------------------------------
| epoch   5 |   200/ 1505 batches | lr 4.07 | ms/batch 17.11 | loss  5.73 | ppl   308.62
| epoch   5 |   400/ 1505 batches | lr 4.07 | ms/batch 17.03 | loss  5.68 | ppl   294.27
| epoch   5 |   600/ 1505 batches | lr 4.07 | ms/batch 17.04 | loss  5.66 | ppl   288.46
| epoch   5 |   800/ 1505 batches | lr 4.07 | ms/batch 17.03 | loss  5.66 | ppl   287.71
| epoch   5 |  1000/ 1505 batches | lr 4.07 | ms/batch 17.04 | loss  5.64 | ppl   281.55
| epoch   5 |  1200/ 1505 batches | lr 4.07 | ms/batch 17.04 | loss  5.66 | ppl   287.55
| epoch   5 |  1400/ 1505 batches | lr 4.07 | ms/batch 17.03 | loss  5.66 | ppl   286.49
-----------------------------------------------------------------------------------------
| end of epoch   5 | time: 26.73s | valid loss  5.71 | valid ppl   301.39
-----------------------------------------------------------------------------------------
| epoch   6 |   200/ 1505 batches | lr 3.87 | ms/batch 17.10 | loss  5.63 | ppl   277.36
| epoch   6 |   400/ 1505 batches | lr 3.87 | ms/batch 17.02 | loss  5.58 | ppl   265.18
| epoch   6 |   600/ 1505 batches | lr 3.87 | ms/batch 17.03 | loss  5.56 | ppl   260.64
| epoch   6 |   800/ 1505 batches | lr 3.87 | ms/batch 17.02 | loss  5.56 | ppl   261.02
| epoch   6 |  1000/ 1505 batches | lr 3.87 | ms/batch 17.04 | loss  5.55 | ppl   256.07
| epoch   6 |  1200/ 1505 batches | lr 3.87 | ms/batch 17.03 | loss  5.57 | ppl   261.85
| epoch   6 |  1400/ 1505 batches | lr 3.87 | ms/batch 17.03 | loss  5.57 | ppl   261.46
-----------------------------------------------------------------------------------------
| end of epoch   6 | time: 26.72s | valid loss  5.66 | valid ppl   286.19
-----------------------------------------------------------------------------------------
| epoch   7 |   200/ 1505 batches | lr 3.68 | ms/batch 17.12 | loss  5.54 | ppl   254.50
| epoch   7 |   400/ 1505 batches | lr 3.68 | ms/batch 17.06 | loss  5.50 | ppl   243.74
| epoch   7 |   600/ 1505 batches | lr 3.68 | ms/batch 17.03 | loss  5.48 | ppl   240.07
| epoch   7 |   800/ 1505 batches | lr 3.68 | ms/batch 17.02 | loss  5.48 | ppl   240.73
| epoch   7 |  1000/ 1505 batches | lr 3.68 | ms/batch 17.02 | loss  5.47 | ppl   236.68
| epoch   7 |  1200/ 1505 batches | lr 3.68 | ms/batch 17.03 | loss  5.49 | ppl   242.42
| epoch   7 |  1400/ 1505 batches | lr 3.68 | ms/batch 17.03 | loss  5.49 | ppl   242.32
-----------------------------------------------------------------------------------------
| end of epoch   7 | time: 26.73s | valid loss  5.63 | valid ppl   279.60
-----------------------------------------------------------------------------------------
| epoch   8 |   200/ 1505 batches | lr 3.49 | ms/batch 17.11 | loss  5.47 | ppl   237.39
| epoch   8 |   400/ 1505 batches | lr 3.49 | ms/batch 17.03 | loss  5.43 | ppl   227.92
| epoch   8 |   600/ 1505 batches | lr 3.49 | ms/batch 17.04 | loss  5.41 | ppl   224.23
| epoch   8 |   800/ 1505 batches | lr 3.49 | ms/batch 17.04 | loss  5.42 | ppl   225.01
| epoch   8 |  1000/ 1505 batches | lr 3.49 | ms/batch 17.04 | loss  5.40 | ppl   221.92
| epoch   8 |  1200/ 1505 batches | lr 3.49 | ms/batch 17.03 | loss  5.42 | ppl   226.90
| epoch   8 |  1400/ 1505 batches | lr 3.49 | ms/batch 17.03 | loss  5.43 | ppl   227.16
-----------------------------------------------------------------------------------------
| end of epoch   8 | time: 26.73s | valid loss  5.60 | valid ppl   270.66
-----------------------------------------------------------------------------------------
| epoch   9 |   200/ 1505 batches | lr 3.32 | ms/batch 17.08 | loss  5.41 | ppl   223.32
| epoch   9 |   400/ 1505 batches | lr 3.32 | ms/batch 17.03 | loss  5.37 | ppl   214.84
| epoch   9 |   600/ 1505 batches | lr 3.32 | ms/batch 17.03 | loss  5.36 | ppl   211.77
| epoch   9 |   800/ 1505 batches | lr 3.32 | ms/batch 17.02 | loss  5.36 | ppl   212.47
| epoch   9 |  1000/ 1505 batches | lr 3.32 | ms/batch 17.04 | loss  5.34 | ppl   209.33
| epoch   9 |  1200/ 1505 batches | lr 3.32 | ms/batch 17.02 | loss  5.37 | ppl   214.30
| epoch   9 |  1400/ 1505 batches | lr 3.32 | ms/batch 17.02 | loss  5.37 | ppl   214.89
-----------------------------------------------------------------------------------------
| end of epoch   9 | time: 26.71s | valid loss  5.58 | valid ppl   264.02
-----------------------------------------------------------------------------------------
| epoch  10 |   200/ 1505 batches | lr 3.15 | ms/batch 17.09 | loss  5.36 | ppl   211.76
| epoch  10 |   400/ 1505 batches | lr 3.15 | ms/batch 17.03 | loss  5.32 | ppl   203.75
| epoch  10 |   600/ 1505 batches | lr 3.15 | ms/batch 17.02 | loss  5.30 | ppl   201.30
| epoch  10 |   800/ 1505 batches | lr 3.15 | ms/batch 17.03 | loss  5.31 | ppl   201.86
| epoch  10 |  1000/ 1505 batches | lr 3.15 | ms/batch 17.02 | loss  5.29 | ppl   199.06
| epoch  10 |  1200/ 1505 batches | lr 3.15 | ms/batch 17.02 | loss  5.32 | ppl   203.58
| epoch  10 |  1400/ 1505 batches | lr 3.15 | ms/batch 17.03 | loss  5.32 | ppl   204.54
-----------------------------------------------------------------------------------------
| end of epoch  10 | time: 26.71s | valid loss  5.57 | valid ppl   261.71
-----------------------------------------------------------------------------------------
```

## 2026-10-03 lördag

Insåg att deadline för checkpoint-inlämning var i torsdags. Får skicka in något i alla fall innan slutinlämningen imorgon.

Länkar:
* https://huggingface.co/datasets/bird-of-paradise/transformer-from-scratch-tutorial/blob/main/Transformer_Implementation_Tutorial.ipynb
* https://pytorch-tutorials-preview.netlify.app/beginner/transformer_tutorial.html

## 2026-10-02 fredag

```
Failed to load JSON from file '/srv/data/lt2326-h26/a1/train/en.txt' with error <class 'pyarrow.lib.ArrowInvalid'>: JSON parse error: Invalid value. in row 0
```

Anledning: missade att sätta "text" när jag anropade load_dataset().

```
TypeError: 'DatasetDict' object is not an instance of 'Sequence'
while processing 'files'
```

Anledning: Använda load_dataset, men borde bara ha laddat in filerna as-is (och bara train-filerna). 

### Förtokeniserare

* Hur tokeniserar man kinesiska?
Verkar vara *SentencePiece* som gäller: https://huggingface.co/learn/llm-course/en/chapter6/4

* https://huggingface.co/docs/tokenizers/en/api/pre-tokenizers
* https://huggingface.co/docs/tokenizers/python/latest/components.html#pre-tokenizers


### Python environment
* `pip install datasets` 

---------------------------------------------

## 2026-10-01 torsdag

### Data

`/srv/data/lt2326-h26/a1/`

```
guserbto@GU.GU.SE@mltgpu:/srv/data/lt2326-h26/a1/tokenizer$ cat balanced.txt | head -10
But French people use the word county (comté) in the name of the Free County region, the old Free County of Burgundy.
Daha sonra buna ek olarak Angel yayın yapmaya başlamıştır.
Formül aynı zamanda gözlemlenemeyen morötesi ve kızılötesi ışıkların bazı ek spektral çizgilerini tahmin etmiştir.
İGD Dış Bürosu tarafından 1980'li yıllarda yayınlanan haber bülteni Türkçenin yanı sıra İngilizce ve Fransızca olarak da çıkmıştır.
Bu durum sayesinde düşmanlarından gizlenir.
The Po river view from Torino.
Beş yıl süren müzakerelerin ana konusu boru hattı güzergâhını belirlemekdi ve 17 Aralık 2013 tarihinde Azerbaycan'ın Bakü kentinde Nihai Yatırım Kararının (FID) imzalanmasıyla sonuçlandı.
現今王小雲担任山東大學密码技术与信息安全教育部重点实验室主任，清华大学密码理论与技术研究中心主任，同时兼任中国密码学会密码数学理论专业委员会主任 。
Bu birleşme Filipinler'deki ilk gazete birleşmesidir.
```

"You may use an existing implementation such as SentencePiece or the Hugging Face tokenizers library."


### Hugginface tokenizers
* https://huggingface.co/docs/tokenizers/en/index

### Python environment
* `python -m venv .venv`
* `source .venv/bin/activate`
* `pip install --upgrade pip`
* `pip install matplotlib torch jupyter` 
* `python -m ipykernel install --user --name ml2_a1_ht26`
* `pip install tokenizers`
* `pip install transformers`



