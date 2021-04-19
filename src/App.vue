<template>
  <div class="flex flex-col items-center justify-center min-h-screen space-y-6 min-w-screen bg-gradient-to-br from-gray-50 to-white">
      <div class="w-11/12 p-px shadow-inner 2xl:w-1/3 bg-gradient-to-br from-gray-100 to-white rounded-2xl">
        <div class="flex flex-col p-4 m-px bg-white rounded-xl">
            <h1 class="mb-8 text-4xl text-gray-900">Cully's Domains</h1>
            <ul class="space-y-5 font-mono text-gray-700">
                <li v-for="domain in state.domains">{{domain}}</li>
            </ul>
        </div>
      </div>
      <div>
            Interested? Email cully@hey.com
        </div>
  </div>
</template>

<script setup>
    import { onMounted, reactive } from 'vue';
    const state = reactive({
        domains: []
    })
    onMounted( async () => {
      const response = await fetch("https://domains.cully.workers.dev");
      state.domains = await response.json().then(data => data.sort());
    });
</script>

<style>

</style>
