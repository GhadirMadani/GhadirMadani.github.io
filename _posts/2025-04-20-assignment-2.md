---
title: "Assignment 2"
date: 2025-04-20
categories:
  - Blog
tags:
  - Jekyll
  - Assignments
---

## Thick Mapping Zanzibar (January-March 1913): Visualizing Shipping Routes from the Zanzibar Gazette

### 1. Introduction
This project looks at maritime activity in East Africa during the British colonial period by focusing on shipping reports from the Zanzibar Gazette. The Gazette was a government-run newspaper that published all kinds of administrative records, including weekly updates on ship traffic. I chose to work with the Shipping Reports section because it lists the names of ships, where they came from, where they were going, and when they arrived or departed — which makes it ideal for mapping.

For this project, I collected and organized 127 entries, covering a three-month period from **the week ending 5 January 1913 to the week ending 30 March 1913**. Each row in my dataset represents the movement of a ship through the Port of Zanzibar (Unguja), either arriving, departing, or staying in harbour.

By focusing on this short but detailed time frame, I was able to get a clear sense of how Zanzibar was connected to other places in the Indian Ocean — like Bombay, Mombasa, Durban, Marseille, and more — and how colonial trade operated through these routes.

### 2. Dataset Modeling

To turn the shipping reports into a usable dataset, I created a table where each row represents one ship movement — either an arrival, a departure, or both. The original reports usually listed the ship’s name, where it came from, where it was heading, its tonnage, nationality, and the date it arrived or left the Port of Zanzibar. I used those elements as the core fields in my spreadsheet.

The main columns I included were:

- **Date (Arr.)**
- **Date (Dep.)**
- **Ship Name**
- **Tonnage**
- **Nationality**
- **From** (the port the ship came from)
- **Bound To** (the next port the ship was heading to)

To prepare the data for mapping, I added two more sets of columns: one for the latitude and longitude of the origin port, and another for the destination. These were either manually researched or matched using a reference table I created.

To organize the data more clearly, I split it into two CSV files: one for **ships arriving in Zanzibar** and one for **ships departing from Zanzibar**. For the arrivals file, I recorded the port the ship came from in the “From” column and used Zanzibar’s coordinates  as the “Bound To” location. For the departures file, I did the opposite — I used Zanzibar’s coordinates as the origin (“From”) and recorded the next port the ship was heading to in the “Bound To” column. This split made it easier to map inbound and outbound traffic separately and helped avoid confusion when visualizing routes. 

In some cases, the Gazette didn’t list a departure or arrival date, or the information was vague — like “still in harbour.” When that happened, I marked those rows as best I could and assumed that “still in harbour” meant the ship was currently in Zanzibar.

I also noticed that some ships, like *Cupid* and *Barawa*, appeared multiple times across different weeks. Rather than combine them, I treated each weekly mention as a separate entry to stay true to the time-based structure of the reports.

### 3. Using GenAI Tools

To extract structured data from the OCR-scanned shipping reports, I used a combination of generative AI tools. My goal was to convert the messy text into clean, tabular information with columns like date, ship name, origin, destination, tonnage, and nationality.

#### Tools I used:
- **ChatGPT-4** 
- **Perplexity**
- **Gemini** 
- **Claude** 
- **OCR-generated PDFs and screenshots** from the Zanzibar Gazette

I uploaded cropped images or pasted the OCR text directly into the AI interfaces. The performance of each tool varied; some handled text layout better, while others struggled with dates, indentation, or hallucinated fields that didn’t exist in the original source.

Out of the tools I tried, **ChatGPT-4** gave me the most consistent results. It handled the formatting well, followed my instructions closely, and was easy to work with when I needed to revise prompts. I also tested **Perplexity**, and in some cases it actually did a better job than ChatGPT at correctly separating the rows and extracting the fields — especially when the OCR was messy. However, I felt more comfortable using ChatGPT overall, both because of the interface and the way I could control the structure of the output more easily.

I also experimented with **Gemini** and **Claude**, but they didn’t perform as well. Claude often combined two ships into one row, and Gemini occasionally skipped important fields like departure dates or misread the structure of the report entirely.

After some trial and error, I found that the best way to get usable results was to **work in small sections** and use a very specific prompt. Here’s the one that worked best:

