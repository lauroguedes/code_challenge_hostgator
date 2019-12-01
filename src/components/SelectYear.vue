<template>
  <div class="row">
      <div class="col-12 text-center">
          <div class="content-options">
            <div class="text">Quero pagar a cada:</div>
            <ul class="options">
                <li v-for="o in options" :key="o.id" :class="{active: o.key === optionSelected.key}">
                    <input type="radio" :id="o.key" :value="o" v-model="optionSelected">
                    <label :for="o.key">{{ o.name }}</label>
                </li>
            </ul>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    data() {
        return {
            options: [
                {
                    key: 'triennially',
                    name: '3 anos'
                },
                {
                    key: 'annually',
                    name: '1 ano'
                },
                {
                    key: 'monthly',
                    name: '1 mês'
                }
            ],
            optionSelected: {
                key: '3-year',
                name: '3 anos'
            }
        }
    },
    methods: {
        checkOption() {

        }
    }
}
</script>

<style lang="scss" scoped>
    .content-options {
        display: inline-block;
        color: scale-color($color: $primary-color, $lightness: 40%);
        .text {
            font-size: .8rem;
        }
    }
    .options {
        list-style: none;
        border: 1px solid scale-color($color: $primary-color, $lightness: 40%);
        background: white;
        box-shadow: 0 0 3px #ccc;
        border-radius: 50px;
        padding: 0;
        li {
            display: inline-block;
            margin-right: 1rem;
            padding: .5rem 1rem;
            border-radius: 50px;
            &:last-child {
                margin-right: 0;
            }
            &.active {
                background: scale-color($color: $primary-color, $lightness: 40%);
                color: white;
                transition: all .3s linear;
            }
            input + label{
                cursor: pointer;
            }
        }
    }
</style>