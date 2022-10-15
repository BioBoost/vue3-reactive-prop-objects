<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps({
  counter: { type: Number, required: true },
  counterObject: { type: Object, required: true },
});

const internalCounter = ref(props.counter);
const internalCounterObject = ref(props.counterObject)

// Damn:

// Mutating Object / Array Props#
// When objects and arrays are passed as props, while the child component cannot mutate the prop binding, it will be able to mutate the object or array's nested properties. This is because in JavaScript objects and arrays are passed by reference, and it is unreasonably expensive for Vue to prevent such mutations.

// The main drawback of such mutations is that it allows the child component to affect parent state in a way that isn't obvious to the parent component, potentially making it more difficult to reason about the data flow in the future. As a best practice, you should avoid such mutations unless the parent and child are tightly coupled by design. In most cases, the child should emit an event to let the parent perform the mutation.

</script>

<template>
  <div style="background-color: palegoldenrod;padding:12px">
    <h2>Inside the component</h2>
    <p>
      Prop Counter: {{ props.counter}}
    </p>
    <p>
      Internal Counter: {{ internalCounter }}
    </p>
    <p>
      Prop Object Counter: {{ props.counterObject.counter}}
    </p>
    <p>
      Internal Object Counter: {{ internalCounterObject.counter }}
    </p>
    <div>
      <button @click="internalCounter++">CounterNow: Add one to Internal Counter</button><br />
      <button @click="internalCounterObject.counter++">CounterNow: Add one to Internal Object Counter</button>

      <!-- Luckily enough this cannot be done -->
      <!-- <btn @click="props.counter++">CounterNow: Add one to Props Counter</btn> -->
    </div>
  </div>
</template>