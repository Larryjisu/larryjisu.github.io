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



## Taylor Expansion with Normal Function


테일러 전개(Taylor Expansion)은 함수를 근사해주는 도구로 사용한다. 일반적인 함수 $f(x)$의 변화량 $df$를 테일러 전개로 표현하면 다음과 같다.

$$
df = f'(x)dx + \frac{1}{2}f''(x)(dx)^2 + \dots
$$

테일러 전개에서 주목할 점은 $(dx)^2$와 같은 아주 작은 변화인의 값은 너무나 작은 값이므로 무시가 가능하다는 사실이다. 그 덕분에 어떤 함수의 변화량에 대한 근사를 단순히 $df \approx f'(x)dx$ 라고 표기할 수 있다. 


## Taylor Expansion with Stochastic Process

앞에서 '일반적인'함수의 경우, 테일러 전개로 그 값을 근사할 수 있다고 말하였다.하지만  어떤 함수가 확률과정(stochastic process)를 따른다면 우린 테일러 전개로 해당 함수를 더이상 근사할 수 없다. 그 이유는 확률과정의 변화량은 단일 값으로 수렴하지 않으며 발산하기 때문이다. 이를 수식으로 표기해보면 다음과 같다.

$$\lim_{dt \to 0} \frac{W(t+dt) - W(t)}{dt} = \lim_{dt \to 0} \frac{\Delta W(t, t+dt)}{dt} = \lim_{dt \to 0} \frac{\sqrt{dt} \cdot Z}{dt} =  \lim_{dt \to 0} \frac{1}{\sqrt{dt}}Z, \quad (Z \sim \mathcal{N}(0,1)) $$

$ dt \to 0 $일 때 $ \frac{1}{\sqrt{dt}} \to \infty $이기에 무한으로 발산해버린다. 이러한 사실은 그래프로도 확인할 수 있다. 확률과정의 대표적 예시인 브라운 운동은 거의 확실히(almost surely) 연속이지만 미분이 불가능하다.
![이미지](/images/bm.png "BM")

따라서 $dx^2$항은 무시할 수 있다는 일반 테일러 전개가 적어도 확률과정에선 통하지 않는다. 그렇다면 확률과정이 갖는 무작위성은 어떻게 통제가 가능할까?

## Itô's Lemma

놀랍게도 브라운 운동에 제곱을 씌우면 그 값은 dt로 수렴하며 무작위성이 통제된다. 브라운 운동$(dW_t)$은 무작위 걸음(random walk)이지만 브라운 운동의 제곱$(dW_t^2)$은 dt가 된다.
$$(dW_t)^2 = dt$$

이제는 어떤 확률과정$f(t,W_t)$에 대한 근사가 가능해진다. 

$$
df = \frac{\partial f}{\partial t}dt + \frac{\partial f}{\partial W_t}dW_t + \frac{1}{2}\frac{\partial^2 f}{\partial W_t^2}(dW_t)^2 + \dots
$$


$$
df = \left(\frac{\partial f}{\partial t} + \frac{1}{2}\frac{\partial^2 f}{\partial W_t^2}\right)dt + \frac{\partial f}{\partial W_t}dW_t
$$
