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

## 3. Clustering and Emergent Patterns

After building my dataset, I used Orange Data Mining and the InceptionV3 model to explore how the images would be grouped by a neural network. I ran the image embedding workflow and generated a visual plot that clustered the images based purely on what the model saw—things like shape, color, and texture. It had no understanding of cultural meaning or context, only patterns.

What I found fascinating was how the clustering revealed unexpected groupings. I manually annotated the four quadrants of the image plot based on what I noticed:

<img src="{{site.baseurl}}/assets/images/Clustering.png">

- **Top-left:** Domestic and Culinary Culture
- **Top-right:** Hand Craft and Tradition
- **Bottom-left:** Architecture and Transport
- **Bottom-right:** Social Ceremonies and Dress

Some of these clusters made sense. Architectural images like forts and towers naturally grouped together because they share similar colors and lines. But others were more surprising—like food and craft items ending up in the same area, likely because of their round forms and earthy tones.

This made me reflect on something Impett and Offert wrote: *“In reading a corpus of visual culture through a neural network, we are always also doing the reverse.”* In other words, the model isn’t just interpreting my dataset; I’m being influenced by how it sees things too. I started noticing connections I hadn’t thought about before. For example, I realized how often ritual objects share materials or color palettes with everyday ones. The clustering didn’t just sort images; it reshaped how I looked at my own visual archive.

## 4. Categorization and Classification

For the next step, I organized my image corpus into five categories that felt meaningful based on what I knew about the images and the culture they came from. These categories were:  
**architecture**, **celebration and clothes**, **crafts**, **food**, **hobby and way of living**

Each folder contained a balanced number of images, and I tried to make the categories distinct, but not too narrow. Then, I ran classification using Orange and the InceptionV3 model, followed by a confusion matrix to evaluate the model’s accuracy.

Here’s the result:

<img src="{{site.baseurl}}/assets/images/ConfusionMatrix.png">

The model performed surprisingly well in some areas. It did a great job identifying **architecture** and **celebration and clothes**, and even **hobby and way of living** images were mostly classified correctly. But things got more complicated with categories like **food**, which was often confused with **crafts**.

At first, I thought the misclassifications were just mistakes. But when I looked closer, they actually made some sense. A round woven tray might be used for food but also look like a piece of craft. The model wasn’t entirely wrong—it was picking up on visual cues that blur the lines between how *we* categorize things and how they *appear*.

This reminded me of what Arnold and Tilton talk about in *Distant Viewing*: how models can reveal hidden patterns, but also simplify complex meanings. The confusion matrix didn’t just show where the model failed—it showed where our own human categories are more fluid than we might think. I found myself rethinking some of my own labels. Maybe “way of living” is too broad. In a way, the model pushed me to see my own cultural assumptions more clearly.

## 5. Letting the AI Describe the Culture

For the last part of the assignment, I used the **Image Captioning** tool in DV Explorer to see how the model would describe some of the images from my dataset. I chose a range of visuals—from architecture and crafts to performances and rituals, and waited to see what the model would generate. What I got was a mix of accurate, generic, and completely off-the-mark descriptions.

Here are some of the images and the captions they received:

- <img src="{{site.baseurl}}/assets/images/captioning1.png">
  *Caption:* “A large white building with a large clock.”  
  → **Reality:** This is a historic fort. There's no clock at all. The model completely misinterpreted its purpose and structure.

- <img src="{{site.baseurl}}/assets/images/captioning2.png">  
  *Caption:* “A large group of people dressed in red and white.”  
  → **Reality:** This was a traditional Emirati yowla performance. The caption reduced it to just clothing colors.

- <img src="{{site.baseurl}}/assets/images/captioning3.png">  
  *Caption:* “Men in white uniforms.”  
  → **Reality:** This is a ritual performance, not a military scene. The word "uniform" flattens the cultural meaning.

- <img src="{{site.baseurl}}/assets/images/captioning4.png"> 
  *Caption:* “A man dressed in a costume holding a piece of paper.”  
  → **Reality:** This is a photo of an Emirati bride, in traditional dress and jewelry. The caption is completely wrong, both in gender and interpretation.

- <img src="{{site.baseurl}}/assets/images/captioning5.png"> 
  *Caption:* “A person cutting cloth with scissors.”  
  → **Reality:** It’s a palm-weaving scene, no scissors involved. The model mistook woven material for fabric.

- <img src="{{site.baseurl}}/assets/images/captioning6.png"> 
  *Caption:* “A small metal pot with a bowl on top.”  
  → **Reality:** This is a dallah, a traditional Arabic coffee pot. The model didn’t recognize its cultural significance at all.

- <img src="{{site.baseurl}}/assets/images/captioning7.png"> 
  *Caption:* “A man standing on a beach with a bird.”  
  → **Reality:** This is a falconry scene, an important part of Emirati heritage. The caption is vague and misleading.

- <img src="{{site.baseurl}}/assets/images/captioning8.png"> 
  *Caption:* “People riding brown horses.”  
  → **Reality:** They’re riding camels. This isn’t just a mistake; it’s a culturally significant one.

- <img src="{{site.baseurl}}/assets/images/captioning9.png"> 
  *Caption:* “A man in the water with a frisbee.”  
  → **Reality:** It’s a pearl diver with a traditional basket. The model had no idea what it was seeing.

---

These results were funny at first, but the more I looked at them, the more revealing they became. The captions show just how limited the model’s knowledge is when it comes to culturally specific objects, scenes, or symbols. As Impett and Offert put it, *“reading through a neural network means being read by it in return.”* I expected the model to miss some details, but seeing it reduce a bride to a “man in a costume” or confuse camels for horses was a strong reminder that AI sees through the lens of its training data.

This part of the assignment helped me understand the core risk of machine vision: not just mislabeling, but erasing meaning altogether. As *Distant Viewing* warns, computational models often flatten what they can’t interpret. And if we’re not careful, we might start seeing those flat readings as truth.

But this experience also made me more aware of what *is* being seen, and how I can use those gaps to ask better questions about how culture is represented, who builds these systems, and who gets left out.



