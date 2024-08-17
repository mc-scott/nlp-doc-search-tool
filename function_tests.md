# Testing module

> Run this testing module using `python -m doctest -v function_tests.md` in the terminal to ensure all functions continue to pass the defined tests below

Import libraries and declare variables

```python
# import libraries

>>> import doctest
>>> from utils import *
>>> from nltk.corpus import stopwords
>>> nltk.download('stopwords')
True

>>> nltk.download('punkt')
True

# define test sentence
>>> text = """
...    This is a TEST sentence 
...    it will contain new line CHARACTERS,
...    miSmaTched case,    inconsistent whitespace,
...    and non-ascii charàcters ∵ I need to test it.
... """

```

## Test text cleaning functionality
Ensure basic text cleaning functionality is applied (remove line break characters, covert all words to lower case, normalise white space, remove non-ascii characters)

```python
>>> fn_text_clean(text)
'this is a test sentence it will contain new line characters, mismatched case, inconsistent whitespace, and non-ascii charcters i need to test it.'

```

Assert that stopword removal process works by checking processed string does not contain any of NLTKs 179 stopwords.

```python
>>> no_stopwords = fn_text_clean(text, rm_stopwords=True)

>>> assert stopwords.words('english') not in no_stopwords.split()

```
