---
title: "ELI5: How does a Transformer work?"
seoTitle: "ELI5: Transformer Functioning Explained"
seoDescription: "ELI5: Transformer Language Models
Picture a clever robot using games and math to form new sentences, picking the best words in a "telephone" style"
datePublished: Thu Apr 13 2023 02:58:05 GMT+0000 (Coordinated Universal Time)
cuid: clgej62lg000309jz0mgb435v
slug: eli5-how-does-a-transformer-work
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1681354498506/fa34631e-bf3d-4908-968a-5d7c871d7fbd.png
tags: eli5, text-processing, transformers, llm, by-soumendra

---

Hey, kiddos! So you want to learn about Transformer language models? No problem! Let's dive in! 🏊‍♀️📚

<mark>Imagine you and your friends are playing a game of "telephone" 📞, where you have to repeat a sentence after hearing it from the previous person. Let's say we want to create an intelligent robot 🤖 that can play this game with us and even make up new sentences that make sense! That's what Transformer language models do!</mark>

Here's a fun way to understand how they work:

## Picture Puzzles 🧩

![Puzzle](https://cdn.hashnode.com/res/hashnode/image/upload/v1681307776873/d4289508-a778-4fb7-b786-d1f967f114e0.jpeg align="center")

* Transformer models see words like puzzle pieces. So when we give them a sentence, they try to find the best puzzle pieces (words) to continue the sentence.
    
* Just like how you can put together puzzle pieces to make a pretty picture! 🎨
    

## Memory Game 🧠

![Cards](https://cdn.hashnode.com/res/hashnode/image/upload/v1681307942760/41a325b7-ee46-4332-bd40-844c68c75453.jpeg align="center")

* Remember when you played memory games and had to remember where cards were on the table?
    
* Transformer models have a great memory too! They remember words they've seen before and use this knowledge to create new sentences.
    

## 📖 Friendship Circles 👫

![six silhouette of people jumping during sunrise](https://images.unsplash.com/photo-1548705085-101177834f47?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1000&q=80 align="left")

* In school, you have friends who you talk to and play with.
    
* Similarly, words in a sentence are like friends. The Transformer model tries to understand how these "word friends" are connected to make sense of the sentence. 🤝
    

## Super Decoder Ring 💍

![woman in white long sleeve shirt kissing girl in white long sleeve shirt](https://images.unsplash.com/photo-1621452773781-0f992fd1f5cb?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1000&q=80 align="left")

* Have you ever used a secret code to send messages to your friends?
    
* Transformer models have their decoder rings! They use math (don't worry, no homework involved! 📚) to find the best words to continue a sentence or answer a question. 🔍
    

And that's how Transformer language models work! They're like our smart robot friends who can play games with us, remember things, and even create new sentences! 🤖📝

---

Let's investigate each point and learn more about Transformer language models! 🧐🔍

## Picture Puzzles 🧩

* You remember how we talked about puzzle pieces, right? Well, Transformer models use something called "tokens" as their puzzle pieces.
    
* Tokens can be words or parts of words. They look at the tokens in a sentence and use a technique called "attention" to figure out which tokens are the most important. Attention helps the model decide how the tokens should be combined to create the best sentence. It's like looking at your puzzle pieces and deciding which fit together to create the prettiest picture! 🖼️
    

## Memory Game 🧠

* As you learn from books and teachers, Transformer models learn from lots and lots of text! They read sentences from books, websites, and more to learn about words and how they fit together.
    
* The Transformer model then stores this knowledge in its "weights." When creating a new sentence, the model uses its memory (weights) to find the best words to use. It's like having a big library of word knowledge in its robot brain! 📚🤖
    

## Friendship Circles 👫

* Every word in a sentence relates to other words, just like how you have relationships with friends.
    
* The Transformer model figures out these relationships using "self-attention." It checks how important each word is to the other words in the sentence.
    
* This helps the model understand the meaning of the sentence better. It's like figuring out which friends you should invite to your birthday party based on how close you are to them! 🎂🎉
    

## Super Decoder Ring 💍

* Remember that secret code I mentioned earlier? In Transformer models, the secret code is math! They use mathematical formulas and "layers" to process the words in a sentence.
    
* Each layer is like a step in decoding the secret message, and they work together to find the best words to continue a sentence or answer a question. It's like solving a series of riddles to find a hidden treasure! 🏴‍☠️💰
    

So, that's a deeper look into how Transformer language models work. They're smart robots using tokens, attention, memory, and math to create sentences and answer questions! 🧠🤖

---

Are you with me till now? Cool, let's dig deeper and explore even deeper into the world of Transformer language models. 🔬🌌

## Picture Puzzles 🧩

* When Transformer models use "attention" to determine which tokens are the most important, they calculate a `score` for each token. <mark>The higher the score, the more critical the token is in the sentence.</mark> These scores are used to "weigh" the tokens and decide which ones are the most important to focus on.
    
* It's like giving each puzzle piece a score based on how well it fits with the others and then using the highest-scoring pieces to complete the picture! 🏆
    

## Memory Game 🧠

* Transformer models learn from the text by adjusting their "weights" and "biases" (parameters) during "training." They read many sentences and compare their predictions to the actual words.
    
* <mark>Weights and Biases are similar to Parameters.</mark>
    
* If the model makes a mistake, it adjusts its weights to improve its predictions. This process continues until the model gets good at understanding and creating sentences! It's like practicing a sport or musical instrument over and over until you become a superstar! ⭐🎵
    
* Therefore, a 15 Billion Transformers model can recall better tokens than a 7 Billion parameter model.
    

## Friendship Circles 👫

* When the Transformer model uses "self-attention" to determine the relationships between words, it creates a "map" of these relationships. This map helps the model understand which words are essential and how they interact.
    
* For example, the model can learn that "cat" and "meow" are related, while "cat" and "bark" are not. This helps the model create sentences that make sense! It's like drawing a map of your friendships, showing who's friends with whom and how strong their friendships are! 🗺️👭
    

## Super Decoder Ring 💍

* The mathematical formulas that Transformer models use to process words are called "neural networks." These networks comprise many "layers," and each layer transforms the input (the tokens) differently.
    
* As the tokens pass through the layers, the model refines its understanding of the sentence and makes better predictions. It's like solving a complex puzzle by breaking it down into smaller, more manageable steps! 🧠🔧
    

So there you have it! We went deeper into Transformer language models, learning more about attention scores, training, self-attention maps, and neural networks. These smart robots use all these tools to understand and create sentences like us! 🤖📝