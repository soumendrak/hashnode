## The story behind Shabdarasa (ଶବ୍ଦରସ)

Please check out the game here: **[www.ଶବ୍ଦରସ.com](https://ଶବ୍ଦରସ.com)**

![Screenshot 2022-01-29 at 10.30.51 AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1643432507045/oUCSsqupZ.png)

## 🤫 Approach (ଆଭିମୁଖ୍ୟ)

- On 12th Jan 2021, I have been approached by [Dr. Aviseka Acharya](https://twitter.com/aviseka) to build the game [Wordle](https://www.powerlanguage.co.uk/wordle/) in [Odia language](https://en.wikipedia.org/wiki/Odia_language) for the Odia people.
- The goal is to engage people to increase their vocabulary and appreciate the richness of the language.
- I did not have any clue of the game Wordle, other than watching people post green-yellow boxes on their Twitter handles.
- Even Dr. Aviseka did not have a clue if it can be done in Odia. Dr. Aviseka and I met once over an [Odias In ML Twitter](https://twitter.com/odias_in_ml) space. Later when I asked him what inspired him to reach out to me with this requirement. His exact response:


> 1. The way English language injecting into our kids life is becoming a threat to our own language. 
> 2. We all know how crucial a language is for state / nation 
> 3. The only way we can claim back and prosperous is with innovation , smart , easy approach with our language so game is one of them. 
> 4. I followed your work and saw your passion for odia language so I thought you may guide me.
> 5. I heard your speech in my space there I discovered your potency as well .


## 🧐 Initial analysis (ପ୍ରାରମ୍ଭିକ ବିଶ୍ଳେଷଣ)

- This is the most critical part of a project.
- This phase makes or breaks the project.
- The first thing a senior programmer does is, learn the problem and get the requirements.
- If you would have asked me 8-10 years before, the first thing I could have done is panic on getting these high-level out-of-the-blue requirements, then tried to write from scratch. **Do not be that guy.**
- I played the game multiple times (through Incognito Window) and get an idea of the algorithm behind it.
- Mind mapping the algorithms for Odia language and getting the low-level requirements.

## 🤨 Requirements gathering

After playing the game and keeping the end goal in mind, I have gathered the following requirements:


1. A specific length of words data/corpus required
2. Need to compare multiple words: position and letter
3. Letter with Matra(diacritics) and Juktakhyara(combination of multiple letters) is a challenge to compare, but let's figure it out later.
4. The sharing part should not reveal the words and their positions, but their color as done in the original game. See: [Zero-knowledge proof](https://en.wikipedia.org/wiki/Zero-knowledge_proof).
5. A keyboard to input Odia letters
6. Rest all requirements are to mimic the features, that the original game has. Those will be Add-on.


## 🕵🏻‍♀️ Haunting for existing solutions (ବିଦ୍ୟମାନ ସମାଧାନ ଖୋଜା)

- Do not reinvent the wheel.
- Where is the best way to search for code. For code, snippets search StackOverflow, but for actual working integrated code, [search GitHub](https://github.com/search?q=wordle+clone).
- From there I zeroed down on the following repos:

|Name|Usability|URL to play|GitHub|Language|Notes|
|---|---|---|---|---|---|
|Italian Wordle||https://pietroppeter.github.io/wordle-it/|https://github.com/pietroppeter/wordle-it|Javascript|Complicated JS code| but all in a single file. Do not know where he hosted it"|
|Word length customizable||http://foldr.moe/hello-wordl/|https://github.com/lynn/hello-wordl|Typescript|Not exactly clone|
|Tailwind Wordle|Medium|https://wordle.hannahmariepark.com/|https://github.com/hannahcode/wordle|"ReactJS| TailwindCSS|The best code however I do not know how to support Odia keyboard here"|
|Another clone||https://guessle.herokuapp.com/|https://github.com/jakerella/guessle|Javascript|Customizable|
|Tamil Wordle|Highest|https://tecoholic.github.io/tamil-wordle/|https://github.com/tecoholic/tamil-wordle|"Go| ReactJS"| hope it will work|
|Bulgarian wordle||https://wordle-bg.ggerganov.com/|https://github.com/ggerganov/wordle-bg|C++|Another language keyboard|
|Thai Wordle|High|https://thwordle.vercel.app/|https://github.com/narze/thwordle|Vite|Closely monitor|
|Motle||https://uk23xf.deta.dev/|Smooth deployment with deta|
|Another||https://wordle-svelte.vercel.app/|https://github.com/nijat/wordle|Svelte||
|gogoprog|Medium|https://gogoprog.github.io/motuz/src/?lang=en|https://github.com/gogoprog/motuz|Javascript|"Multilanguage support| without keyboard"|

- From day-0 the challenging part I knew will be to get an Odia keyboard.
- Most of the solutions use the default English keyboard.

### Tamil-Wordle


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1643401469305/jyoRantQAr.png)

- I have been a Python programmer, I was looking for a Python-based solution, the Tamil-wordle was written in Golang. I learned (and forgot) Golang in IBM, therefore I was a bit confident about it that I can recall the concepts and apply them. It has a backend and a frontend. 
- The front end makes calls to the backend Golang server, where the validation and verification happen.
- The main branch was based on CLI and the UI was in progress. 
- There were two UI PRs were there, One UI PR (Pull Request) was built in ReactJS, which caught my attention.
- It had a Tamil keyboard with Alternate row functionality using the Shift key i.e. in one row you can display two rows of keys. One row normal key (the vowels) and another row (the corresponding matra/diacritics) with pressing the Shift key.

#### Pros

- An Indic (Tamil) keyboard support that can be easily transformed into an Odia keyboard.
- Golang backend and ReactJS frontend I have knowledge once upon a time, I can recall once I see the code.


#### Cons

- It was not maintained seriously, no commit for 6 days. A lot of risk on future support and maintenance.
- The UI was not there and all I had to bet on was a PR, which was probably accepted by the repo owner.
- The UI PR was not exactly like the original wordle game, but far from it.

### ReactJS/Tailwind Wordle


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1643401444745/Aj0h8rLy6.png)

- This was started just 4 days before Dr. Aviseka pitched the idea to me.
- It looked promising with a clean UI.
- It was written in ReactJS typescript and Tailwind. I have some knowledge of ReactJS but not much of Typescript or Tailwind.
- However, I just have a faint memory from the [CodeWithHarry video](https://www.youtube.com/watch?v=ghZZB_7HFS8) where he explained how can we create a good looking website with Tailwind CSS in just 5 minutes.

#### Pros

- SImple clean UI; mimics the original Wordle to a large extent.



![Overall Flow.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1643433841981/qsSVIiX1M.png)

- There was no backend or server-side scripting involved. Just load the website and you are all set. No back and forth API calls I need to make.
- The repo was maintained pretty actively and got the highest stars in wordle-clone GitHub search.
- Each day one-word code changes already implemented

#### Cons

- No Odia keyboard support
- I have written many programs in Natural Language Processing in Python, but I had absolutely no idea how can I use Typescript to do text/word comparison.


### Thai-Wordle


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1643401507647/HU1x9J_pj.png)

- It was one of the first clones I had come across, where being a non-English wordle clone, the UI looked fine.
- It had a text box where you can type in the words before putting them into the boxes.
- It gave me hope that non-English wordle is possible.

#### Pros

- Many rows can be used to put non-English letter entries.
- The text box helps to type in by physical keyboard before entering into the assigned box.

#### Cons

- In a new framework called *Svelte* which I have never heard of before. Not even have the slightest clue. Googled a bit and got to know about it, but not much comfortable.
- The UI was not as beautiful as the previous Tailwind one.


## 🙋🏻‍♀️ Do we have a winner? (କେହି ବିଜେତା ମିଳିଲେ କି?)

- I have started with the Tamil Wordle first, even set up the Odia keyboard with the UI PR.
- Here is the picture:

![wordle-1.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1643402102222/HGpAETbbB.jpeg)

- The non-acceptance of this UI PR haunted me down. Every passing day the risk was getting higher and higher.
- One fine day I decided to try my hands on the Tailwind Wordle one. 
- Used the multi-key row structure from the Thai Wordle to design the keyboard. In Tamil-wordle it was taking Unicode, but here I had to give the actual value of the keys.
- It took me some time to understand why the name is **Type**script, everything you write should have a predefined type associated with it.

## 😰 Major Challenges (ପ୍ରମୁଖ ସମସ୍ୟା)

### 1. Odia Keyboard ⌨ support

Transforming the Keyboard

From
![Screenshot 2022-01-29 at 10.07.44 AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1643431133968/tKRIMchli.png)

To
![Screenshot 2022-01-29 at 10.08.13 AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1643431151281/FpSh6EqP9.png)

- There are other keyboards available for Odia but, how to highlight the key in sync with the grid box colors.
- The alignment of the keys, where to keep the consonants, the vowels the diacritics.
- My [OpenOdia project](https://openodia.soumendrak.com/) helped me get the Odia alphabet easily.
- The frequent use of Halant ('୍') diacritics made me make the key a bit larger than the other keys.

### 2. Merging diacritics into the current cell 📦

- Each key was taken as a single letter therefore, writing diacritics like *aa' kaar matra* ('ା') was written into the new cell on the grid as an independent letter.
- To merge diacritics with the non-diacritics, I have used the code snippet from [Tamil-wordle](https://github.com/tecoholic/tamil-wordle/blob/a9db5ca535c41c6babac71287a3c8135682e1ce1/ui/src/utils.js#L33)
- Directly it was not possible to use, have to modify it for Typescript.
- Also I have to make further changes to do unlimited diacritics overlap with the letters, this is to write complex letters like: 'ରାଷ୍ଟ୍ର'
- Later on, to simplify, I got rid of the diacritics Object and made it an array of strings.

```typescript
export const diacritics: string[] = [  'ଁ',  'ଂ',  'ଃ',  '଼',  'ା',  'ି',  'ୀ',  'ୁ',  'ୂ',  'ୃ',  'ୄ',  'େ',  'ୈ',  'ୋ',  'ୌ',  '୍',  'ୖ',' ୗ',
]
export function toOdiaLetters(word: string): string[] {
  // Joins Unicodes to Odia letters
  let letters = []
  for (let i = 0; i !== word.length; i++) {
    let character: string = word[i]
    if (
      (diacritics.includes(character) && letters.length) ||
      (i > 0 && word[i - 1] === '୍')
    ) {
      letters[letters.length - 1] += character
    } else letters.push(character)
  }
  return letters
}
```

- It checks if the current key pressed is a diacritic, then merges with the previous cell.
- Also if the previous key is *halant* then merges with the previous cell, to create Juktakhyara.

### 3. Writing diacritics and juktakhyara in the last box 🎁

- How to accept keyboard inputs even if all the cells are filled, creates an issue.
- After the last cell gets filled, it was not allowed to input further keys into the last cell.
- Need to debug the entire keyboard to grid flow multiple times to get this sorted.
- This looks easy, but a tricky problem to solve.

### 4. Maximum 🙆🏻‍♀️ word length

- Watching the original Wordle, we have started with 5 letter words.

![5-letters-grid.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1644338509263/keYH_zXDZ.jpeg)

![5-letters.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1644338519675/S8rAlZYWH.jpeg)

- However, within no time, we got to know it is impossible for a common person to guess the 5 letter word, even if we gave them 10 chances.
- Each letterbox can have ~50 possibilities. 5 letters 50 * 5 = 250 combinations; and with 10 chances. There is no way.
- Initial trial runs were disasters.
- Then we graded it down to 4 letter words.

![4-letter.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1644338549753/BHWZrL1iS.jpeg)
- Even with that it took us some time to figure out the word in less than 10 iterations. The possibilities are vast.
- There we realized the richness of the vocabulary of the Odia language.
_ With the letters, when we add the diacritics and Juktakhyara Odia is an advanced language to represent a larger meaning in lesser space.
- In addition to feeling proud, it was a new challenge.
- Finally, we made it down to 3 letter words.
- In all these iterations, we never had a scarcity of words. We had 28,000+ 3 letter and 4 letter words. 10,000+ 5 letter words.
- Later I added 40,000+ more 3 letter words to increase the word strength to 70,000.

### 5. Typing 👩🏻‍💻 complex juktakhyara with this keyboard

- Though I have written 140+ articles on Odia Wikipedia, still I struggle when the Google transliteration tool fails. In this keyboard, without transliteration support I agree is a challenge

### 6. Calculating 🧮 the length of a word

- The length you see in your naked eye and for a computer are different.
- While 'ବିଦ୍ରୋହ' looks like a 3 letter word.
- To computer
```typescript
>> 'ବିଦ୍ରୋହ'.length
7
```
- Which is a combination of 7 Unicode letters,  "ବ", "ି", "ଦ", "୍", "ର", "ୋ" and "ହ"
- To calculate the exact length was a challenge.

### 7. Fixing the length of the letters support 🤷🏻‍♀️
- In the original English wordle, the maximum word length was 5 to reduce it to three and make necessary changes throughout the code by removing the hardcoded values.
- As it is told, to start from scratch is easy, but to understand another developer's code and do changes is difficult. Everything has trade-offs.

### 8. Showcasing diacritics/juktakhyara mismatch 🙅🏻‍♀️ to users
- This was a no-brainer.
- Odia and almost all the Indic languages support matra/diacritics and juktakhyaras i.e. combination of two or more letters.
- How to match these multiple Unicode letters and successfully display a reliable message to user was a challenge.
- For that, I need to introduce two more colors, orange and blue.
- Even still there is scope for another three colors.

### 9. Showing hints ⚡️ to users

- It's easy to plain English wordle, there are only 26 letters so on each guess you get 5 / 26 = almost 20% letters covered.
- However, in Odia including diacritics, there are 65 keys to be entered.
- It takes more attempts (compute this)
- It does not make sense to increase the attempts, the player will be bored off by them and may leave the game. Games should bring pleasure dopamine to the player's brain.
- With alpha testing feedback, the demand was to implement some sort of hint after multiple failed attempts.
- Based on the feedback I have implemented a single letter hint if a player failed to predict a single letter on the first three attempts.

### 10. Hosting the site 🕸

- Where can I easily build and deploy the site with custom domain support.
- I tried GitLab pages, Vercel and Netlify.
- Writing script to GitLab pages I got difficulties, switched to Vercel and finally to Netlify.
- Vercel and Netlify both have one-click React deployment support.
- Got an issue with custom domain support for Vercel, that's why moved to Netlify.
- The other branch builds' URLs [can not be deleted](https://answers.netlify.com/t/how-to-delete-old-deploys/11793) in Netlify, therefore using Vercel for other branch builds (beta testing of new features) and using Netlify for production custom website support.


## Rewind ⏪

- We have gone through the motivation behind this project.
- My initial analysis to satisfy the requirements.
- The challenges faced and the solutions we traded off with.
- Major USP (Unique Selling Points) are the algorithm and the vast 71,000+ 3-letter word corpus.

## 📖 Lessons learnt (କ'ଣ ଶିଖିବାକୁ ମିଳିଲା?)

- If you have an idea and do not have the necessary skills, find someone who can make it for you.
- Sometimes you do not know if it can be done, the only way to know is by doing it.
- Programming languages are just tools to solve problems. Do not get limited by a specific tool. To solve different problems, different tools are built.
> “When something is important enough, you do it even if the odds are not in your favor.” – Elon Musk
- Emotions can make people do unimaginable things. That's what makes us human.


## 🔮 Future plans (ଭବିଷ୍ୟତ ଯୋଜନା)
- Customized game specific to Odia Bhagabata by Jagannath Das, Sarala Mahabharata, and more.
- Jumbled sentence prediction
- Children education in school
- STEAM education
- Spell correction using the words we have.
- Sentence auto-completion
- Transliteration


## ✌🏼Conclusion (ସିଦ୍ଧାନ୍ତ)

- All it took was a sincere effort towards the right direction and a lot of emotion towards your motherland.
- People should take this as an inspiration that, yes whatever can be done in English, can be done in Indic languages too, can be done in Odia too.
- It has been just 10 days and we have more than 1,700 unique users from 25+ countries. More on that later.
- Thanks for your time. Please check out the game here: [www.ଶବ୍ଦରସ.com](https://ଶବ୍ଦରସ.com)
As always, please provide your valuable feedback.
- Check out other versions of the Wordle in [Wordles of the World](https://rwmpelstilzchen.gitlab.io/wordles/) and in [Wordle Alternatives](https://aloneonahill.com/blog/wordle-alternatives/)

## 🙏🏼 Acknowledgements

- [Arunmozhi](https://twitter.com/tecoholic) from Tamil-Wordle to share the diacritics merging code snippet.
- [Hannah Park et al.](https://www.linkedin.com/in/hannahpark1000/) for starting and maintaining the base[https://github.com/hannahcode/wordle] of the repository above this foundation the codebase has been built.
- [Dr. Aviseka Acharya](https://twitter.com/aviseka) for all the inspiration and support throughout.
- [Saswata Debadutta](https://twitter.com/pureodiasaswata) et al for making the logo and providing ideas on upgrading the UX.
- All the alpha testers who have tested the website before public release and provided their suggestions for improvement.
- The launch audience of Twitter space, who have provided instant feedback.
- The players who post their gameplay results, motivate other Odias to play, report bugs, and provide valuable feedback to us.

<!-- Citation -->
<hr>
If you find this article useful, please cite this using:

```bibtex
@misc{Soumendrak,
    author       = {Soumendra Kumar Sahoo},
    title        = {The story behind Shabdarasa},
    howpublished = {\url{https://www.blog.soumendrak.com/}},
    year         = {2022}
}
```
