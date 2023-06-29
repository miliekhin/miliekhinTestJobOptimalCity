<script setup>
  import {ref} from "vue";
  let selectedItemIndx = ref(0);
  const items = ref([])
  const rndText = () => Math.random().toString(36).substring(2);
  for (let i = 0; i < 20; i++) {
    items.value.push(
        {
          'name': rndText(),
          'value': rndText(),
        }
    );
  }
</script>

<template>
  <h1 class="text-2xl pb-8">
    Привет!
  </h1>
  <form
   @submit.stop.prevent
   class="
   w-64
   pb-8
  "
  >
    <p class="pb-2">Name: {{items[selectedItemIndx].name}}</p>
    <label>Value:</label>
    <input
      v-model="items[selectedItemIndx].value"
      type="text"
      class="
        p-2
        w-64
        border-solid
        border-2
      "
    />
  </form>
  <main>
    <div
      v-for="(item, i) in items"
      :key="i"
      class="
        border-solid
        border-2
        border-indigo-200
        rounded-xl
        p-4
        my-2
        w-64
        hover:bg-indigo-100
        active:border-indigo-800
        cursor-pointer
      "
      :class="selectedItemIndx === i ? 'border-indigo-800 border-2' : ''"
      @click="selectedItemIndx = i"
    >
      <header>Name: {{item.name}}</header>
      <p>Value: {{item.value}}</p>
    </div>
  </main>
</template>

<style scoped>
</style>
