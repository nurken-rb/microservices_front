<script setup>

import {onBeforeMount, onMounted, ref} from "vue";

const currentDateTime = ref(null);
const date = ref(null)
const time = ref(null)

function updateTime() {
  currentDateTime.value = new Date()
  date.value = currentDateTime.value.toDateString()
  time.value = currentDateTime.value.toLocaleTimeString(
    [],
    {
      hour12: false
    }
  )

}

onBeforeMount(() => {
  updateTime()
})

onMounted(() => {
  setInterval(updateTime, 1000)
})

</script>

<template>
  <div class="datetime">
    <div class="time">
      <div class="time__inner">
        <span>{{ time }}</span>
      </div>
    </div>
    <div class="date">
      <span>{{ date }}</span>
    </div>
  </div>
</template>

<style scoped>

.datetime {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.time {
  margin-top: 20%;
}

.time__inner {
  font-family: Arial, sans-serif;
  font-weight: bold;
  font-size: 8rem;
  font-weight: bold;
  color: #469546;
}

.date {

}

</style>