> **Prompt used:**  
> *You are a data extraction assistant working with OCR-scanned historical documents. Extract the following fields from each entry in the shipping report: Date (Arr.), Date (Dep.), Ship Name, Tons, Nationality, Where From, Bound To. If a field is missing or not clear, leave it blank. Return the data as a clean markdown table with one row per ship.*

Even with this prompt, I had to check each result manually. OCR issues like misread dates (e.g., “Jan. 1l” instead of “Jan. 11”) or merged ship names and tonnage were common. Some tools also hallucinated fields that weren’t there. In the end, GenAI helped speed up the extraction, but it still required a lot of human correction to get the data into a clean, usable format.

### 4. Data Cleaning & Geocoding

Once the data was extracted, I had to go through each row manually to correct OCR errors and fill in missing or misinterpreted values. Some common issues included ship names merging with tonnage numbers, misread dates, or inconsistent spacing. I also corrected cases where a field was left blank due to formatting in the original source — for example, when dates were listed as quotation marks (") to repeat the one above, I manually added the correct date.

After that, I started the geocoding process. For each port listed in the “From” and “Bound To” columns, I looked up its latitude and longitude individually. I didn’t use any automated tools for this part — instead, I created a manual reference list and entered the coordinates by hand. For commonly repeated ports like Bombay, Zanzibar, or Mombasa, this was straightforward. But for more ambiguous entries, I had to make some interpretive decisions.

For example:
- **“D'Salam”** was standardized to **Dar-es-Salam**
- **“Benadir Coast”** was mapped to **Mogadishu**
- **“Delagoabay”** was mapped to **Maputo Bay (Mozambique)**
- **“Diamond Island”** referred to a small island off Myanmar
- **“South”** was mapped to **Mauritius** 
- **“Europe”** was mapped to **Paris, France** 
Finally, I created two sets of coordinates for each ship entry: one for where the ship came from, and one for where it was going. If a ship was listed as “still in harbour,” I used the coordinates for the Port of Zanzibar to represent its location.

#### Port Coordinates Reference Table

| Port Name              | Country/Region            | Latitude   | Longitude   |
|------------------------|---------------------------|------------|-------------|
| Perim (Mayyun)         | Yemen (Red Sea)           | 12.6497    | 43.4067     |
| Pemba                  | Tanzania (Zanzibar)       | -5.2452    | 39.8100     |
| Zanzibar (Unguja)      | Tanzania                  | -6.1659    | 39.2026     |
| Dar-es-Salam           | Tanzania                  | -6.7924    | 39.2083     |
| Mombasa                | Kenya                     | -4.0435    | 39.6682     |
| Aden                   | Yemen (Gulf of Aden)      | 12.7855    | 45.0187     |
| Bombay (Mumbai)        | India                     | 18.9388    | 72.8354     |
| London                 | United Kingdom            | 51.5072    | -0.1276     |
| New York               | United States             | 40.7128    | -74.0060    |
| Europe (central est.)  | Approx. France            | 48.8566    | 2.3522      |
| Beira                  | Mozambique                | -19.8360   | 34.8500     |
| South (unspecified)    | Approx. Mauritius         | -20.3484   | 57.5522     |
| Marseilles             | France                    | 43.2965    | 5.3698      |
| Durban                 | South Africa              | -29.8587   | 31.0218     |
| Tanga                  | Tanzania                  | -5.0689    | 39.1024     |
| Benadir (Mogadishu)    | Somalia                   | 2.0469     | 45.3182     |
| Mogalisho              | Somalia                   | 2.0469     | 45.3182     |
| Kismayu                | Somalia                   | -0.3582    | 42.5454     |
| Madagascar             | Madagascar (Antananarivo) | -18.8792   | 47.5079     |
| Liverpool              | United Kingdom            | 53.4084    | -2.9916     |
| Genoa                  | Italy                     | 44.4056    | 8.9463      |
| Birkenhead             | United Kingdom            | 53.3925    | -3.0128     |
| Diamond Island         | Myanmar                   | 16.2843    | 94.6943     |
| Delagoabay             | Mozambique (Maputo Bay)   | -25.9653   | 32.5832     |
| Comoro Island          | Comoros                   | -11.6455   | 43.3333     |
| Majunga                | Madagascar                | -15.7167   | 46.3167     |
| Batoum                 | Georgia (Black Sea)       | 41.6500    | 41.6333     |
| Aroebay (approx.)      | Indonesia region          | -5.5000    | 132.2500    |

**Table 1: Port Coordinates Reference Table**  
A manually compiled list of all ports mentioned in the dataset, matched to their approximate modern-day latitude and longitude. These values were used to geocode each ship route for mapping. In cases where the port name was vague or historical (e.g. “South,” “Europe,” or “Benadir Coast”), a central location was selected based on historical context.

### 5. Visualization & Insights

After completing the dataset, I visualized the ship movements using [kepler.gl](https://kepler.gl), splitting the routes into two separate views: **ships arriving in Zanzibar** and **ships departing from Zanzibar**. This approach helped me clearly distinguish inbound and outbound maritime traffic and better understand the directionality of trade.

For both maps, I used **arc layers** to connect each pair of ports. I adjusted the **thickness of the arcs** based on how frequently a route appeared — routes used multiple times appeared thicker, while one-off or infrequent routes were thinner. This made it easy to see which connections were central to Zanzibar’s shipping activity during this period.

In the inbound map (to Zanzibar), strong and repeated routes came from **Pemba**, **Bombay**, **Mombasa**, and **Dar-es-Salam**, with ships like *Cupid* and *Barawa* appearing many times. These created heavy, almost “braided” arcs around the Zanzibar-Pemba region. Outbound routes (from Zanzibar) showed similar clustering, but with broader dispersal to **Durban**, **Europe**, and the **Benadir Coast**.

This method made it easier to pick up on both the **regional rhythm** of short-haul traffic and the **long-distance colonial trade links**. It also helped spot imbalances — for example, some ports had frequent incoming ships but fewer outgoing ones, and vice versa.

#### Example Maps:
<img src="{{site.baseurl}}/assets/images/zanzibar_arrivals.png">

**Figure 1: Ships arriving in Zanzibar between January and March 1913**  
Arc thickness indicates the frequency of arrivals from each port — thicker arcs show heavily trafficked routes, especially from regional ports like Pemba, Bombay, and Dar-es-Salam.

<img src="{{site.baseurl}}/assets/images/zanzibar_departures.png">

**Figure 2: Ships departing from Zanzibar between January and March 1913**  
This map visualizes outbound movements from the port of Zanzibar. Thicker arcs represent routes that were used more often, such as repeated trips to Pemba, Bombay, and Durban.

### 6. Critical Reflection: GenAI and Colonial Archives

Working with generative AI tools made this project faster and more manageable — but it also raised questions about what it means to extract, automate, and visualize data from a colonial archive like the Zanzibar Gazette.

The article *Provocations from the Humanities for Generative AI Research* argues that AI systems inherit the assumptions and structures of the materials they’re trained on. In this case, I was using AI to extract structured data from a bureaucratic source that was already shaped by the colonial mindset. The Gazette only recorded what the British administration considered important — ship names, tonnage, nationalities — but said nothing about the people on board, the labor involved, or the impact of this movement on local communities and economies.

GenAI tools like ChatGPT helped me organize and map that structure, but they also reinforced it. The shipping records start to look “clean” and “complete” once visualized — but what’s missing is just as important. There are no records of African sailors, no information about goods or cargo, and no sense of resistance or complexity. In this way, AI risks making the archive look more neutral and objective than it really is.

At the same time, thick mapping helped me see new layers of meaning. It showed how often ships moved between Zanzibar and certain key ports — not just as individual events, but as patterns of repetition, control, and extraction. It also made me think about the gaps: why do some ports only appear once? Why are others repeated every week?

This reflection reminded me that using AI in the humanities isn’t just about speed or automation — it’s also about asking better questions, being aware of what's left out, and understanding how digital tools can both reveal and erase historical meaning.

## 7. Dataset and Visuals

The full dataset used for this project includes 127 rows of cleaned and geocoded shipping data extracted from the Zanzibar Gazette, covering the period between January and March 1913.

**[Click here to view the full dataset for the arricals (CSV)](/assets/assignment2_From.csv)**

**[Click here to view the full dataset for the arricals (CSV)](/assets/assignment2_To.csv)**



