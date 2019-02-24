<template>
    <div class="row cabecalho"> 
        <div class="col-md-3 col-sm-12  menu menu-usuario">
            <div class="perfil-foto"></div>
            <div class="perfil-dados">
                <div>{{usuario.name}}</div>
                <div>GC ID: {{usuario.id}}</div>
            </div>
        </div>
        <div class="col-md-6 col-sm-12  menu-range">
            <div class="row">
                <div class="col-3 text-right pr-0">
                    <span class="patente">CASUAL</span>
                    <svg-pin rotate='180' active="casual" :expertise="usuario.expertise"></svg-pin>
                </div>
                <div class="col-3 offset-3 text-right pr-0">
                    <span class="patente">AMADOR</span>
                    <svg-pin rotate='180' active="amador" :expertise="usuario.expertise"></svg-pin>
                </div>
            </div>
            <div class="progress" style="height: 14px;">
                <div class="progress-bar" role="progressbar" :style="{ width: progressWidth }" aria-valuenow="25" aria-valuemin="0" aria-valuemax="100"></div>
            </div>
            <div class="row">
                <div class="col-3 offset-3 text-right pr-0">
                    <span class="patente">COMPETITIVO</span>
                    <svg-pin rotate='0' active="competitivo"  :expertise="usuario.expertise" ></svg-pin>
                </div>
                <div class="col-3 offset-3 text-right pr-0">
                    <span class="patente">PRO</span>
                    <svg-pin rotate='0' active="pro" :expertise="usuario.expertise" ></svg-pin>
                </div>
            </div>
        </div>
        <div class="col-md-3 col-sm-12 menu menu-config pr-0">
            <div class="icone quadro">
                <img alt="icone" src="../assets/icone.png">
            </div>
            <div class="beginner quadro">
                <svg-beginner></svg-beginner>
            </div>
            <div class="patent quadro">
                <img alt="patent" :src="usuario.patent" width="30">
            </div>
            <div class="level quadro">
                <span>{{usuario.level}}</span>
            </div>
            <div class="escudo quadro">
             <img alt="icone" src="../assets/escudo.png">
            </div>
            <!-- <div class="molde quadro">
                <span>1</span>
            </div> -->
        </div>
    </div>
</template>
<script>
import SvgPin from './svgs/Pin.vue'
import SvgBeginner from './svgs/Beginner.vue'
export default {
    props: ['usuario'],
    data() {
        return {
            tamanha: 0
        }
    },
    components: {
        svgPin: SvgPin,
        svgBeginner: SvgBeginner
    },
    computed: {
        progressWidth: function () {
            if(this.usuario.expertise == 'casual') {
                this.tamanho = '25%'
            }
            if(this.usuario.expertise == 'competitive') {
                this.tamanho = '50%'
            }
            if(this.usuario.expertise == 'amateur') {
                this.tamanho = '75%'
            }
            if(this.usuario.expertise == 'pro') {
                this.tamanho = '100%'
            }
            $('.progress div').css('width', '50%')
            return this.tamanho
        }
    }
}
</script>

<style lang="scss">
@import "../scss/variaveis";
    .cabecalho {
        color: white;
        height: 93px;
        background-color: #272940;
        box-shadow: 0 8px 16px -4px rgba(0, 0, 0, 0.5);
        background: url('../assets/background-menu.png') no-repeat 60% top/cover;
        @media screen and (max-width: $break-small) {
            height: 260px;
        }
        @media screen and (max-width: $break-xl) {
            height: 305px;
        }
        .menu {
            display: flex;
            align-items: center;        
            .perfil-foto {
                width: 50px;
                height: 50px;
                min-width: 50px;
                border-radius: 50px;
                border: 2px solid #95b200;
                background: url('../assets/pbperfil.png') no-repeat 60% top/cover;
            }
            .perfil-dados {                
                flex-direction: column;
                align-items: start;
                margin-left: 10px;
                font-family: "Poppins";
                font-size: 9pt;
                div:nth-child(2){
                    color: #7c7da3;
                }
            }
            .escudo {
                height: 100%;
                background-image: radial-gradient(circle 58px at 1813.86% 187.59%, #19f3ff 0%, #3883db 100%);
                margin: -1px;
                img {
                    margin: 20px 15px;
                }
            }
        }
        .menu-config {
            display: flex;
            flex: 1;
            justify-content: space-between;
            @media screen and (min-width: $break-large) {
                height: 100%;
            }
            .quadro {
                text-align: center;
            }
            .level {
                border: 2px solid #46485b;
                width: 35px;
                max-width: 35px;
                height: 35px;
                border-radius: 45px;
                text-align: center;
                padding: 4px;
            }
            .molde {
                height: 100%;
                background: radial-gradient(circle 58px at 1813.86% 187.59%, #19f3ff 0%, #3883db 100%);
            }
        }
        .menu-range {
            margin: 15px auto;
            font-size: 10pt;
            .patente {
                margin: 3px;
                position: relative;
                top: 3px;
            }
            .progress {
                border-radius: 7px;
                .progress-bar {
                    background-image: linear-gradient(to right, #5c3abd 0%, #77dbff 100%);
                }
            }
        }
    }
</style>