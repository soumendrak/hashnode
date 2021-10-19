## Random Odia Name Generator

*This article was first published on the [OpenOdia application page](https://openodia.soumendrak.com/application/)*
## Generate Odia names

- Using the [Odia names generation package](https://openodia.soumendrak.com/#odia-names) you can create **lakhs of unique** Odia names.


```python
from openodia import name
name.generate_names(20)
'''
['ସାବିତ୍ରୀ ଧଳ', 'ଶ୍ରୀଯୁକ୍ତ ଉତ୍କଳ ପାଳ', 'ଯଦୁମଣି ସୁବାହୁ', 'ପ୍ରେମଲତା ପମ', 'ଗୁରୁ ପୃଷ୍ଟି', 
 'ଗୀତା ଦାସବର୍ମା', 'କୁମାରୀ ଦୁର୍ଗା ବ୍ରହ୍ମା', 'କୁମାରୀ ପୁପୁଲ ହେମ୍ବ୍ରମ', 'ମକର ସାଇ', 'ଲକ୍ଷ୍ମୀକାନ୍ତ ନନ୍ଦି', 
 'ଶ୍ରୀ ଦୀନବନ୍ଧୁ ଲୋକ', 'କୁମାରୀ ଜିନା ଗଜପତି', 'ମୃଣାଳ ଭୂଷଣ ଛତ୍ରିଆ', 'ସୁଧାଂଶୁମାଳିନୀ ସିଂହ ସାଲୁଜା', 'ସୁଧାଂଶୁମାଳିନୀ ମହାନନ୍ଦ', 
 'ସୁମନୀ ନାଥ', 'କୁମାରୀ ନୀତୁ ହିକ୍କା', 'ଶ୍ରୀମତୀ ଲୀଳା କାଡାମ୍', 'ସନାତନ କୁଅଁର', 'କୁମାରୀ କବି ଦାସନାୟକ']
'''
```


### Data Masking

- As these names database has been taken from Wikipedia and actual person names in Odisha, you can use these as NER for person name recognition.
- In data engineering projects when you need to ingest a large amount of data, you need to mask or anonymize the PI (Personal Identification) data from the data source.
- This is to remove bias and increase privacy on your data/model.

#### Masking names: 

- To avoid disrupting the privacy of individuals, you can identify the names of people in the text and 
- Replace the names with a masked tag like `<name>`.
- Example:
    - `ବୈଦ୍ୟନାଥ ସିଂହଦେଓ ବାବୁ ସସ୍ତ୍ରୀକ ନିଜ କାରରେ ବସି ପୁରୀ ବୁଲିଯାଇଛନ୍ତି ।` has potential personal data that which a person can derive like:
        1. `ବୈଦ୍ୟନାଥ ସିଂହଦେଓ` is married.
        2. `ବୈଦ୍ୟନାଥ ସିଂହଦେଓ` is male.
        3. He has a car.
        4. He is in Puri.
    - To avoid this kind of personal privacy exposure, we need to mask the text to `<name> ବାବୁ ସସ୍ତ୍ରୀକ ନିଜ କାରରେ ବସି ପୁରୀ ବୁଲିଯାଇଛନ୍ତି ।`
- The problem with this method is you miss the credibility of an important feature of the input data. As there is no uniqueness among the name field.

#### Anonymization of names:

- Using this method rather than completely removing all names with a `<name>` tag you can substitute with a fake name.
- It maintains the uniqueness of the name field.
- However, in many cases, you may need to revert back to the original person name after a certain operation has been completed. That's not possible as anonymization is an irreversible procedure.
- Example
    - `ବୈଦ୍ୟନାଥ ସିଂହଦେଓ ବାବୁ ସସ୍ତ୍ରୀକ ନିଜ କାରରେ ବସି ପୁରୀ ବୁଲିଯାଇଛନ୍ତି ।` will be anonymized as `ବ୍ରଜମୋହନ ପଣ୍ଡା ବାବୁ ସସ୍ତ୍ରୀକ ନିଜ କାରରେ ବସି ପୁରୀ ବୁଲିଯାଇଛନ୍ତି ।` 
    - Did you notice how `ବୈଦ୍ୟନାଥ ସିଂହଦେଓ` has changed to `ବ୍ରଜମୋହନ ପଣ୍ଡା`?
- Here are some situations in which you may want to use anonymization:[^1]
    - If you no longer need to communicate or work with a consumer, but wish to archive their activity, order history, or any other details that could not be used to identify them.
    - To perform data analyses that are unrelated to the services you provide the consumer.
    - If you need to make data available to a group of people outside those that are designated to fulfil your services, such as a wide group of employees or consultants.


#### Pseudonimization of names:

- This is the same as anonymization, with the only difference that, the anonymized names can be replaced with their original names.
- Example
    - `ବୈଦ୍ୟନାଥ ସିଂହଦେଓ ବାବୁ ସସ୍ତ୍ରୀକ ନିଜ କାରରେ ବସି ପୁରୀ ବୁଲିଯାଇଛନ୍ତି ।` will be pseudonymized as `hrtvd6wqbvs4320 ବାବୁ ସସ୍ତ୍ରୀକ ନିଜ କାରରେ ବସି ପୁରୀ ବୁଲିଯାଇଛନ୍ତି ।` 
    - Did you notice how `ବୈଦ୍ୟନାଥ ସିଂହଦେଓ` has changed to `hrtvd6wqbvs4320`?
    - Here `hrtvd6wqbvs4320` has shown as a demonstration of a key, which can be stored in a hash table with value as `ବୈଦ୍ୟନାଥ ସିଂହଦେଓ`.
    - This text can be further reversed by referring to this hash table or a unique private key.
- Data pseudonymization can be used when you will need to re-identify users in the future:[^1]
    - To keep data secure during the fulfilment of services, by masking identifying details to employees or other data handlers that do not need those details.
    - To maintain data protection within your database or records, order histories, and inactive customers that you remain in contact with.
    - To transfer data over international borders.
    - To maintain data protection and Privacy by Design principles laid out by the [GDPR](https://gdpr.eu/).



<!-- Citation -->
<hr>
If you find this page useful, please cite this using:

```bibtex
@misc{OpenOdia,
    author       = {Soumendra Kumar Sahoo},
    title        = {Random Name Generator in Odia},
    howpublished = {\url{https://www.openodia.soumendrak.com/}},
    year         = {2021}
}
```

[^1]: https://www.termsfeed.com/blog/gdpr-pseudonymization-anonymization/
