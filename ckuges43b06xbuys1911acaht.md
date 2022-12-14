# Odia language detection

## Abstract

I could not find a suitable language detection library for the [Odia language](https://en.wikipedia.org/wiki/Odia_language). Around 45 million people speak Odia, majorly based out of one of the eastern states of India.

I have attempted to develop a language detection tool for the Odia language. When given a text of words or sentences, it should be able to provide whether the text is provided in Odia or any other language.

There is no AI or ML involved in this library. Instead, basic Python programming is used with a little bit of probability to get the result.

```python
# pip install openodia
>>> from openodia import ud
>>> ud.detect_language("hey how are you?")
{'language': 'non-odia', 'confidence_score': 1.0}

>>> ud.detect_language("ନ୍ୟାଚୁରାଲ ଲାଙ୍ଗୁଏଜ ପ୍ରୋସେସିଂ ବା ପ୍ରାକୃତିକ ଭାଷା ପ୍ରକ୍ରିୟାକରଣ କଂପ୍ୟୁଟର ବିଜ୍ଞାନ ଏବଂ ଆର୍ଟିଫିସିଆଲ ଇଣ୍ଟେଲିଜେନ୍ସର ସେହି ବିଭାଗକୁ କୁହାଯ ାଏ ଯାହା ମନୁଷ୍ୟର ଭାଷାଗୁଡ଼ିକ ସହ କମ୍ପ୍ୟୁଟରର କଥାବାର୍ତ୍ତାକୁ ବୁଝାଇଥାଏ। ")
{'language': 'odia', 'confidence_score': 0.99404}
```
## Requirement

I have started with the bare minimum requirements.

- Given an input text, find out whether the text is in Odia or Non-Odia

## Design

The following initial flow thought of

1. User will provide the input text
2. Iterate over all the letters
3. Check the letter is Odia letter or not
4. If a single Odia letter is found, return as Odia text found

This initial flow of thought is good to start with but does not make any sense for practical use of the language detector. 
- For example, if a text has 100 letters and one letter is Odia, we can not say the text is in Odia language.
- Therefore, I came up with the plan to incorporate a confidence score in the output, which will suggest how confident the program is that it is Odia language. 

### Confidence score calculation

- If there are 100 letters in a text and 80 letters are found to be in Odia language, then the program returns it as Odia language with the confidence score of 80/100 = 0.8. 
- The confidence score suggests that the program is 80% sure that the given text is in Odia language.
- If there are 20 Odia letters found, then the program suggests that it is non-Odia text with a confidence score of 0.8, calculated as:

20/100 = 0.2   
1 - 0.2 = 0.8  

- If Odia letters appear more than 50%, the program regarded it as Odia text. 
- However, this may not be the case always; depending upon the use cases; we may need to increase the matching Odia letters to a higher percentage. 
- Thus, I have introduced another parameter called, **Threshold**.

### Threshold

- The Threshold is used to set a limit in the confidence score, after which the confidence score of the given text will be regarded as Odia language. 
- E.g., if you set the Threshold to 0.9, that means if there are more than 90% of Odia letters in the given input text, then only the given input text will be regarded as Odia language.
- This may be confusing a bit, let's try to understand by one example:

```python
>>> ud.detect_language("hey how are you? ନ୍ୟାଚୁରାଲ ଲାଙ୍ଗୁଏଜ ପ୍ରୋସେସିଂ")
{'language': 'odia', 'confidence_score': 0.67}

>>> ud.detect_language("hey how are you? ନ୍ୟାଚୁରାଲ ଲାଙ୍ଗୁଏଜ ପ୍ରୋସେସିଂ", threshold=0.7)
{'language': 'non-odia', 'confidence_score': 0.33}
```

- In the first example, we saw the confidence score is 0.67, which means 67% of the given text are in the Odia language.
- However, in the second example, we increased the Threshold to 0.7, i.e. when 70% of the given input text will be Odia letters, the input text will be regarded as Odia language.
- As the confidence score is less than 0.7, in return, we got the language as 'non-Odia'. 
- However, as you can see, the confidence score is not 0.67 anymore. It is 0.33.
- That means the program is in 33% confidence that the given input text is non-Odia language.

The made language detector is an essential and fast Odia language detector, without any fancy AI/ML. It works.  

## References

- To know more about the `OpenOdia` library please visit: https://openodia.soumendrak.com/
- To know other Open-source projects on Odia language, please visit https://www.mte2o.com

ଧନ୍ୟବାଦ । 
ଜୟ ଜଗନ୍ନାଥ 🙏🏼 

<!-- Citation -->
<hr>
If you find this article helpful or influential please consider citing:

```bibtex
@inproceedings{OdiaLanguageDetection,
    author       = {Soumendra Kumar Sahoo},
    title        = {Odia language detection by Soumendra Kumar Sahoo},
    howpublished = {\url{https://blog.soumendrak.com/odia-language-detection}},
    year         = {2021}
}
```

-----

Let me know what you think at any of the following places:

- 🔗 LinkedIn: https://www.linkedin.com/in/soumendrak/
- 📝 Medium: https://medium.com/@soumendrak
- 📖 Blog: https://blog.soumendrak.com/
- 🐥 Twitter: https://twitter.com/soumendrak_
- 🧑🏻‍💻 Github: https://github.com/soumendrak
- 📹 Youtube: https://www.youtube.com/@openodia