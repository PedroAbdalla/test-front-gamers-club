<template>
    <div>
        <div class="titulo">
            <svg-lobby></svg-lobby> <span class="ml-1">LOBBY</span>
        </div>
        <div class="row historico">
            <div class="col-4 p-0 pl-1">
                <div class="historico-numeros p-1">
                    <div class="numero n-partidas">{{games.matches}}</div>
                    <div>PARTIDAS</div>
                </div>
            </div>
            <div class="col-4 p-0 pl-1">
                <div class="historico-numeros p-1">
                    <div class="numero n-vitorias">{{games.win}}</div>
                    <div>VITORIAS</div>
                </div>
            </div>
            <div class="col-4 p-0 pl-1">
                <div class="historico-numeros p-1">                
                    <div class="numero n-derrotas">{{games.lose}}</div>
                    <div>DERROTAS</div>
                </div>
            </div>
            <div class="col-12 p-0">
                 <a :href="games.cta.link">
                    <button class="button-games">
                        {{games.cta.title}}
                    </button>
                </a>
            </div>
        </div>
    </div>
</template>
<script>
import SvgLobby from './svgs/Lobby.vue'
export default {
    props: ['games'],
    components: {
        svgLobby: SvgLobby
    },
}
</script>
<style lang="scss">
    .historico{
        .historico-numeros {
            height: 122px;
            background-image: linear-gradient(180deg, rgba(238, 238, 238, 0.1) 0%, rgba(255, 255, 255, 0) 100%);
            color: white;
            .numero {
                font-size: 30pt;
                height: 40px;
            }
            .n-partidas {
                color: #ddbc39;
            }
            .n-vitorias {
                color: #92aa00;
            }
            .n-derrotas {
                color: #fc3537;
            }
        }
        button {
            width: 100%;
            box-shadow: 0 6px 6px -3px rgba(0, 0, 0, 0.25), inset 0 1px 0 rgba(255, 255, 255, 0.25);
            border-radius: 2px;
            background-color: #ddbc39;
            background-image: linear-gradient(180deg, rgba(255, 255, 255, 0.25) 0%, rgba(255, 255, 255, 0) 100%);
            border: none;
            color: white;
            padding: 5px;
            text-transform: uppercase;
        }
    }
</style>
