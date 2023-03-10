---
title: "SQL with TD 2"
excerpt: "Modeling data from a web API with Python & SQL"
header:
  teaser: assets/images/er-diagram.png
share: false
sidebar:
  - title: "Links"
    text: "<ul>
    <li><a href='https://github.com/justinhnain/td2-sqlite'>GitHub repository</a></li>
    <li><a href='https://colab.research.google.com/drive/1nZgowA33ApEjFH4lrfHTvsvcB-qCcK9k?usp=sharing'>Google Colab notebook</a></li>
    </ul>"
  - title: "Tools Used"
    text: "Python, SQLite"
toc: true
toc_icon: "cog"
toc_label: "Table of Contents"
classes: wide
#toc_sticky: true
#sidebar_sticky: false
---

<p float="left">
<img alt="Animated gif of the game" src="https://user-images.githubusercontent.com/78244259/184516851-f0a3512e-fcc7-4e7a-a5fa-3bfdde512585.gif" width="55%" /><img alt="A graph of ELO relative to hours played." src="https://user-images.githubusercontent.com/78244259/184796640-7ed11279-e38f-40fb-acb7-180a4dea9d70.png" width="45%"/> </p>


### Purpose & Overview
This is practice in undertaking a full ETL process, and forming SQL queries.  

I pull data from an API, format & clean the data, input the data into an SQLite database, query it with Python's SQLite3 interface, and make <u>basic</u> visuals out of the data using several Python libraries in Google Colaboratory.

Each section in the Google Colaboratory notebook showcases command over different SQL features.

#### Data Source
The data is collected from the official Legion TD 2 public API, which serves its data in JSON format.  I was provided an API key at their developer portal.  Replicating this can be done by following the instructions of the [API document page for Legion TD 2](https://swagger.legiontd2.com/).

#### Project Structure
- The Google Colaboratory notebook contains the SQL analysis of the database.
- The file db_fns.py is a collection of functions for writing to the database that is named 'td2.db'.  
- The file td2.py is the main program, which handles collecting data from this project's API, cleaning that data, and writing to the database through db_fns.py.

### Choosing an RDBMS
I've chosen SQLite3 because it's light weight, and my data doesn't need future updates for this one-off analysis.  A 2015 presentation on SQLite by Dr. Richard Hipp is inspirational for this choice.  Otherwise, I'd have probably set up a PostgreSQL server, and ran a cron job for pulling data each day.  I'll reserve that for another time, because my objective here is primarily to display my competency in SQL.

#### Designing the Database
The storage needs to be designed with considerations for both simplicity and efficiency.  Simplicity is a concern because analyses on a needlessly complicated database will prove cumbersome.  Efficiency is a concern because some of the tables in here contain hundreds of thousands of records.


![ER diagram](/assets/images/er-diagram.png)


After some contemplation about relationally modelling the data, I've arrived at these three entities connected by two one-to-many relationships.  It's only in the second normal form, but further normalization would only be necessary if this database were to be maintained.

### Choosing Interesting Questions

Choosing interesting questions that naturally involve disparate SQL techniques is another challenge for my presentation.  The questions that arise from the data are both influenced by my experience playing the game Legion TD 2 and SQLzoo's website, which is a website that contains various SQL tutorials.  I credit the tutorial-writers at SQLzoo for having given me some direction for the techniques I portray in my queries.

### Dealing with Legacy Data from the API and 504 Errors!

Major issues that I faced came from both data with missing fields, and error data resulting from an overloaded API server.  To meet these challenges, defensive code, try-catch structures, and some detailed comments are present in td2.py's code.

### Legion TD 2
[Legion TD 2](https://legiontd2.com) is "an infinitely replayable multiplayer and single-player tower defense. [Where players defend] against waves of enemies and destroy the enemy's king before they destroy yours. Legion TD 2 is a one-of-a-kind game of tactics, teamwork, and prediction. [Players may party] as 1-8 players. (AutoAttack Games, 2022)"

#### References & Links

[1] API data-source documentation: https://swagger.legiontd2.com/

[2] Query inspiration: www.sqlzoo.net

[3] SQLite: The Database at the Edge of the Network with Dr. Richard Hipp: https://www.youtube.com/watch?v=Jib2AmRb_rk

[4] AutoAttack Games: https://store.steampowered.com/app/469600/Legion_TD_2__Multiplayer_Tower_Defense/

[5] Animated GIF source: https://www.youtube.com/watch?v=JA7sUGS6Fk4 (2:57,...)

