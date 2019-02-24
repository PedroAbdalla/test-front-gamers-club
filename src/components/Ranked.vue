<template>
    <div>
        <div class="titulo">
            <svg-open class=" t-ranked"></svg-open> <span class="ml-1  t-ranked">RANKED OPEN</span>
        </div>
        <div class="row historico">
            <div class="col-4 p-0 pl-1">
                <div class="historico-numeros p-1">
                    <div class="numero n-partidas">{{ranked.matches}}</div>
                    <div>PARTIDAS</div>
                </div>
            </div>
            <div class="col-4 p-0 pl-1">
                <div class="historico-numeros p-1">
                    <div class="numero n-vitorias">{{ranked.win}}</div>
                    <div>VITORIAS</div>
                </div>
            </div>
            <div class="col-4 p-0 pl-1">
                <div class="historico-numeros p-1">                
                    <div class="numero n-derrotas">{{ranked.lose}}</div>
                    <div>DERROTAS</div>
                </div>
            </div>
            <div class="col-12 p-0">
                <a :href="ranked.cta.link">
                    <button class="button-ranked">
                        <i class="fas fa-users"></i> {{ranked.cta.line}} |
                        {{ranked.cta.title}}
                    </button>
                </a>
            </div>
        </div>
    </div>
</template>
<script>
import SvgOpen from './svgs/Open.vue'
export default {
    props: ['ranked'],
    components: {
        svgOpen: SvgOpen
    },
}
</script>
<style lang="scss">
    .t-ranked {
       position: relative;
       top: 7px;
    }
    .button-ranked {
        background-color: #2c97de !important;
        background-image: linear-gradient(180deg, rgba(255, 255, 255, 0.25) 0%, rgba(255, 255, 255, 0) 100%) !important;
    }
</style>
