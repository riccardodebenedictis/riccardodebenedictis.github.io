---
layout: post
title: Dialogue is all you need!
---

[Transformers](https://en.wikipedia.org/wiki/Transformer_(machine_learning_model)) are a powerful architecture, which can be used for a wide range of tasks, including machine translation, text summarization, and dialogue generation. The Transformer architecture is a stack of self-attention layers, which are followed by feed-forward layers. The self-attention layers are based on the attention mechanism, which is a mechanism that allows a model to focus on a specific part of the input sequence, while generating the output sequence. They have been introduced in a famous paper entitled "Attention is all you need" \[[1](#r1)\].

These architectures have become particularly famous, in recent times, thanks to their use within [ChatGPT](https://chat.openai.com/), a chatbot that, trained on a large corpus of text, is able to predict the next word in a sequence, given the previous words in the sequence, resulting in the generation of coherent and entertaining conversations.

The criticisms of these systems, however, are not few. Due to its structure, in fact, by simply choosing sequences of words, one runs the risk that the system [invents its own facts](https://twitter.com/itstimconnors/status/1599544717943123969?s=20&t=cAB9lIKbw8q5DQ2svACxgQ) and, therefore, is increasingly being [excluded](https://meta.stackoverflow.com/questions/421831/temporary-policy-chatgpt-is-banned) from critical situations such as responding convincingly, but often incorrectly, to questions, not to mention the fact that it risks [amplifying some biases](https://www.bloomberg.com/news/newsletters/2022-12-08/chatgpt-open-ai-s-chatbot-is-spitting-out-biased-sexist-results) already present in the users of the system. Furthermore, relying almost exclusively on natural language, the logical and mathematical abilities are [extremely limited](https://writings.stephenwolfram.com/2023/01/wolframalpha-as-the-way-to-bring-computational-knowledge-superpowers-to-chatgpt/).


### References

[<a name="r1"></a>1] Vaswani A., Shazeer N., Parmar N., Uszkoreit J., Jones L., Gomez A. N., Kaiser Ł., and Polosukhin I. (2017), *Attention is all you need*. Proceedings of the 31st International Conference on Neural Information Processing Systems (NIPS'17). Curran Associates Inc., Red Hook, NY, USA, 6000–6010. [Online]. Available: http://papers.nips.cc/paper/7181-attention-is-all-you-need.pdf.