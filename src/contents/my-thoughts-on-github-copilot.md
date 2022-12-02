---
author: Joseph Cano
datetime: 2022-12-01T02:44:14Z
title: My Thoughts on Github Copilot
slug: "my-thoughts-on-github-copilot"
featured: true
draft: false
tags:
  - advice
  - github
  - productivity
ogImage: ""
description:
  "I've been using Github Copilot full time over the past month and have collected my thoughts on this new industry redefining tool. It's a product that has the potential to impact my life greatly and a product that's a mix of helpful, clumsy and potentially dangerous. Let's dive into some of the good and bad parts of Copilot"
---

<div style="text-align:center;margin-bottom:1rem;">
  <img src="https://i.blogs.es/c22105/github-copilot-1/1366_2000.jpeg"/>
</div>

I've been using Github Copilot full time over the past month and have collected my thoughts on this new industry redefining tool. It's a product that has the potential to impact my life greatly and a product that's a mix of helpful, clumsy and potentially dangerous. Let's dive into some of the good and bad parts of Copilot

<hr/>

## Table of Contents

## The $10 Price Point is Perfect, and It Makes Me Mad

The pricing model for Copilot is my favorite part. $10/month doubles my GitHub costs. That’s almost one Netflix… to have tab completion!? $10/month for copy-pasta from StackOverflow? No way.

On the other hand, if you asked me, *“For ~$100/year, I can make coding a little easier. Do you want that?”* I am an unequivocal “Hell yes.” For **27¢/day** I can have a robot buddy help me write code? Even if it’s only a little helpful, that’s worth it relative to what I earn… but the critical question is, does it work as advertised?

## I’ve Never Hit the Esc Key More in My Life

Copilot is noisy and attempts to insert itself in the conversation whenever there’s a pause in coding. Sometimes Copilot is magical, effortlessly finishing an entire block of code on my behalf. And sometimes, Copilot is like one of those “Garth and Kat” SNL sketches where Fred Armisen and Kristin Wiig attempt to sing totally improvised songs in unison…

<iframe width="736" height="414" src="https://www.youtube.com/embed/zaCNscXD9GU" title="Weekend Update: Garth and Kat Sing Spring Songs - SNL" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

I find Copilot has a low accuracy specifically around closing brackets and parenthesis, so with Copilot I hit escape to cancel suggestions a lot. This seems like an area Copilot should succeed, but Copilot routinely adds extra brackets and prematurely closes objects, functions, and arrays. Those situations are frustrating.

This accuracy problem might get solved over time. Other people on my team have had similar experiences, so it seems not isolated to me, but maybe it’s related to our setup. Muscle memory plays a part too. Copilot could be like an instrument where you get better at it over time. Maybe I could find a situation where Copilot does succeed…

## Can Copilot Automate Borign Tasks?

I thought writing tests would be a good task for Copilot. I don’t like writing tests, maybe Copilot does? After typing test( for an Alert component, Copilot suggested…

```js
test('renders the correct markup with props', () => {
  const wrapper = shallowMount(Alert, {
    propsData: {
      type: 'error',
      message: 'This is an error message'
    }
  })
  expect(wrapper.element).toMatchSnapshot()
})
```

Great job, Copilot… but watch out! The use of toMatchSnapshot() introduced more overhead than what I was going for at the time. I also didn’t have message prop in my Alert component, so that was wrong and confused me for a bit. And the test could be a bit simpler. After some editing, the final test for rendering an error Alert looked like this:

```js
test('renders the correct markup with type=error', async () => {
  await wrapper.setProps({ type: 'error' })
  expect(wrapper.classes()).toContain('error')
})
```

I don’t expect a robot to know the only changes in `<Alert type="error">` is a class="error" on the element or that we had already setup a wrapper in a beforeEach function, but…

To Copilot’s credit, it did write a passing test; it just wasn’t the best test. I’ll still call this a win because a lot of testing is about getting started. Copilot seems good at summoning tests out of its butt much faster than I can, so I consider this a success.

## Is Copilot Bad for the Industry?

There’s a lot of FUD (fear, uncertainty, and doubt) about Copilot being bad for the industry. I don’t want to dismiss genuine concerns, but here’s some of my thoughts on the common concerns raised.

1. **Copilot creates lazy programmers.** Sure, I guess, but I sort of got into programming because I am lazy. If a robot can make me more lazy, that seems like a win. The nuance here is that you still need to be a good programmer to know if what the machine generates is (both stylistically and morally) good code.
2. **This will spread bad code.** I agree with this point, Copilot has the potential to efficiently produce bad code to the extent that I wonder if the next twenty years of programming might be undoing AI-generated code.
3. **Licensing is a big problem.** Theoretically, if humans trained Copilot on GPL code and injects a single line of GPL code into my software, then technically that means my entire application became GPL and I need to open source it all. Yikes. How do we quality control this? Does each line of machine-generated code need to come with a license? This is unsustainable at best. A few months in, I have no idea what lines of code were authored by me or by the machine. IANAL, but what I hope happens is that we’re catapulted into a new era of software licensing where code becomes an open commons.
4. **AI is coming for my job.** AI **IS** growing at an exponential rate. It wasn't so long ago when the closest we had to AI was the autocomplete in our phones. Nowdays, with tools like Midjourney or Dall-e, we can generate incredible images with just text prompts. If AI can replace artists, the embodiment of the human creativity, where does that leave us programmers? Universal Basic Income, hopefully, but beyond that, I started looking for non-Doomsday scenarios with AI where it augments work for the better. My favorite example was this [Behind the Scenes look at the how Into the Spiderverse used AI to automate the creation of wrinkle lines](https://youtu.be/l-wUKu_V2Lk?t=341) to help express emotion.

It’ll be interesting to watch what happens on these fronts. What’s most interesting is that we’re no longer talking about AI programming in a theoretical sense, it’s here now. It’s getting better. We’re at the singularity. That’s fascinating to think about, but let me share the biggest shift I experienced while using Copilot.

## The Writing Code → Reviewing Code Shift

My biggest adjustment with using Copilot was that instead of writing code, my posture shifted to reviewing code. Rather than a free form solo-coding session I was now in a pair-programming session with myself (ironically) in the copilot seat reviewing. I kept having a verbal conversation with myself…

> Okay… <br/>
Do I like that?<br/>
Is that right?<br/>
It’s probably good enough.<br/>
That will have to be fixed.

That shift in posture change was enough to make me not like Copilot at first. I want to write code, not read code, dammit! Blast, you infernal machine! This activity is about me writing code, not me approving changes… but then I started to get over my ego a bit.

Identifying the shift in posture allowed me to start enjoying Copilot. The end goal of programming is working software and the robot can suggest code faster than I can write code. Yielding to that dynamic creates a fundamental shift in programming…

## Programming is now a game

Now when I sit down to write a block of code, I imagine that block of code in my brain. Then I start typing and Copilot starts guessing. Programming is now a game to see if Copilot matches that block of code in my head.

Sometimes Copilot gets this comically wrong. But…

When Copilot is in the ballpark of what I imagined in my brain, it feels wonderful. A mind-reading robot, how incredible! Zoltar, the magnificent! The robot’s suggestion reinforces my intuition and makes me feel that I’m on a right path because this robot (who was trained on billions of lines of code from hundreds of thousands of developers) arrived at near the same answer as me. That is a reassuring feeling.

For now, I’m in on Copilot. They have my $100. I look forward to seeing where this future is headed.
