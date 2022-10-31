<script setup>
import Letter from './components/Letter.vue'
import mail_svg from '../public/mail_email_message_electronic_online_web_icon-icons.com_59986.svg'
import telegram_svg from '../public/telegram_logo_icon_144811.svg'
import WorkExperience from './components/WorkExperience.vue';

const stackData = [
  'Vue ✌️',
  'React ⚛️',
  'TypeScript 📜',
  'SASS / Tailwind 💅',
  'JS ES6 + 💪',
  'Zustand, Pinia 🍍'
]

</script>

<template>
  <main>
    <section>
      <h1 class="glow">Plotnikov Vladimir</h1>
    </section>
    <section>
      <p>
        Hello 👋! I'm a
        <span>Frontend Developer</span> and <span>UI Designer</span>
        based in Karaganda.
      </p>
    </section>
    <section class="links_wrapper">
      <a class="link" href="mailto:vladimirplotnikovkz@gmail.com">
        <span>Email</span>
        <img :src="mail_svg" alt="📧" />
      </a>
      <a class="link" href="https://t.me/Voloduhe">
        <span>Telegram</span>
        <img :src="telegram_svg" alt="✈️" />
      </a>
    </section>
    <div class="canvas_wrapper">
      <Letter />
    </div>
  </main>
  <div class="info_wrapper">
    <div class="custom-shape-divider-top-1666469643">
      <svg data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 120" preserveAspectRatio="none">
        <path
          d="M321.39,56.44c58-10.79,114.16-30.13,172-41.86,82.39-16.72,168.19-17.73,250.45-.39C823.78,31,906.67,72,985.66,92.83c70.05,18.48,146.53,26.09,214.34,3V0H0V27.35A600.21,600.21,0,0,0,321.39,56.44Z"
          class="shape-fill" fill="#161719"></path>
      </svg>
    </div>
    <div class="info">
      <section>
        <h1>Stack</h1>
      </section>
      <ul>
        <li v-for="stack in stackData" :key="stack">
          {{ stack }}
        </li>
      </ul>
      <section>
        <h1>Work experience</h1>
      </section>
      <div class="job_container">
        <WorkExperience />
      </div>
    </div>
  </div>
</template>

<style scoped lang="sass">
.canvas_wrapper
  height: 256px

.job_container
  width: 100%
  display: flex
  align-items: center
  justify-content: center
  position: relative

.info_wrapper
  position: relative
  background: #2c3337
  padding-top: 100px

  .info
    display: flex
    flex-direction: column
    align-items: center
    gap: 32px
    justify-content: center
    color: #c5c8c6
    padding: 20px


    ul
      font-size: 24px

      display: flex
      gap: 20px

      li
        background: #4056A1
        color: #c5c8c6
        padding: 6px 24px
        border-radius: 50px
        display: flex
        justify-content: center

        border: 1px solid rgba(255, 255, 255, 0.2)



  .custom-shape-divider-top-1666469643
    position: absolute
    top: 0
    left: 0
    width: 100%
    overflow: hidden
    line-height: 0
    
.links_wrapper
  width: 100%
  display: flex
  gap: 40px

  .link
    display: flex
    align-items: center
    justify-content: center
    padding: 5px
    position: relative
    transition: all 200ms

    

    span
      z-index: 1
    
    &::before
      content: ''
      position: absolute
      top: 0
      left: 0
      width: 0%
      height: 100%
      background: #6587fc

      z-index: 0
      transition: all 200ms

      

    &:hover
      &::before
        width: 100%
        box-shadow: 0 0 100px #94acff
        transition: all 200ms
      img
        filter: invert(0)
      color: #000000

    &:last-child
      &::before
        background: #e00c03
      &:hover
        &::before
          box-shadow: 0 0 100px #e05f5a

    img
      filter: invert(1)
      height: 20px
      width: 20px
      margin-left: 10px

main
  height: 100vh
  display: flex
  flex-direction: column
  align-items: center
  gap: 32px
  justify-content: center
  color: #c5c8c6
  padding: 20px



section
  display: flex
  justify-content: center
  text-align: center

  h1
    font-size: 48px
    font-family: 'DM Serif Display', serif

  p
    font-size: 24px




.glow
  background: linear-gradient(90deg, #6587fc, #ff9787, #EFE1BA)
  background-clip: text
  -webkit-background-clip: text
  color: transparent




@media (max-width: 1300px)
  .info
    ul
      flex-direction: column
</style>
