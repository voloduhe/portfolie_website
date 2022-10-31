<script setup>

const props = defineProps({
  heading: String,
  content: String,
  company: String,
  date: String
})

function move(event) {
  const { currentTarget: target } = event

  const rect = target.getBoundingClientRect()
  const [x, y] = [event.clientX - rect.left, event.clientY - rect.top]

  target.style.setProperty('--mouseX', `${x}px`)
  target.style.setProperty('--mouseY', `${y}px`)
}


</script>

<template>
  <p class="job_date">{{ props.date }}</p>
  <div class="job_wrapper" @mousemove="move">
    <h2 class="job_heading">{{ props.heading }}</h2>
    <h3 class="job_company">{{ props.company }}</h3>
    <p class="job_content">{{ props.content }}</p>
  </div>
</template>

<style lang='sass' scoped>
.job_date
  margin-bottom: 8px
  margin-left: 20px
  color: rgba(255, 255, 255, 0.3)
  font-size: 14px
.job_wrapper
  background: #4056A1
  border-radius: 12px
  border: 1px solid rgba(255, 255, 255, 0.3)
  padding: 16px
  color: #c5c8c6
  position: relative

  &:hover
    &::before
      opacity: 1

  &::before
    content: ''
    border-radius: inherit
    height: 100%
    width: 100%
    position: absolute
    left: 0
    top: 0

    background: radial-gradient(600px circle at var(--mouseX) var(--mouseY), rgba(255, 255, 255, 0.1), transparent 40%)
    opacity: 0
    z-index: 2

    transition: opacity 500ms

  .job_heading
    font-size: 24px

  .job_company
    color: rgba(255, 255, 255, 0.4)
    font-size: 14px
    margin-bottom: 16px
</style>