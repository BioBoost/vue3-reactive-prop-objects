<script setup lang="ts">
import { ref } from 'vue';
import CounterNow from '@/components/CounterNow.vue'

const counter = ref(3);
const counterObject = ref({ counter: 5 })


</script>

<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div>
      <p>
        External Counter: {{ counter }}
      </p>
      <p>
        External Counter Object: {{ counterObject.counter }}
      </p>
      <div>
        <button @click="counter++">External: Add one to Counter</button><br />
        <button @click="counterObject.counter++">External: Add one to Object Counter</button>
      </div>
      <counter-now :counter="counter" :counter-object="counterObject"/>
    </div>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
}
</style>
