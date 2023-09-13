---
title: "Large Language Models History"
seoDescription: "Explore the history of language models, from rule-based to large-scale models like ChatGPT, and their impact on natural language processing tasks"
datePublished: Wed Sep 13 2023 18:30:09 GMT+0000 (Coordinated Universal Time)
cuid: clmi2u1em000w09mr23zmg72p
slug: large-language-models-history
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694628384133/cc93e1c3-854c-4656-a133-404b4d626a89.png
tags: nlp, llm, languagemodelling, large-language-models

---

## What are Language Models?

A language model (LM) is a tool that guesses the next word in a given sequence of terms.

## Evolution of Language Models

The development of LMs can be broadly classified into five stages.

1. Rule-based LM
    
2. Statistical LM
    
3. Neural LM
    
4. Pre-Trained LM
    
5. Large Language Models (LLM)
    

### Rule-based Language Models

* Grammatical rules of a specific language were used to predict the next word in a sentence.
    
* E.g., in English `I` will be followed by `am` not `are`, and `They` can be followed by `have` or `are` like these grammatical rules.
    
* However, there are many exceptions, and handling all the language rules is tricky.
    

### Statistical Language Models

* In this method, a large set of texts was analyzed, and the word-level probability of a word after a bunch of words was determined statistically.
    
* How many times does `am` appear after `I` that probability is compared with other words like `are` or `is`.
    
* In an advanced SLM n-gram model, instead of finding probability from a previous single word, the last bi-gram (two words) and tri-grams (three terms) were used to find the possibility of the next word.
    
* However, In English, a single word can have multiple meanings based on the context of the sentence. SLM can not able to determine the context of the sentence.
    

### Neural Language Models

* With Word2Vec (Word to Vector), these models calculate the probability of the following words by neural networks.
    
* Example: RNN (Recurrent Neural Network), LSTM (Long Short Term Memory)
    

### Pre-Trained Language Models

* ELMo (Context-aware Word Embedding) and Self-Attention through Transformer architecture raised the performance bar of NLP tasks. Example: BERT and GPT-2
    
* Models were trained with a large amount of text, and the context awareness increased.
    

### Large Language Models (LLM)

* There is a thin line between PLM and LLM.
    
* Scaling model size and training data size of PLMs new emergent abilities of model discovered. Example: ChatGPT, LLaMA, Claude
    
* LLM is different from PLM broadly in three ways:
    
    * Emergent abilities
        
    * Prompting/Conversational Interface
        
    * To attend the scale, Engineering and Research problems must be solved.
        

## References

1. [Language Models in Plain English (](https://learning.oreilly.com/library/view/language-models-in/9781098109073/)[oreilly.com](http://oreilly.com)[)](https://learning.oreilly.com/library/view/language-models-in/9781098109073/)
    
2. [\[2303.18223\] A Survey of Large Language Models (](https://arxiv.org/abs/2303.18223)[arxiv.org](http://arxiv.org)[)](https://arxiv.org/abs/2303.18223)