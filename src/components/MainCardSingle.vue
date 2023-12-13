<script setup>
  import { ref } from 'vue'
  import { faker } from '@faker-js/faker'

  import useAPI from '@/composables/useAPI'
  //const { getVehicles } = useAPI()

  const selectCard = () => {
    console.log(`${props.vehicle.make} selected`)
  }

  const props = defineProps({
    vehicle: {
      type: Object,
      required: true,
      default: () => {
        return {
          vehicleId: '123',
          make: 'John Doe',
          model: 'A55',
          year: '2007',
          color: 'White',
          image: 'https://www.example.com'
        }
      },
    },
  })

  //const departmentResponse = await getDepartment(props.vehicle.departmentId)
  //const department = ref(departmentResponse)
</script>

<template>
  <RouterLink v-if="props.vehicle.vehicleId" :to="`/api/vehicles/${props.vehicle.vehicleId}`">
  <div class="card" @click="selectCard">
    <div class="card-image">
      <img :src="props.vehicle.image" alt="" srcset="" />
    </div>
    <div class="card-details">
      <p class="card-details-make font-preahvihear" font-bold>{{ props.vehicle.make }}</p>

    </div>
  </div>
  </RouterLink>
</template>

<style scoped lang="postcss">
  .card {
    @apply cursor-pointer overflow-hidden rounded-md p-8 shadow-md transition-transform duration-300 hover:scale-110 hover:shadow-2xl hover:shadow-slate-900;
    &-image {
      img {
        @apply mx-auto rounded-full object-contain;
      }
    }
    &-details {
      @apply flex flex-col gap-2  pt-6 text-center;
      &-name {
        @apply text-4xl  text-black ;
      }
      &-job {
        @apply -mt-2 text-xs font-bold text-yellow-700;
      }
      &-quote {
        @apply pt-4 text-lg italic text-slate-800;
      }
    }
  }
</style>