<template>
  <h1>HOUSES PAGE</h1>
</template>


<script>
import Pop from "../utils/Pop.js";
import {computed, onMounted} from 'vue'
import { housesService } from "../services/HousesService.js";
import { AppState } from "../AppState.js";

export default {
   setup(){
    async function getHouses(){
      try {
        await housesService.getHouses()
      } catch (error) {
        Pop.error(error)
      }
    }


    onMounted(() => {
      getHouses()
    })


    return {
      houses: computed(() => AppState.houses)
    }
  }
}
</script>


<style lang="scss" scoped>

</style>