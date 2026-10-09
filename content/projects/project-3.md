---
title: "The Inquisitor"
date: 2025-02-04
summary: "Politcal Deepfake Detector (Honorable Mention)"
tags: ["TensorFlow", "Chrome Extension", "JavaScript"]
---

Deepfake classifier demoed at Hacking for Humanity at Duquesne University where we received an honorable mention and invite to present at the governor's residence in Harrisburg. Our demo features a google chrome extension that would run our ML model on social media to flag images that contain AI imagery to battle misinformation witnessed during the 2024 presidential election.

## What it does

- Utilizes a custom TensorFlow and Keras module to classify an image as deepfake or real
- Trained on Kaggle dataset of deepfake images and uses transfer learning to better generalize to political figures.
- Reached up to 95% accuracy on validation data.

## Why it's interesting

During this time, social media companies were virtually doing nothing to spot out misinformation to their users. Political campaigns and accounts that post memes could trick users into believing something that never happened. My team thought that it was important that people know how cheap the compute is to avoid this conflict.

**Repo:** https://github.com/remysedlak/steelhacks-2025
