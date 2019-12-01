<template>
  <section id="plans">
      <div class="container">
          <SelectYear />
          <OptionPlans />
      </div>
  </section>
</template>

<script>
import SelectYear from './SelectYear.vue'
import OptionPlans from './OptionPlans'

export default {
    components: {
        SelectYear,
        OptionPlans
    }
}
</script>

<style>

</style>