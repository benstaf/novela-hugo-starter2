+++
authors = []
date = 2020-02-12T23:00:00Z
excerpt = "Molecule generation is a hot topic in AI for drug discovery. In a previous blog post, I exposed how some methods had issues with generating diversity. Since then, new papers appeared to address this problem (sometimes without citing my paper raising it)."
hero = ""
timeToRead = 5
title = "You didn’t need deep learning to generate new molecules"

+++
Molecule generation is a hot topic in AI for drug discovery. In a previous [blog post](https://medium.com/the-ai-lab/artificial-intelligence-in-drug-discovery-is-overhyped-examples-from-astrazeneca-harvard-315d69a7f863), I exposed how some methods had issues with generating diversity. Since then, new papers appeared to address this problem (sometimes without citing [my paper](https://arxiv.org/abs/1708.08227) raising it). Most of the proposed solutions are quite complicated, like those from [Insilico Medicine](https://pubs.acs.org/doi/10.1021/acs.molpharmaceut.7b01137), [Harvard-Toronto-Insilico Medicine](https://pubs.acs.org/doi/abs/10.1021/acs.jcim.7b00690), [Israel Institute of Technology](https://arxiv.org/abs/1804.02668), or [Stanford](https://arxiv.org/abs/1806.02473).

However, these complicated solutions are probably not necessary, because of [another paper](https://arxiv.org/abs/1804.02134), much simpler, from a team led by Koji Tsuda, at the university of Tokyo. They propose a genetic algorithm, called [ChemGE](https://arxiv.org/abs/1804.02134), for _Chemistry Grammatical Evolution_.

![](https://miro.medium.com/max/30/1*7MaITxvuiCPl8_JPuK65SA.jpeg?q=20 =863x508)

![](https://miro.medium.com/max/863/1*7MaITxvuiCPl8_JPuK65SA.jpeg =863x508)

![](https://miro.medium.com/max/30/1*APJYwq3Ltq7WfH87-RJ-LA.png?q=20 =800x445)

![](https://miro.medium.com/max/800/1*APJYwq3Ltq7WfH87-RJ-LA.png =800x445)

They consider a fitness score, which evaluates the desired output: druglikeness, expected activity, and so on. They start from a random collection of molecules, they select the fittest half of the population, and eliminate others (selection). Next, they double the surviving population by random sampling (reproduction), and they randomly tweak the chemical formula of the newborn molecules (mutation). They iterate until the population of molecules is acceptable.

The Tokyo team compared this genetic algorithm with their own deep reinforcement learning algorithm, [ChemTS](https://arxiv.org/abs/1710.00616), inspired by [AlphaGo](https://en.wikipedia.org/wiki/AlphaGo). They found that ChemGE performed at least similarly to ChemTS: generated molecules achieved good fitness, and they were sufficiently different from each other. Moreover, ChemGE was much faster.

![](https://miro.medium.com/max/30/1*5LsZG-fxUTtlcgSyXATMew.jpeg?q=20 =500x320)

![](https://miro.medium.com/max/500/1*5LsZG-fxUTtlcgSyXATMew.jpeg =500x320)

[ChemTS](https://arxiv.org/abs/1710.00616), the deep reinforcement learning baseline

Genetic algorithms have a long history in molecule generation. They date back to 1995 at least, with a paper by Glen and Payne, from Wellcome labs (an ancestor of the big pharma [GSK](https://en.wikipedia.org/wiki/GlaxoSmithKline#Glaxo_Wellcome)).

## A genetic algorithm for the automated generation of molecules within constraints

### A genetic algorithm has been designed which generates molecular structures within constraints. The constraints may be…

#### link.springer.com

Before genetic algorithms, there were even other methods, like this 1989 [paper](https://link.springer.com/article/10.1007/BF01533070) from Abbott Labs (an ancestor of the big pharma [Abbvie](https://en.wikipedia.org/wiki/AbbVie_Inc.)). You can check this [1994 survey](https://pubs.acs.org/doi/abs/10.1021/ci00017a027?journalCode=jcics1) for more details (consider [Sci-Hub](https://sci-hub.tw/), if you didn’t subscribe). This historical background can explain why so many people in the pharma industry are skeptical about deep learning: they keep wondering whether it brings anything new to the table.

So the main contribution of this Tokyo paper is the benchmark GA vs. DRL, which is reasonably well performed (an earlier benchmark was also attempted by BenevolentAI, but it was poorly executed, see an [older blog post](https://medium.com/the-ai-lab/benevolent-ai-drug-discovery-paper-at-iclr-2018-my-open-review-a942a1c523a3)). The result should not be too surprising: similar observations were made about video games tasks. In April 2017, an OpenAI team, led by Ilya Sutskever, compared deep reinforcement learning with evolution strategies, and they often found that both have comparable performance.

## Evolution Strategies as a Scalable Alternative to Reinforcement Learning

### We've discovered that evolution strategies (ES), an optimization technique that's been known for decades, rivals the…

#### blog.openai.com

Another interesting fact is that this Tokyo paper remains largely under-noticed. It appeared in April 2018, more than five months ago, but apparently, the conclusion didn’t fit the narrative or agenda of mainstream tech journalism, industry and academia. This paper makes the field look embarrassingly cheap, that’s bad news for business. The community is often reluctant to perform careful benchmarks. For example, there is this tweet by [Olexandr Isayev](https://medium.com/u/7e4194627f88?source=post_page-----4c784747b2cc----------------------), an academic from the university of North Carolina, author of a [recent paper](http://advances.sciencemag.org/content/4/7/eaap7885) about deep reinforcement learning:

Olexandr Isayev should know that the adoption of deep learning followed a benchmark, the famous 2012 ImageNet, in which a deep learning classifier, AlexNet, outperformed alternatives by a wide margin. No benchmark, no deep learning revolution.

![](https://miro.medium.com/max/30/1*LDibvmzmmLiUs9sxRpHK9w.jpeg?q=20 =1000x734)

![](https://miro.medium.com/max/1000/1*LDibvmzmmLiUs9sxRpHK9w.jpeg =1000x734)

Shallow vs. Deep learning: it’s all about benchmarks

Benchmarks are the way to track progress, or lack thereof. I outlined a [benchmark proposal](https://medium.com/the-ai-lab/diversitynet-a-collaborative-benchmark-for-generative-ai-models-in-chemistry-f1b9cc669cba) in February 2018, and I am still looking for sponsors.

In the meantime, if you meet marketing people, from industry or academia, who want you to adopt their deep learning solution, ask them: how is it better than older, simpler, and faster methods ?

# _Updates:_

_Koji Tsuda reacts:_

_Anvita Gupta, from Stanford (paper_ [_here_](https://arxiv.org/abs/1804.01694)_), reacts (multi-tweet thread):_

## 