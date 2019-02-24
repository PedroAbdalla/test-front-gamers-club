<template>
    <div>
        <div class="titulo">
            <svg-fun></svg-fun> <span class="mt-3 ml-1 t-fun">4 FUN</span>
        </div>
        <div class="row" style="border: 2px solid">
            11111111
        </div>
    </div>
</template>
<script>
import SvgFun from './svgs/4Fun.vue'
export default {
    components: {
        svgFun: SvgFun
    },
}
</script>
<style lang="scss">
    .titulo {
        .t-fun {
            position: relative;
            top: 5px
        }
    }
</style>
