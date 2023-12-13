<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { useRoute } from 'vue-router'

import useAPI from '@/composables/useAPI';

const { fetchVehicle, currentVehicle } = useAPI()


const route = useRoute()

const vehicle = ref('')
onMounted(async () => {
  await fetchVehicle(route.params.id)
  console.log(route.params.id)
})

onUnmounted(() => {
 currentVehicle.value = null
})

</script>

<template>
  <main
    class="min-h-screen bg-gradient-to-b from-gray-500 to-black-300 font-preahvihear "
  >
    <div
      v-if="currentVehicle"
      class="flex flex-col items-center justify-center gap-6"
    >
      <img class="p-4 h-99 w-34"
        :src="currentVehicle.image"
        :alt="currentVehicle.make"
      />
      <h1 class="text-white-800 text-6xl font-bold">
        
        {{ currentVehicle.model }}
        
      </h1>

      <h1 class="text--400 text-3xl font-bold">
        
        {{ currentVehicle.color }}
        {{ currentVehicle.year }}
      </h1>
      
    </div>
  </main>
</template>


