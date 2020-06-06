## News

**05/05/2020**: If you want to participate in the challenge, fill in this [form](https://forms.gle/pXgWVDiMMUYDgeyM7)

**16/03/2020**: We are now online!

## Menu

- [Task Description](#task-description)
- [Data Description](#data-description)
- [How to Participate](#how-to-participate)
- [Important Dates](#important-dates)
- [Organizers](#organizers)
- [Contacts](#contacts)


## Task Description

The task CONcreTEXT (so dubbed after CONcreteness in conTEXT) focuses on automatic concreteness (and conversely, abstractness) recognition. Given a sentence along with a target word, we ask participants to propose a system able to assess the concreteness of the target word according to a [1-7] concreteness scale, where 1 stands for fully abstract (e.g., 'idempotence') and 7 for maximally concrete (e.g., 'car'). 

The concreteness score being assigned to the word must be evaluated in context: the word should not be considered in isolation, but as part of the given sentence. For example, systems are expected to assign different scores to the verb 'COVER' in the next two sentences:
- *COVER the pot and bring the water to a vigorous boil*;
- *Your fees and tuition help to COVER the costs of providing these services*.

Target words may be either verbs or nouns.

We invite participants to exploit all possible strategies to solve the task, including (but not limited to) knowledge bases, external training data, word embeddings, etc.

### Motivation and state of the art

Ordinary experience suggests that semantic representation and lexical access and processing of concepts can be affected by concepts' concrete/abstract status: concrete meanings, closer to perceptual experience, are acknowledged to be more quickly and easily delivered in human communication than abstract meanings [[1]](#1). Such kind of information grasps a complex combination of experiential (e.g., sensory, motor) and strictly linguistic features, such as verbal associations arising through co-occurrence patterns and syntactic information [[2]](#2).
These features make conceptual concreteness/abstractness a challenging though only superficially explored field, with the notable exception of some works at the intersection between Computational Linguistics and Cognitive Science, such as [[3]](#3) [[4]](#4).
In the last few years, mounting experimental evidences have been gathered in the fields of Neuroscience and Cognitive Science on conceptual access and retrieval dynamics that posit novel issues, such as imageability associated to terms and concepts [[5]](#5), and traits contributing to inferential vs. referential lexical tasks [[6]](#6) [[7]](#7).

The CONcreTEXT task is aimed at investigating how the concreteness information affects sense selection: different from past research, we are interested in assessing the concreteness of terms in context rather than in isolation [[8]](#8) [[9]](#9). The concreteness score is assumed to be a property of word meanings rather than a property of word forms; thus, scoring the concreteness of a term in context implicitly requires to individuate its underlying sense, by handling lexical phenomena such as polysemy and homonymy.

### Reference scientific communities

Information on conceptual concreteness impacts on many diverse tasks and different fields. As mentioned, this task addresses from a novel perspective an old problem such as word sense disambiguation, even if  sense identification and grounding are intentionally left unspecified (that is, participants are not requested to specify what does the target mean by providing a WordNet/BabelNet synset identifier). Additionally, the concrete/abstract nature of senses may be relevant to further NLP tasks, such as the semantic processing of figurative language [[10]](#10) [[11]](#11) [[12]](#12), the automatic translation and simplification [[13]](#13), the characterisation of web queries with difficulty scores [[14]](#14), the processing of social tagging information [[15]](#15).
Furthermore, the task will be useful to test contextualized models (such as those descending from [[16]](#16) and [[17]](#17)), that were proposed to extend traditional embeddings by also extracting context sensitive features.

The CONcreTEXT task may be relevant also for the psycho-linguistics community, where ratings about concreteness, imageability and other features (a.o. [[8]](#8), [[9]](#9)) are largely used as control variables in many experiments. The resulting annotated dataset itself (for both the Italian and English languages) will be a resource to be exploited for future researches focused on concreteness in a more contextual, and thus ecological, setting.

### Definition of concreteness

Operationally, the very first issue is that it is not straightforward to define concreteness/abstractness [[18]](#18). Provided that more fine grained distinctions on abstract and concrete word meanings can be drawn, the term 'concrete' has two main interpretations: 
- what is closer to perception (as opposed to what cannot be experienced directly through the senses);
- what is more specific (as opposed to high-level, abstract).

We are mostly interested in the first aspect, that is perceptually salient concreteness/abstractness.

## Data Description

The dataset used for this task will be taken from the English-Italian parallel section of *The Human Instruction Dataset* [[19]](#19), derived from WikiHow instructions. The dataset is freely available on [Kaggle](https://www.kaggle.com/paolop/human-instructions-multilingual-wikihow). All such documents have been anonymized beforehand, so that downloaded data present no privacy nor data sensitivity issues.

The dataset will be composed by overall 1,000 sentences, and arranged as follows: 500 Italian sentences plus 500 English sentences. For each sentence a target term will be selected, and multiple annotators will be asked to provide it with a concreteness score (1-7 scale). 
After the annotation, inter-rater agreement will be computed and items featured by reduced Kappa (<.7) will be dropped, so to deliver fully reliable data. Human ratings will be averaged, and the resulting figures will be used as gold standard.

### Data Format

The dataset will be released as tab-separated files (one for Italian, one for English) containing 3 fields:
- ID: the index of the target word in the proposed sentence;
- POS: the part-of-speech tag of the target word;
- TEXT: the sentence containing the target to be evaluated.

### Evaluation

Participants' output will be evaluated by measuring its correlation with human ratings, through Pearson and Spearman coefficients.

### Baseline

The baseline will be implemented by considering the concreteness scores provided in literature: [[8]](#8) for English and [[9]](#9) for Italian. 

Let us presently consider Italian and English languages as (*L*); in both languages, given a sentence *S<sub>L</sub>* composed of *N* words, we will compute the concreteness score of the target word *w* as a function of the average concreteness of the sentence. The underlying assumption is that concrete senses typically co-occur with concrete ones, and the same holds for abstract senses [[20]](#20).

Then *C<sub>t</sub>*, the concreteness of the target word *t &isin; S<sub>L</sub>* will be computed averaging the scores associated to all lexical items contained therein: &sum;*C<sub>t</sub> / N*

For terms that have no annotated concreteness score in the considered sources ([[8]](#8) and [[9]](#9)), we will employ the concreteness score of the closest term, on the basis of vector representation, for which human ratings are available in the mentioned works. To these ends, either ConceptNet Numberbatch [[21]](#21) or FastText [[22]](#22) word embeddings will be used.

## How to Participate

*TBA*

## Important Dates

- <del>**29th May 2020**</del> **15th June 2020**: distribution of trial data
- **4th September 2020**: development and distribution of datasets for testing
- **11th - 17th September 2020**: evaluation windows and collection of participants results
- **2nd October 2020**: assessment returned to participants
- **TBD**: report due from participants
- **30th November – 3rd December 2020**: [EVALITA 2020](http://www.evalita.it/) (co-located with CLiC-it 2020)


## References
[<a name="1">1</a>] Valentina Bambini, Donatella Resta, and Mirko Grimaldi. A dataset of metaphors from the Italian literature: exploring psycholinguistic variables and the role of context. PloS one, 9(9):1–13, 2014.

[<a name="2">2</a>] Gabriella Vigliocco, Lotte Meteyard, Mark Andrews, and Stavroula Kousta. Toward a theory of semantic representation. Language and Cognition, 1(2):219–247, 2009.

[<a name="3">3</a>] Felix Hill, Douwe Kiela, and Anna Korhonen. Concreteness and corpora: A theoretical and practical study. In Proceedings of the Fourth Annual Workshop on Cognitive Modeling and Computational Linguistics (CMCL), pages 75–83, 2013.

[<a name="4">4</a>] Felix Hill and Anna Korhonen. Learning abstract concept embeddings from multi-modal data: Since you probably can’t see what i mean. In Proceedings of the 2014 Conference on Empirical Methods in Natural Language Processing (EMNLP), pages 255–265, 2014.

[<a name="5">5</a>] Alessandra Vergallito, Marco Alessandro Petilli, and Marco Marelli. Perceptual modality norms for 1,121 italian words: A comparison with concreteness and imageability scores and an analysis of their impact in word processing tasks. Behavior Research Methods, pages 1–18, 2019.

[<a name="6">6</a>] Diego Marconi. Lexical competence. MIT Press, 1997.

[<a name="7">7</a>] Francesca Garbarini, Fabrizio Calzavarini, Matteo Diano, Monica Biggio, Carola Barbero, Daniele P Radicioni, Giuliano Geminiani, Katiuscia Sacco, and Diego Marconi. Imageability effect on the functional brain activity during a naming to definition task. Neuropsychologia, 137:107275, 2020.

[<a name="8">8</a>] Marc Brysbaert, Amy Beth Warriner, and Victor Kuperman. Concreteness ratings for 40,000 generally known english word lemmas. BEHAV RES METH, 46(3):904–911, 2014.

[<a name="9">9</a>] Maria Montefinese, Ettore Ambrosini, Beth Fairfield, and Nicola Mammarella. The adaptation of the affective norms for english words (anew) for italian. Behavior research methods, 46(3):887–903, 2014.

[<a name="10">10</a>] Julia Birke and Anoop Sarkar. A clustering approach for nearly unsupervised recognition of nonliteral language. In Procs. of the 11th conference of EACL, 2006.

[<a name="11">11</a>] Yair Neuman, Dan Assaf, Yohai Cohen, Mark Last, Shlomo Argamon, Newton Howard, and Ophir Frieder. Metaphor identification in large texts corpora. PloS one, 8(4):e62343, 2013.

[<a name="12">12</a>] Enrico Mensa, Aureliano Porporato, and Daniele P. Radicioni. Grasping metaphors: Lexical semantics in metaphor analysis. In The Semantic Web: ESWC 2018 Satellite Events, pages 192–195, Cham, 2018. Springer. ISBN 978-3-319-98192-5.

[<a name="13">13</a>] Zhemin Zhu, Delphine Bernhard, and Iryna Gurevych. A monolingual treebased translation model for sentence simplification. In Procs. of the 23rd international conference on computational linguistics, pages 1353–1361. ACL, 2010.

[<a name="14">14</a>] Xing Xing, Yi Zhang, and Mei Han. Query difficulty prediction for contextual image retrieval. In European Conference on Information Retrieval, pages 581–585, 2010.

[<a name="15">15</a>] Dominik Benz, Christian Körner, Andreas Hotho, Gerd Stumme, and Markus Strohmaier. One tag to bind them all: Measuring term abstractness in social metadata. In Procs. of ESWC, pages 360–374. Springer, 2011.

[<a name="16">16</a>] Matthew E Peters, Mark Neumann, Mohit Iyyer, Matt Gardner, Christopher Clark, Kenton Lee, and Luke Zettlemoyer. Deep contextualized word representations. In Proceedings of NAACL-HLT, pages 2227–2237, 2018.

[<a name="17">17</a>] Jacob Devlin, Ming-Wei Chang, Kenton Lee, and Kristina Toutanova. BERT: Pre-training of deep bidirectional transformers for language understanding. In Proceedings of the 2019 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, Volume 1 (Long and Short Papers), pages 4171–4186, 2019.

[<a name="18">18</a>] Rumen Iliev and Robert Axelrod. The paradox of abstraction: Precision versus concreteness. Journal of psycholinguistic research, 46(3):715–729, 2017.

[<a name="19">19</a>] Paula Chocron and Paolo Pareti. Vocabulary alignment for collaborative agents: a study with real-world multilingual how-to instructions. In Proceedings of the Twenty-Sixth International Joint Conference on Artificial Intelligence, IJCAI-18, pages 159–165. International Joint Conferences on Artificial Intelligence Organization, 7 2018. doi: 10.24963/ijcai.2018/22. URL
https://doi.org/10.24963/ijcai.2018/22.

[<a name="20">20</a>] Diego Frassinelli, Daniela Naumann, Jason Utt, Im Walde, and Sabine Schulte. Contextual characteristics of concrete and abstract words. In IWCS 2017, 2017.

[<a name="21">21</a>] Robert Speer, Joshua Chin, and Catherine Havasi. ConceptNet 5.5: An open multilingual graph of general knowledge. In AAAI, pages 4444–4451, 2017. Piotr Bojanowski, Edouard Grave, Armand Joulin, and Tomas Mikolov. Enriching word vectors with subword information. arXiv preprint arXiv:1607.04606, 2016.

[<a name="22">22</a>] Piotr Bojanowski, Edouard Grave, Armand Joulin, and Tomas Mikolov. Enriching word vectors with subword information. arXiv preprint arXiv:1607.04606, 2016.

## Organisers

- Daniele Radicioni, Università di Torino
- Rossella Varvara, Università di Firenze
- Lorenzo Gregori, Università di Firenze
- Andrea Amelio Ravelli, ItaliaNLP Lab - Istituto di Linguistica Computazionale "A. Zampolli" (CNR) Pisa
- Maria Montefinese, Università di Padova

## Contacts

concretext2020@gmail.com
