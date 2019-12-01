<template>
  <section id="banner">
      <div class="container">
          <div class="row">
              <div class="col-12">
                  <div class="content-text">
                    <div class="mini-title">{{ miniTitle }}</div>
                    <h1 class="title">{{ title }}</h1>
                    <div class="options-text">
                        <span v-for="o in optionsText" :key="o.id"><i class="fas fa-check"></i> {{ o }}</span>
                    </div>
                  </div>
              </div>
          </div>
      </div>
  </section>
</template>

<script>
export default {
    data() {
        return {
            miniTitle: 'Hospedagem de Sites',
            title: 'Tenha uma hospedagem de sites estável e evite perder visitantes diariamente',
            optionsText: [
                '99,9% de disponibilidade: seu site sempre no ar',
                'Suporte 24h todos os dias',
                'Painel de controle cPanel'
            ]
        }
    }
}
</script>

<style lang="scss">
    #banner {
        position: relative;
        height: 460px;
        &:before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url(../assets/bg-feature.svg);
            //background-position: center;
            //background-repeat: no-repeat;
            //background-size: cover;
            z-index: -3;
        }
        .container {
            height: 100%;
        }
    }
    .content-text {
        text-align: center;
        width: 100%;
        position: absolute;
        top: calc(50% - 15px);
        left: 0;
        transform: translateY(-50%);
        color: white;
        .title,
        .options-text {
            display: inline-block;
            width: 60%;
        }
        .mini-title {
            color: lighten($primary-color, 50%);
        }
        .options-text span {
            color: lighten($primary-color, 50%);
            margin-right: .8rem;
            &.last-child {
                margin-right: 0
            }
        }
    }
</style>