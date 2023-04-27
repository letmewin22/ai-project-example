<script setup lang="ts">
import gsap from 'gsap'
import ScrollTrigger from 'gsap/ScrollTrigger'
// import disorder from '@ignatiusmb/scramble'

import { pageTransition } from '~~/assets/scripts/transition'

gsap.registerPlugin(ScrollTrigger)

definePageMeta({
  pageTransition,
})

const $el = ref(null)
// const $decoder = ref(null)

onMounted(() => {
  // disorder.interval = 100
  // disorder($decoder.value)

  const tl = gsap.timeline()
  const tl2 = gsap.timeline({
    defaults: {
      ease: 'linear.none',
    },
  })

  ScrollTrigger.create({
    trigger: $el.value,
    start: () => 'top top',
    end: () => 'bottom-=60% bottom',
    scrub: true,
    pin: false,
    pinSpacing: false,
    animation: tl,
  })

  ScrollTrigger.create({
    trigger: $el.value,
    start: () => 'top+=30% top',
    end: () => 'bottom bottom',
    scrub: true,
    pin: false,
    pinSpacing: false,
    animation: tl2,
  })

  ScrollTrigger.create({
    trigger: $el.value,
    start: () => 'top top',
    end: () => 'bottom bottom',
    scrub: true,
    pin: true,
    pinSpacing: false,
    anticipatePin: 1,
    markers: false,
    // animation: tl2,
  })

  const $square = document.querySelector('.big-square') as HTMLElement

  if (window.innerWidth > window.innerHeight) {
    $square && ($square.style.width = window.innerWidth + 'px')
    $square && ($square.style.height = window.innerWidth + 'px')
  } else {
    $square && ($square.style.width = window.innerHeight + 'px')
    $square && ($square.style.height = window.innerHeight + 'px')
  }

  tl2.to(
    '.big-square',
    {
      duration: 1,

      rotationX: 0,
      rotationY: 0,
      scale: 1,
      // y: '-100%',
      // ease: 'none',
    },
    0
  )

  tl.to(
    '.pin-wrapper',
    {
      duration: 1,
      x: '-100vw',
    },
    0
  )

  tl.to(
    '.s-1__jaw',
    {
      duration: 1,
      x: '95vw',
      opacity: 0,
    },
    0
  )

  tl.to(
    '.h1__text--1',
    {
      duration: 1,
      x: '100vw',
      // y: '-100%',
      // ease: 'none',
    },
    0
  )

  tl.to(
    '.h1__text--2',
    {
      duration: 1,
      x: '95vw',
    },
    0
  )

  tl.to(
    '.h1__text--3',
    {
      duration: 1,
      x: '98vw',
    },
    0
  )
})
</script>

<template>
  <main>
    <div ref="$el" class="pin-wrapper" style="height: 1500vh">
      <section class="section s-1">
        <div class="container s-1__container">
          <div class="s-1__jaw">
            <span>Trust us, it's a game-changer!</span>
            <span
              ><svg
                width="14"
                height="13"
                viewBox="0 0 14 13"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M11.602 0L13.002 1.4L3.40195 11L12.002 11V13L0.00195312 13L0.00195313 1H2.00195L2.00195 9.6L11.602 0Z"
                  fill="#FFFAF9"
                />
              </svg>
            </span>
          </div>
          <h1 class="h1 s-1__h1">
            <span class="h1__text h1__text--1">Unlock your</span>
            <span class="h1__text h1__text--2">Productivity</span>
            <span class="h1__text h1__text--3">
              with <span class="h1__hl-text">AI Tools...</span>
            </span>
          </h1>
          <!-- <div ref="$decoder" class="decoder-screen">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Quibusdam
            necessitatibus atque ullam magni nihil error alias ipsam eaque est,
            optio fugiat, dolorem incidunt nobis, voluptatibus eius. Odit, iusto
            consequatur, harum rem expedita excepturi eius qui, explicabo dolore
            unde repellendus cupiditate eos maxime itaque nam temporibus magni
            in sapiente velit quidem dolorum veritatis hic. Quam dolores
            voluptas, nostrum repellat incidunt rem quibusdam tempore quaerat
            quos perspiciatis ea velit quas illo sed iste maiores consequuntur
            perferendis enim, sint a provident eos neque inventore. Explicabo
            odio repudiandae, enim inventore quos maxime? Similique explicabo in
            minus, illum sequi dicta itaque omnis culpa nam aut.
          </div> -->

          <div class="s-1__window">
            <div class="s-1__window-content">
              <p>
                Hey there! Ready to take your digital game to the next level?
                Artificial intelligence (AI) is here to help!
              </p>
              <p>
                With AI-powered tools, you can automate tedious tasks, gain
                insights into customer behavior, and optimize workflows to
                achieve better results.
              </p>
              <p>
                AI tools can make your life easier by streamlining manual tasks
                and freeing up time for more creative and innovative pursuits.
                Plus, they can provide data-driven insights that would be
                difficult to obtain otherwise.
              </p>
            </div>
          </div>
        </div>
      </section>
    </div>
    <div class="big-square"></div>
    <section class="section section--nm s-2">
      <div class="container s-2__container">
        <div class="s-2__left">
          <div class="s-2__left-wrapper">
            <h2 class="s-2__h">Marie</h2>
            <p class="s-2__occupation">a freelance writer</p>
          </div>
          <p class="s-2__desc">
            used Grammarly to catch errors and improve the quality of her
            writing
          </p>
        </div>
        <div class="s-2__right">
          <div class="s-2__right-wrapper">
            <blockquote class="s-2__quote">
              So, you've decided to use AI tools, but which one is right for
              you? The answer depends on the specific problem you're trying to
              solve. For instance, if you're looking to automate customer
              service, chatbots might be your best bet.
            </blockquote>
            <p class="s-2__details">(Punctuation checker) Plagiarism checker</p>
          </div>
          <div class="s-2__card-wrapper">
            <img class="s-2__card s-2__card--1" src="/card.jpg" alt="" />
            <img class="s-2__card s-2__card--2" src="/card.jpg" alt="" />
          </div>
        </div>
      </div>
    </section>
  </main>
</template>
