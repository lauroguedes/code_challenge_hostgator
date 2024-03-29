<template>
  <div class="row">
      <carousel 
        :navigationEnabled="true" 
        :perPage="3" 
        :perPageCustom="[[320, 1], [768, 2], [970, 3]]"
        :minSwipeDistance="100"
        navigationNextLabel="<i class='fas fa-arrow-circle-right'></i>"
        navigationPrevLabel="<i class='fas fa-arrow-circle-left'></i>">
          <slide v-for="p in plans" :key="p.id">  
            <div :class="['col-12 plans', p.name == 'Plano M' ? 'plan-m' : '']">
                <div class="option-plan-header">
                    <div class="icon"></div>
                    <h2>{{ p.name }}</h2>
                </div>
                <div class="option-plan-body">
                    <div class="price-one">
                        <del>{{ price(p) | currency }}</del> <strong>{{ priceDiscount(p) | currency }}</strong>
                        <div>equivalente a</div>
                    </div>
                    <div class="price-two">
                        <span class="primary-color-light">R$</span>
                        <span class="text-xl">{{ priceCycle(p) | currency('') }}</span>
                        <span class="primary-color-light">/mes</span>
                    </div>
                    <div class="button-action">
                        <a target="_blank" :href="generateUrlContractNow(p)" :class="['btn', p.name == 'Plano M' ? 'btn-secondary' : 'btn-primary']">Contrate Agora</a>
                    </div>
                    <div class="price-three">
                            <p>
                                <strong>1 ano de Dominio grátis <i class="fas fa-info-circle primary-color-light"></i></strong>
                            </p>
                        <span class="primary-color-light">Economize {{ priceDifference(p) | currency }}</span>
                        <span class="badge-green">40% OFF</span>
                    </div>
                </div>
                <div class="option-plan-features">
                    <ul>
                        <li><span class="outline">Para 1 site</span></li>
                        <li><strong>100 GB</strong> de armazenamento</li>
                        <li><span class="outline">Contas de e-mail</span> <strong>Ilimitadas</strong></li>
                        <li>Criador de sites <strong>Grátis</strong></li>
                        <li>Certificado SSL <strong>Grátis</strong> (https)</li>
                    </ul>
                </div>
            </div>
          </slide>
      </carousel>
  </div>
</template>

<script>
import axios from 'axios'
import { Carousel, Slide } from 'vue-carousel';

export default {
    components: {
        Carousel,
        Slide
    },
    props: {
        cycle: String,
        promoCode: String
    },
    data() {
        return {
            plans: []
        }
    },
    mounted() {
        axios
            .get('https://7ac2b8ab-f3e5-4534-863d-90dd424a6405.mock.pstmn.io/prices')
            .then(response => (this.plans = response.data.shared.products))
    },
    methods: {
        price(plan) {
            return plan.cycle[this.cycle].priceOrder
        },
        priceDiscount(plan) {
            let price = plan.cycle[this.cycle].priceOrder
            return price * 0.4;
        },
        priceCycle(plan) {
            let discount = this.priceDiscount(plan);
            return discount/plan.cycle[this.cycle].months;
        },
        priceDifference(plan) {
            let value = this.price(plan);
            let valueDiscount = this.priceDiscount(plan);
            return value - valueDiscount;
        },
        generateUrlContractNow(plan) {
            let params = {
                a: 'add',
                pid: plan.id,
                billingcycle: this.cycle,
                promocode: this.promoCode
            }
            return '?' + Object.keys(params).map(key => key + '=' + params[key]).join('&');
        }
    }
}
</script>

<style lang="scss">
    .VueCarousel-slide {
        margin-right: 2rem;
    }
    .fa-arrow-circle-right,
    .fa-arrow-circle-left {
        position: relative;
        font-size: 2rem;
        color: $primary-color;
    }
    .fa-arrow-circle-right {
        right: 2rem;
    }
    .fa-arrow-circle-left {
        left: 2rem;
    }
    .plans {
        background: white;
        border-radius: .3rem;
        text-align: center;
        &.plan-m {
            position: relative;
            bottom: .5rem;
            border-top: 8px solid $secondary-color;
            border-bottom: 4px solid $secondary-color;
        }
        .option-plan-header,
        .option-plan-body,
        .option-plan-features {
            padding: 1rem;
        }
        .option-plan-header {
            border-bottom: 2px solid scale-color($color: $primary-color, $lightness: 95%);
            h2 {
                color: $primary-color;
            }
        }
        .option-plan-body {
            border-bottom: 2px solid scale-color($color: $primary-color, $lightness: 95%);
            padding: 2rem 0;
            .price-one {
                font-size: .7rem;
            }
            .price-two {
                .text-xl {
                    font-size: 2rem;
                    font-weight: bold;
                    color: $primary-color;
                }
            }
            .button-action {
                margin: 2rem 0;
                .btn {
                    color: white;
                    padding: .6rem 1rem;
                    border-radius: 50px;
                    text-decoration: none;
                    transition: all .3s linear;
                    &.btn-primary {
                        background: $primary-color;
                        &:hover {
                            background: scale-color($color: $primary-color, $lightness: 10%);
                        }
                    }
                    &.btn-secondary {
                        background: $secondary-color;
                        &:hover {
                            background: scale-color($color: $secondary-color, $lightness: 10%);
                        }
                    }
                }
            }
            .price-three {
                font-size: .8rem;
                .badge-green {
                    background: $green-color;
                    color: white;
                    padding: .3rem .5rem;
                    border-radius: 30px;
                    margin-left: .5rem;
                }
            }
        }
        .option-plan-features {
            text-align: left;
            ul {
                list-style: none;
                padding: 0;
                li {
                    margin-bottom: .5rem;
                }
            }
            .outline {
                border-bottom: 1px dotted scale-color($color: $primary-color, $lightness: 95%);
            }
        }
    }
</style>