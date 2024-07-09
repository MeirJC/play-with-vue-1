<script setup lang="ts">
import { ref } from 'vue'

const count = ref(0)
const increment = () => count.value++
const decrement = () => (count.value > 0 && count.value--)

const tasks = ref<string[]>(["Buy Milk", "Make Coffee", "Learn Vue", "Build Awesome Apps"])

const newTask = ref<string>("")

const addTask = () => {
  tasks.value.push(newTask.value)
  newTask.value = ""
}

</script>

<template>
  <main class="font-mono text-xl bg-neutral-900 text-amber-400 min-h-dvh">
    <h1 class="flex items-center justify-center gap-6 py-12 text-6xl text-center">Hello
      <img src='./assets/logo.svg' alt="Vue JS" width="48px" height="48px"
        class="inline w-20 drop-shadow-[0_20px_50px_rgba(8,_112,_184,_0.7)]">
    </h1>
    <section class="container flex flex-col items-center justify-center w-full h-full gap-4">
      <!--  -->
      <h2 class="pt-4 font-mono text-3xl font-light tracking-wider">Counter</h2>
      <div
        class="flex items-center justify-center w-full max-w-3xl gap-4 p-2 border rounded-md md:gap-6 border-amber-300/20">
        <button
          class="w-full py-2 text-2xl font-bold transition-colors duration-300 border rounded-md min-w-24 border-amber-300 hover:bg-neutral-500/40"
          @click="increment">+</button>
        <p class="text-2xl whitespace-nowrap">Count is {{ count }}</p>
        <button
          class="w-full py-2 text-2xl font-bold transition-colors duration-300 border rounded-md min-w-24 border-amber-300 hover:bg-neutral-500/40"
          @click="decrement">−</button>
      </div>
      <!--  -->
      <h2 class="pt-4 font-mono text-3xl font-light tracking-wider">Task List</h2>
      <div
        class="flex flex-col items-center justify-center w-full max-w-3xl gap-4 p-2 border rounded-md md:gap-6 md:flex-row border-amber-300/20">
        <ul class="w-full divide-y-2">
          <li v-for="task in tasks" :key="task" class="flex items-center justify-between p-2 border-amber-300/20">
            <span>{{ task }}</span>
            <button class="text-sm text-amber-400" @click="tasks.splice(tasks.indexOf(task), 1)">❌</button>
          </li>
          <li v-if="tasks.length === 0" class="flex items-center justify-between p-2 border-amber-300/20">
            <span>No more tasks 🤓</span>
          </li>
        </ul>
        <input v-model="newTask" @keyup.enter="addTask" type="text"
          class="w-full p-2 transition-colors duration-300 border rounded-md border-amber-300/20 bg-neutral-900 text-amber-400 placeholder:text-amber-500/70 focus:outline-none focus:border-amber-400/85 focus:border-2 hover:border-amber-400/50"
          placeholder="Add a new task" />
      </div>
    </section>
  </main>
</template>
