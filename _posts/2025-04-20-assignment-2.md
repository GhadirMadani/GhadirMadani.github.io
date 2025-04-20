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
Finally, I created two sets of coordinates for each ship entry: one for where the ship came from, and one for where it was going. If a ship was listed as “still in harbour,” I used the coordinates for the Port of Zanzibar ==(lat: `-6.1659`, lon: `39.2026`)== to represent its location.

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
This is the table with all the coordinates included in them.




