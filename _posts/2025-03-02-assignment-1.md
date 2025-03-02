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
We conducted a computational analysis using R Markdown, generating four key visualizations: a word cloud, a word frequency table, a TF-IDF analysis table, and a word frequency graph. After loading the necessary packages, we combined the three texts into a single data frame, tokenized the text, and removed stop words for accuracy. Using `count(word, sort = TRUE)`, we identified the most frequent words and visualized them in a word cloud. The `bind_tf_idf(word, source, n)` function computed the TF-IDF scores to highlight distinctive words in each text. Finally, we created a word frequency graph to compare linguistic patterns across the three works. 
