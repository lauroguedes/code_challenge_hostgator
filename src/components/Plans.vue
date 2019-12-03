<template>
  <section id="plans">
      <div class="container">
          <SelectYear @option-cycle="sendCycleOptionPlans" />
          <OptionPlans :cycle="getCycle" :promo-code="promoCode" />
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
    },
    data() {
        return {
            getCycle: '',
            promoCode: 'PROMOHG40'
        }
    },
    methods: {
        sendCycleOptionPlans(payload) {
            //console.log('Ciclo - ' + payload.cycle);
            this.getCycle = payload.cycle
        }
    }
}
</script>

<style>

</style>