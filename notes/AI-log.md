# AI log

Prompt:

Why do I get this error when trying to load my tokenization data with load_dataset():

TypeError                                 Traceback (most recent call last)
Cell In[42], line 1
----> 1 tokenizer.train(wiki_data, trainer)

TypeError: 'DatasetDict' object is not an instance of 'Sequence'
while processing 'files'

Why: See error in prompt.

Incorporated as: Changed to "simple" import by reading file paths as array.



