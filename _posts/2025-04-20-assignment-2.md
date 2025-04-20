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

To organize the data more clearly, I split it into two CSV files: one for **ships arriving in Zanzibar** and one for **ships departing from Zanzibar**. For the arrivals file, I recorded the port the ship came from in the “From” column and used Zanzibar’s coordinates (`lat: -6.1659`, `lon: 39.2026`) as the “Bound To” location. For the departures file, I did the opposite — I used Zanzibar’s coordinates as the origin (“From”) and recorded the next port the ship was heading to in the “Bound To” column. This split made it easier to map inbound and outbound traffic separately and helped avoid confusion when visualizing routes. 

In some cases, the Gazette didn’t list a departure or arrival date, or the information was vague — like “still in harbour.” When that happened, I marked those rows as best I could and assumed that “still in harbour” meant the ship was currently in Zanzibar.

I also noticed that some ships, like *Cupid* and *Barawa*, appeared multiple times across different weeks. Rather than combine them, I treated each weekly mention as a separate entry to stay true to the time-based structure of the reports.

One of the more challenging parts of modeling the data was dealing with port names that were either historical, vague, or inconsistently spelled. For example, “D'Salam” appeared frequently in the reports, which I interpreted as Dar-es-Salam (modern-day Dar es Salaam, Tanzania). I standardized names like these to their present-day equivalents so I could geocode them accurately.

Some entries referred to broad regions rather than specific ports — like “South” or “Europe.” In these cases, I had to make informed decisions about what location to assign. For “South,” I used coordinates for **Mauritius** (lat: `-20.3484`, lon: `57.5522`), since it appeared to be the central hub for southern Indian Ocean routes in this dataset. For “Europe,” I used **Paris, France** (lat: `48.8566`, lon: `2.3522`) as a general European reference point, given the lack of specificity.

Other ambiguous entries, like “Benadir Coast,” were matched to **Mogadishu** (lat: `2.0469`, lon: `45.3182`), which was the main port in that region during the time. “Delagoabay” was mapped to **Maputo Bay** in Mozambique, and “Diamond Island” was matched to its historical location off the coast of Myanmar. All ports were manually researched and matched one by one, based on their colonial or modern names, and then their coordinates were entered into the dataset by hand.

