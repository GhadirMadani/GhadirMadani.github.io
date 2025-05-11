---
title: "Assignment 2"
date: 2025-04-20
categories:
  - Blog
tags:
  - Jekyll
  - Assignments
---

## Reading Emirati Heritage through Machines: A Cultural Analysis of Visual AI

### 1. Introduction

This project was a chance to explore how machine learning models “see” images, especially images that represent a culture they may not have been trained on. I built a custom image corpus focused on UAE heritage, including traditional architecture, crafts, clothing, food, and rituals. These images reflect a culture I know personally, but I wanted to understand how tools like Orange Data Mining and DV Explorer would interpret them. Would the models recognize the meaning behind a dallah or a yowla dance? Or would they just see shapes and colors?

By running these images through clustering, classification, and captioning tools, I started to notice not just what the models could do, but what they overlooked. Some of their outputs were impressively accurate—but others were completely off, sometimes even humorous. These gaps revealed a lot about how AI interprets the world visually, and more importantly, how it simplifies and flattens cultural meaning. As Impett and Offert suggest, using neural networks to read culture always means we're also being shaped by how the model reads us back.

This assignment brings together those experiments, findings, and reflections.

### 2. Building the Dataset

To begin this project, I created a custom image corpus focused on UAE culture and heritage. I chose this topic because it's culturally specific, personally meaningful, and very different from the kinds of content most AI models are trained on, like those in datasets such as ImageNet or COCO. My goal was to see how a machine might interpret visuals tied to local traditions, materials, and rituals that aren't commonly represented in global training data.

The final corpus consisted of 89 images. While I tried to follow the guideline of avoiding human faces, a few images in my dataset did include people, especially in cases where the subject matter was inseparable from the human presence—such as cultural performances, traditional dress, or group rituals. I focused more on capturing the context and cultural details rather than cropping out the faces entirely, since in many cases, the people themselves were part of the visual meaning.

My images were loosely organized into categories that reflect both object and activity types:
- **Architecture** 
- **Crafts** 
- **Food** 
- **Celebration and clothing** 
- **Hobby and way of living** 

Even the process of collecting and curating the images felt like part of the analysis. I had to think critically about what “represents” culture, which scenes or objects would visually stand out to a machine, and what kinds of meanings could get lost or misread in translation. It became clear early on that this was not just a technical dataset; it was a narrative about place, identity, and visibility.
