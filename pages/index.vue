<template>
    <div>
      <div style="margin: 1rem 0">
        <PiniaLogo />
      </div>
  
      <p>
        This is an example store to test out devtools. Try one of the following
        with the devtools open:
        <br />
      </p>
  
      <ol>
        <li>Use the different increment actions</li>
        <li>Change the counter directly from the devtools</li>
        <li>Use decrement to zero to see how action groups work</li>
        <li>
          Click
          <b>Test Errors</b> and immediately after <b>increment</b> the store
        </li>
        <li>
          While the dev server is running, try changing counter.changeMe, adding,
          and removing new state properties
        </li>
      </ol>
  
      <h2>Counter Store</h2>
  
      <p data-testid="counter-values">
        Counter: {{ counter.n }}. Double: {{ counter.double }}
      </p>
  
      <p>Increment the Store:</p>
  
      <PinButton @click="counter.increment()" data-testid="increment">+1</PinButton>
      <PinButton @click="counter.increment(10)">+10</PinButton>
      <PinButton @click="counter.increment(100)">+100</PinButton>
      <PinButton @click="counter.n++">Direct Increment</PinButton>
      <PinButton
        @click="
          counter.$patch((state) => {
            state.n++
            state.incrementedTimes++
          })
        "
      >
        Direct patch
      </PinButton>
  
      <p>Other actions:</p>
  
      <PinButton @click="counter.fail">Test Errors</PinButton>
      <PinButton @click="counter.decrementToZero()">Decrement to zero</PinButton>
      <PinButton @click="counter.changeMe()">
        <code>counter.changeMe()</code>
      </PinButton>
  
      <hr />
  
      <p>
        Complete store state via
        <code>store.$state</code>:
      </p>
  
      <pre>{{ counter.$state }}</pre>
    </div>
  </template>
  
  <script setup lang="ts">
  import PiniaLogo from '~/components/PiniaLogo.vue'
  
  const counter = useCounter()
  
  
  </script>
  
  <style scoped>
  .storybook-button {
    margin-right: 0.1rem;
    margin-bottom: 0.5rem;
  }
  </style>
  