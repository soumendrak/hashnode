## Extracting Parallel-text pairs from Wikipedia


I was able to extract almost 15,000 English (en) to Odia (or) parallel text pairs from Wikipedia. Millions can be extracted for a well-resourced language.

## Translation Tool of Wikipedia does not do the auto translation for Odia

Wikipedia has got its own [Translation tool](https://en.wikipedia.org/wiki/Wikipedia:Translation), by which you can translate an Article from one language to another. Mostly it uses [Google Translator API](https://en.wikipedia.org/wiki/Google_Translator_Toolkit) to convert the sentences in near real-time. However, some of the unfortunate languages like Odia, where Google translate is not available yet, you have to translate manually.

## Paragraph Alignment

After an Editor, translate an Article, the good thing about the tool is that it manages to keep alignment between the paragraphs of source and destination language. However, it may not be always accurate. Quoting text from the [*MediaWiki* page](https://www.mediawiki.org/wiki/Content_translation/Published_translations#Parallel%20corpora):
> Content Translation does not do any kind of automatic alignment and the provided alignment is only best effort based on how the connections were preserved while translation happens. When automatically aligning the sentences, it is good to remember that the translations do not necessarily match 1:1.

## Weekly data dump

Wikipedia maintains a weekly dump of the articles created through this Translation tool. Which can be accessed [here](https://dumps.wikimedia.org/other/contenttranslation/). Once you find your interested language pairs you will find parallel text in both tmx and JSON format to download the data.

In the JSON format of the dump you will get the pairs in this structure:

```
{
        "id": "116954/mwVw",
        "sourceLanguage": "en",
        "targetLanguage": "or",
        "source": {
            "content": "References"
        },
        "mt": null,
        "target": {
            "content": "ଆଧାର"
        }
},
```


The keys are self-explanatory. ‘mt’ stands for Machine Translation.

I have decided to keep the format as a text file where the structure will be like below. As this structure will help me see the bigger picture in a single file with a provision to manually adding sentences.

```
<source content>||<target content>
References||ଆଧାର
```


## Custom code

I have written custom code to

* Do data validation and

* Extract the output on the above specific format

```
import json
import pandas as pd


from collections import defaultdict as dd
from character_mapping import MATRA # Odia language specific

# path varibales
import os
input_data_path = os.path.join(os.path.dirname(os.getcwd()), 'data', 'input')
output_data_path = os.path.join(os.path.dirname(os.getcwd()), 'data', 'output')
wiki_file_path = os.path.join(input_data_path, 'cx-corpora.en2or.text_May_2019.json')

# File got from, https://dumps.wikimedia.org/other/contenttranslation/
with open(wiki_file_path, 'r', encoding='utf-8') as json_file:
    json_data = json.loads(json_file.read())
```


The necessary files/libraries are imported and the paths were provided.

```
MATRA = {
    "ଁ", "ଂ", "ଃ", "଼", "ଽ", "ା", "ି", "ୀ", "ୁ", "ୂ", "ୃ", "ୄ", "େ", "ୈ", "ୋ", "ୌ", "୍", "ୖ", "ୗ", "୰", "ୱ", "୲"
    }
```


The *character_mapping* file contains the Matras of Odia language which are mandatory even to form a single word. The content of the file is provided above.

```
pd_dict = dd(list)
for each_dict in json_data:
    try:
        or_content = each_dict.get('target', 'NA').get('content', '')
        if any(matra in or_content for matra in MATRA) and or_content.strip() != "+ ଅନୁବାଦ ଯୋଗକରନ୍ତୁ":
            pd_dict[each_dict.get('sourceLanguage', 'NA')].append(each_dict.get('source', 'NA').get('content', ''))
            pd_dict[each_dict.get('targetLanguage', 'NA')].append(or_content)
    except Exception as error_message:
        print("Getting some issues while encoding need to look deeper", error_message)
```


In the above code snippet, the *en* and *or* pairs are separated out. We check the existence of a valid Odia sentence before going ahead with the pair.

```
def find_punctuation_marks(text):
    if any('"' in text or ',' in text or "'" in text):
        return True

  df = df.drop(df[df['en'].astype('str').map(len) > 30].index)
  df = new_df.drop(new_df[new_df['or'].astype('str').map(len) > 50].index)
  df = new_df.drop(new_df[new_df['or'].astype('str').map(finding_punctuation_marks)].index)
```


The punctuation marks sentences are dropped out (which is omitting many useful sentences, I need to recheck this part). Any pair with less than 30 *en* sentence characters length and 50 for *or* are dropped. This is done by analyzing the pairs, where lesser length pairs were not so useful. Generally, due to *Matras,* a transliterated Odia text gets more number of characters than English.

```
df = pd.DataFrame(data=pd_dict)
df.drop_duplicates(keep="last", inplace=True)
```


The duplicate pairs are removed and an intermediate file has been saved.

```
df['piped'] = df['en'] + '||' + d['or']  *# pairs are joined*
df.to_csv(output_file_location)
```


The pairs are joined by double pipes and dumped into a CSV file. I got around 10k pairs. However, the quality of the pairs are not accurate and manual review is needed currently. Around 4000 pairs have been created with manual review and consolidating few other corpora.

## Open-source source code

The code is written on Python in Jupyter notebook and detail work are open-sourced and available for researchers, students and interested people in [this Github repository](https://soumendrak.github.io/MTEnglish2Odia/). The 4000+ reviewed pairs are currently hosted at the [Odia Wikimedia organization](https://github.com/OdiaWikimedia) in [this Github repository](https://github.com/OdiaWikimedia/English-Odia).

## Conclusion

There has been a minimal footprint of Odia language over the Internet. The [Odia Wikipedia](http://or.wikipedia.org/) is the only project available which has a large Odia CC-licensed text and will be useful for future Linguists, Researchers, Students, etc.

In addition to Odia, there are about 190 languages are available for download including Hindi, Telugu, Tamil, Bangla, Kannada, Spanish, Portuguese, etc.

## Related Work

* On July 26, 2019, Facebook Research team has published [an article](https://ai.facebook.com/blog/wikimatrix/), where they have extracted 135 million sentences in 1,620 language pairs (Odia is not there :( ) using Distance-based mining approach (Schwenk, 2018; Artetxe and Schwenk, 2018a).

## Future Scope

This is an ongoing project. There is a scope of doing the following activities:

* Collect at least 50,000 reviewed accurate parallel pairs.

* Auto-alignment of the pairs based on the word matching level; maybe using [Segtok](https://github.com/fnl/segtok).

* Prepare PoS tag and NER from Odia sentences. Extracting from [Wikidata](https://www.wikidata.org/wiki/Wikidata:Main_Page) might help.

* Splitting the pairs into dev, test sets for [Moses](http://www.statmt.org/moses/) SMT ([Statistical Machine Translation](https://en.wikipedia.org/wiki/Statistical_machine_translation)) and NMT ([Neural Machine Translation](https://en.wikipedia.org/wiki/Neural_machine_translation)).

* Developing a seq2seq translation model for the NMT.

* Combining this with Mozilla’s open-sourced [Common Voice project](https://voice.mozilla.org/en) for [Text to Speech](https://en.wikipedia.org/wiki/Speech_synthesis) in Odia.