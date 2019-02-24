<template>
<div id="app">
    <div class="conteudo">
        <app-cabecalho :usuario="dados.user"></app-cabecalho>
        <div class="row">
            <div class="col-md-6 col-sm-12 fun pb-2">
                <app-fun :fun="dados['4fun']"></app-fun>
            </div>
            <div class="col-md-3 col-sm-12 lobby pb-2">
                <app-lobby :games="dados.games[0]"></app-lobby>
            </div>
            <div class="col-md-3 col-sm-12 ranked pb-2">
                <app-ranked :ranked="dados.games[1]"></app-ranked>
            </div>
            <app-rodape :online="dados.online" :banidos="dados.latest_banned"></app-rodape>
        </div>
    </div>
</div>
</template>
<script>
import Cabecalho from './components/Cabecalho.vue'
import Fun from './components/Fun.vue'
import Lobby from './components/Lobby.vue'
import Ranked from './components/Ranked.vue'
import Rodape from './components/Rodape.vue'
export default {
    data() {
        return {
            dados: []
        }
    },
    components: {
        appCabecalho: Cabecalho,
        appFun: Fun,
        appLobby: Lobby,
        appRanked: Ranked,
        appRodape: Rodape
    },
    methods: {        
        setDados: function (retorno) {
            this.dados = retorno
        },
    },
    mounted() {
        let meuThis = this
        $.ajax({
            type: "GET",
            url: "https://api.myjson.com/bins/sqwaq",
            dataType: "json",
            async: true,
            success: function (retorno) {
               meuThis.setDados(retorno)
            }
        })
    }
}
</script>

<style lang="scss">
.row {
    margin: 0px;
}    
body {
    background: url('./assets/bitmap.png') no-repeat 60% top/cover;
    height: 100vh
}
#app {
    font-family: Teko;
    max-width: 1600px;
    margin: auto 20px;
    .conteudo {
        border: 1px solid #333548;
        margin-top: 87px !important;
        background-color: #27293c;
        .topo {
            background-color: #24292e;
            padding: 6px 10px;
            color: white;
            display: flex;
            align-items: center;
            img {
                margin-right: 5px; 
            }
        }
    }
    .lobby {
        border: 1px solid #333548;
        border-top: 0;
        border-bottom: 0;
    }
    .titulo {
        color: white;
        font-size: 13pt;
        height: 50px;
    }
}
</style>
