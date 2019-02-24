<template>
    <div class="perfil col-md-3 col-sm-12">
        <router-link to="/perfil">
            <div class="perfil-foto"></div>
        </router-link>
        <div class="perfil-nome">
            <router-link to="/perfil">
                <div>Pedro Abdalla</div>
            </router-link>
            <div>Front End Dev</div>
        </div>
    </div>
    
</template>

<script>
export default {

}
</script>

<style lang="scss">
    @import "../scss/variaveis";
    .perfil {           
        .perfil-foto {
            width: 150px;
            height: 150px;
            border-radius: 150px;
            margin: 15px auto;
            background: url('../assets/pbperfil.png') no-repeat 60% top/cover;
        }
        .perfil-nome {
            div {
                color: $brownish-grey;
                text-align: center;
                &:first-child {
                    font-weight: bold;
                    columns: $dark-grey;
                }
            }
        }
        @media screen and (max-width: $break-small) {
            display: flex;
            justify-items: center;
            margin-bottom: -35px;
            .perfil-foto {
                margin: 15px 6px !important;
            }
            .perfil-nome {
                display: flex;
                flex-direction: column;
                justify-content: center;
            }
            .perfil-foto {
                width: 90px;
                height: 90px;
                border-radius: 90px;
                margin: 15px auto;
                background: url('../assets/pbperfil.png') no-repeat 60% top/cover;
            }
        }
    }
</style>

