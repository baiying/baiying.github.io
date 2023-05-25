---
title: How to manage mutiple versions of nodejs under the MacOS
toc: true
date: 2023-05-25 10:59:13
cover: /images/programming.png
thumbnail: /images/programming.png
categories: [Programming, Skill]
tags: [MacOS, Nodejs]
---

We can use 'n' to manage mutiple nodejs.

1. Install n globally
```bash
npm install -g n
```

2. Install the specified version of nodejs
```bash
sudo -E n 16.18.0
```

3. View the list of installed versions
```bash
n list
```

4. Remove specified version
```bash
n rm 16.18.0
```

5. Switch versions
```bash
sudo n
# Select version by Up/Down keys
```