---
layout: post
title:      "Ruby CLI Data Gem Project : Weather Alert"
date:       2018-06-04 17:00:49 +0000
permalink:  ruby_cli_data_gem_project_weather_alert
---


For this project I created a program that scrapes data from https://alerts.weather.gov/. The user enters a U.S. state and the program returns a list of weather watches, warnings or advisories for the state. From this list, the user can select an alert to get more details and links to the weather.gov website.

In the code, I created two classes, Alert and CLI. 

The **Alert class** is responsible for creating instances of the class, Alert. Instances have attributes such as areas affected, date, description, the name of the alert, status and urgency. The Alert class also performs the webscraping. (In other cli data gem examples, others have created a separate Scraper class (and maybe I should too). It was just easier for me to code the Alert class to scrape and create instances of Alert.

I initially had a lot of trouble scraping the alerts.weather.gov website. In the webpage for each state (example: https://alerts.weather.gov/cap/al.php?x=1), somehow the html elements I inspected in Chrome differed greatly from the Nokogiri, web-scraped data object. So I had to use binding.pry to review the Nokogiri data and use css selectors to webscrape the alert's attributes. For example, 

```
new_alert.name = box.css("event").text
new_alert.status = box.css("status").text)
```

(I wasn't selecting the usual html elements: div, span, p that I was familiar with.)

Then the Alert class performs secondary scraping of each alert's webpage to get the alert's description and preparedness instructions.

The Alert class method, create_alerts returns an array of instances of the class Alert.

The **CLI class** is the command line interface that interacts with the user. It welcomes the user, asks them to input a state, displays the state's alerts and each alert's details if the user requests. 

Controversially, the CLI class has an instance variable, @state_alerts that stores the array of alerts created by the Alert class. One may wonder, "Why is it the CLI class's job to store the alerts? Shouldn't the Alert class keep track of instances of itself?"

(I'm not entirely sure of the following but here is my justification.)

In other Ruby labs, many of the classes contain a class variable, @@all that stores all instances of the class. I would argue that in those situations, the data is more static and less likely to be updated. For example, in the Music Library CLI, the @@all array of Artists will likely by added to but the entire @@all array is unlikely to be constantly changing. In other words, I'll probably add to my music collection but it's less likely that I'll regularly throw out all my music and start a brand-new collection.

Because weather alerts are frequently updated (existing alerts can expire and new ones are added), I decided against an @@all array to store alerts. If I did use the @@all array, I'd have to maintain it regularly by removing any expired alerts and adding new ones. It would just be easier to scrape (from scratch) a state's alerts each time a user requests it and create a new batch of alerts for the state. (The major drawback is that it takes up to 1 minute to retrieve a state's weather alerts but the benefit of doing this is that the data is current.)

And because the user selects a state through the CLI class, I decided to store the array of Alerts (@state_alerts) in the CLI class.

I'm not sure if this decision is entirely justified but I just wanted to explain my thought process.

link to github: https://github.com/marcusjun/weather-alert-mbj-cli-app

