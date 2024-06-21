---
title: "Daniel Díaz Martel - GitHub Profile"
author: "Daniel Díaz Martel"
output: html_document
---

# 👋 Hello! I'm Daniel Díaz Martel

I am a Computer Engineering student with a passion for programming and developing projects. On this profile, you'll find a variety of projects and repositories that reflect my interests in different areas of computer science, especially in Java.

## 📚 About Me

- **Name:** Daniel Díaz Martel
- **GitHub Account:** [DaniYDevs](https://github.com/DaniYDevs)
- **Degree:** Computer Engineering

## 🛠️ Technologies and Tools

- **Programming Languages:** Java, C++, JavaScript, TypeScript, HTML, CSS, Python
- **Platforms and Frameworks:** Angular, React, Arduino, Vue.js
- **Development Tools:** IntelliJ IDEA, Visual Studio Code, Git

## 🌱 Currently Learning

- Single page applications with AJAX
- Create a blog application from scratch using Node, Express, and MongoDB
- Web development with JavaScript and React
- Deploy your applications and work with cloud databases
- Recognize and prevent common security exploits like SQL-Injection & XSS

## 📫 How to Reach Me

- **Email:** [danidzm18@gmail.com](mailto:danidzm18@gmail.com)
- **LinkedIn:** [Daniel Díaz Martel](www.linkedin.com/in/daniydevs)

## 📈 GitHub Statistics

```{r echo=FALSE}
knitr::opts_chunk$set(echo = FALSE)

library(gh)
library(tidyverse)

# Get GitHub user information
user_info <- gh::gh("/users/DaniYDevs")
repos <- gh::gh("/users/DaniYDevs/repos", .limit = Inf)

# Create a dataframe with repository statistics
repo_data <- tibble(
  name = map_chr(repos, "name"),
  stars = map_int(repos, "stargazers_count"),
  forks = map_int(repos, "forks_count")
)

# General statistics
total_repos <- length(repos)
total_stars <- sum(repo_data$stars)
total_forks <- sum(repo_data$forks)

# Display statistics
cat(paste0("Total Repositories: ", total_repos, "\n"))
cat(paste0("Total Stars: ", total_stars, "\n"))
cat(paste0("Total Forks: ", total_forks, "\n"))

# Bar chart with ggplot2
repo_data %>%
  ggplot(aes(x = reorder(name, stars), y = stars, fill = forks)) +
  geom_bar(stat = "identity") +
  coord_flip() +
  labs(title = "Repository Statistics",
       x = "Repository",
       y = "Number of Stars") +
  theme_minimal()
```
