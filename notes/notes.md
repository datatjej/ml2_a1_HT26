# Notes

## 2026-10-03 söndag

## 2026-10-03 lördag

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



