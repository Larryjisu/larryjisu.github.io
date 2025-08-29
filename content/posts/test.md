---
title: "Risk Neutral Density in the Black-Scholes Model: Introduction"
date: 2025-08-28T15:18:00+09:00
draft: false
author: "Jisu Bang"
tags: ["BSM", "Risk Neutral Density"]
categories: ["금융"]
summary: "이 글은 Black Scholes Nodel에서의 Risk Neutral Density에 관한 글입니다."
math: true
# 대표 이미지 설정
cover:
    image: "/images/stonk.png" # static/images 폴더에 이미지를 넣어야 합니다.
    alt: "포스트 대표 이미지에 대한 설명"
    caption: "이미지 아래에 표시될 캡션"
---

## Brownian Motion

$$dX_t = \mu dt + \sigma dW_t$$

브라운 운동은 미분이 불가능하다. 

$$\lim_{dt \to 0} \frac{W(t+dt) - W(t)}{dt} = \lim_{dt \to 0} \frac{\Delta W(t, t+dt)}{dt}$$

여기서 $$\Delta W(t, t+dt) \sim \mathcal{N}(0, dt)$$ 이며,따라서,

$$\frac{\Delta W(t, t+dt)}{dt} = \frac{\sqrt{dt} \cdot Z}{dt} = \frac{1}{\sqrt{dt}}Z \quad \text{, where } Z \sim \mathcal{N}(0,1)$$이다.

위 식에서 $$dt \to 0$$극한을 취하면 $$frac{1}{\sqrt{dt}}$$은 무한대로 발산한다. 따라서 브라운 운동의 변화량은 단일 값으로 수렴하지 않고 발산하게 된다. 

