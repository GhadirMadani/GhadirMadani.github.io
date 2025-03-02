---
title: "Assignment 1"
date: 2025-02-03
categories:
  - Blog
tags:
  - Jekyll
  - Assignments
  - Corpus
  - Voyant Tools
  - R Markdown
---

## How Feminist Ideas Evolved: A Textual Analysis of Gender, Oppression, and Identity

### Introduction 
Feminist ideas have changed a lot over time, influenced by the historical and social challenges of each era. This study looks at three important feminist texts: *A Vindication of the Rights of Woman* (1792) by Mary Wollstonecraft, *The Second Sex* (1949) by Simone de Beauvoir, and *Ain’t I a Woman: Black Women and Feminism* (1981) by Bell Hooks. Each of these books pushes back against the way society defines women, but they do so in different ways. Wollstonecraft, writing in the 18th century, argues that women are not naturally inferior but are kept in a lower position because they are denied education and opportunities (Wollstonecraft). She believed women should be seen as rational individuals, just like men. Over 150 years later, Beauvoir introduced the idea that womanhood is not something women are born into, but something society forces upon them, showing how women have been treated as the "Other" in a world designed for men (Beauvoir 267; Moi). Then, in the late 20th century, Hooks took feminism further by exposing its failure to address race and class, arguing that Black women experience oppression differently because they face both racism and sexism (Hooks). Looking at these three books together, we can see how feminist ideas have expanded, from fighting for basic rights like education to questioning what it even means to be a woman and addressing the larger power structures that shape oppression. Over time, feminism has become more complex and inclusive, reflecting the diverse struggles women have faced across history.

### Methodology
We conducted a computational analysis using R Markdown, generating four key visualizations: a word cloud, a word frequency table, a TF-IDF analysis table, and a word frequency graph. After loading the necessary packages, we combined the three texts into a single data frame, tokenized the text, and removed stop words for accuracy. Using count(word, sort = TRUE), we identified the most frequent words and visualized them in a word cloud. The bind_tf_idf(word, source, n) function computed the TF-IDF scores to highlight distinctive words in each text. Finally, we created a word frequency graph to compare linguistic patterns across the three works. 

### Analysis and Findings
#### Voyant Tools Analysis
For the first part of the analysis, we used Voyant Tools to explore the language in A Vindication of the Rights of Woman, The Second Sex, and Ain’t I a Woman. We looked at word frequency, common phrases, and how key terms are linked to see how each author discussed gender, oppression, and womanhood. In the visualizations, the key terms appear in blue, with larger words representing the most frequently used terms in each text. Additionally, the thicker the line connecting two words, the stronger their relationship, meaning they often appear together in the text. This helped us track changes in feminist thought over time. For example, Wollstonecraft often focused on reason, Beauvoir on otherness, and Hooks on race and intersectionality. By studying these connections, we gained insight into how feminist ideas have evolved across different historical periods.

<iframe style='width: 709px; height: 411px;' src='https://voyant-tools.org/tool/CollocatesGraph/?query=home*&query=home&query=life&query=men&query=women&query=man&query=children&corpus=8abd612db5621971ff1faa824465e2ad'></iframe>
Mary Wollstonecraft’s A Vindication of the Rights of Woman criticizes the rules and traditions that limit women’s roles in society. The word “women” is central in her argument and is closely connected to “men,” “society,” “life,” and “duties,” showing her belief that social norms hold women back from getting an education, being independent, and having equal rights. She explains how “men” are seen as the leaders in both public life and at home, while words like “children” and “wives” reinforce the idea that women are expected to be caretakers instead of intellectual equals. Wollstonecraft challenges the belief that a woman’s main purpose is to be a wife and mother.. The link between “men” and “society” shows her criticism of male-led institutions that keep women in lower positions. The connection between “life” and “women” highlights her call for women to have control over their own lives. Her work is a key feminist argument for changing social structures and giving women more freedom and equality.

<iframe style='width: 709px; height: 411px;' src='https://voyant-tools.org/tool/CollocatesGraph/?query=father&query=father*&query=home&corpus=58f6970aeb658858f8f3eb91ab456c49'></iframe>
Simone de Beauvoir’s The Second Sex critiques how women have historically been defined in relation to men rather than as independent individuals. The central focus on “woman” and its strong link to “man” reflects her argument that gender roles are socially constructed. She explores how marriage and family life confine women, with terms like “mother,” “wife,” and “home” emphasizing traditional domestic expectations. Beauvoir also critiques patriarchal authority, with “man” linked to “authority” and “God,” reinforcing the idea that men are positioned as the societal norm while women are the “Other.” Through these themes, Beauvoir argues that women’s liberation depends on breaking free from restrictive social roles and achieving true autonomy.

<iframe style='width: 709px; height: 411px;' src='https://voyant-tools.org/tool/CollocatesGraph/?query=racism&query=slave&query=feminism*&corpus=896ae0f748615b1d733b55e735325492'></iframe>
Bell Hooks’ Ain’t I a Woman: Black Women and Feminism focuses on how race and gender shape women’s experiences. The most important words in her text (“black,” “white,” and “women”) show that she examines how racism and sexism are connected. The strong link between “black” and “white” suggests she discusses racial identity, privilege, and exclusion in feminism, while “women” being connected to both highlights her intersectional approach. Though “men” and “male” appear, they are less central, meaning patriarchy is discussed but not the main focus. The words “slave,” “black,” “women,” and “experience” being connected show how the history of slavery still affects Black women. The presence of “racism” and “sexism” emphasizes that these struggles overlap, and “sexual” being linked to “white” and “women” suggests a discussion of sexual politics and exploitation. The word “feminism” shows that hooks critiques the feminist movement, and “experience” being tied to “woman” and “slave” reinforces her argument that lived experiences matter in feminist discussions. Overall, Hooks challenges feminism’s failure to fully include Black women and calls for a more inclusive, intersectional movement.

#### R Markdown Analysis
![Image](/Images/Image1.png)
