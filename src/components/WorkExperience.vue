<script setup lang="ts">
import JobCard from './JobCard.vue';
import { formatDistance, format, isToday } from 'date-fns'

const jobData = [
  {
    heading: 'Frontend developer',
    company: 'AO Satty Zhuldyz (joint stock company)',
    content: "i don't know)",
    //date: 'November 2022 - present',
    date: {
      start: new Date(2022, 10, 1),
      end: new Date()
    },
    id: 0
  },
  {
    heading: 'Junior Frontend developer',
    company: 'OOO TRANSMASH (limited liability company)',
    content: 'Frontend for control panel for an AI in security and CCTV systems. User interface design. Real-time capturing and 2D visualization in schematic way using data from camera.',
    //date: 'December 2021 - September 2022',
    date: {
      start: new Date(2021, 11, 1),
      end: new Date(2022, 8, 1)
    },
    id: 1
  },
  {
    heading: 'HTML, CSS developer',
    company: 'Freelance',
    content: 'Single page websites in HTML, CSS, JS for animation.',
    //date: 'January 2021 - July 2021',
    date: {
      start: new Date(2021, 0, 1),
      end: new Date(2021, 6, 1)
    },
    id: 2
  },
]

interface IDateObj {
  start: Date
  end: Date
}

function calculateDate(dateObj: IDateObj): string {
  const { start, end } = dateObj
  const distance = formatDistance(start, end)
  const dates = `${format(start, 'MMM yyyy')} - ${isToday(end) ? 'present' : format(end, 'MMM yyyy')}`
  return `${dates} (${distance})`
}

console.log(calculateDate(jobData[0].date))


</script>

<template>
  <div class="timeline">
    <ul>
      <li v-for="job in jobData">
        <JobCard :company="job.company" :content="job.content" :heading="job.heading" :key="job.company"
          :date="calculateDate(job.date)" />
        <div v-if="job.id !== 2" class="line_wrapper">
          <div class="line"></div>
        </div>
      </li>
    </ul>
  </div>
</template>

<style lang='sass' scoped>
.timeline
  width: 80%
  max-width: 800px
  margin: 0 auto
  position: relative

  ul
    li
      margin-bottom: 20px

      &:last-child
        margin-bottom: 0

@media (max-width: 767px)
  .timeline
    .line_wrapper
      margin-top: 20px
      height: 80px
      display: flex
      justify-content: center
      .line
        height: 100%
        width: 2px
        background: #c5c8c6
        border-radius: 5px
        position: relative

        &::after
          content: ''
          background: #c5c8c6
          width: 15px
          height: 15px
          border-radius: 50%
          position: absolute
          top: 50%
          left: -6.5px
          
          transform: translateY(-50%)

@media (min-width: 768px)
  .timeline
    &::before
      content: ''
      position: absolute
      height: 100%
      width: 2px
      background: #c5c8c6
      border-radius: 5px
      left: 50%
      transform: translateX(-50%)

    ul
      li
        width: 50%
        margin-bottom: 50px

        &::after
          content: ''
          position: absolute
          width: 15px
          height: 15px
          background: #c5c8c6
          border-radius: 50%
          top: 50%


        &:nth-child(odd)
          float: left
          clear: right
          transform: translateX(-20px)

          &::after
            right: -27.5px
          
        &:nth-child(even)
          float: right
          clear: left
          transform: translateX(20px)

          &::after
            left: -27.5px
  

</style>