<template>
    <div class="home">
        <div class="row">
            <QuadroPerfil />
            <MenusRepos />
        </div>
    </div>
</template>
<style lang="scss">
    .row {
        margin: 0px;
    }    
</style>

<script>
// @ is an alias to /src
import QuadroPerfil from '@/components/QuadroPerfil.vue';
import MenusRepos from '@/components/MenusRepos.vue';

export default {
name: 'home',
    components: {
        QuadroPerfil,
        MenusRepos,
    },
};
</script>
