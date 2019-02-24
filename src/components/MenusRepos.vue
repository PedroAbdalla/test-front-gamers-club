<template>
    <div class="repositorio col-md-9 col-sm-12 p-0">
        <ul class="menu list-inline">
            <li class="list-inline-item" 
                v-on:click="setActive('repos'), switchComponent('lista-repos')"
                :class="{ active: isActive('repos') }">
                <div>
                    <span>Repos</span> 
                    <div class="bolinha">{{ repos.length }}</div>
                </div>
            </li>
            <li class="list-inline-item" 
                v-on:click="setActive('starred'), switchComponent('lista-starred')"
                :class="{ active:isActive('starred') }">
                <div>
                    <span>Starred</span> 
                    <div class="bolinha">{{ starred.length }}</div>
                </div>
            </li>
        </ul>
        <!-- <component :is="currentComp" :dado="dados"></component> -->
        <lista-repos :dado="dados"></lista-repos>
    </div>
</template>

<script>
import ListaRepos from './ListaRepos.vue';
export default {
    data() {
        return {
            // currentComp: 'lista-repos',
            activeItem: 'repos',
            repos: [],
            starred: [],
            dados: []
        }
    },
    methods: {
        isActive: function (menuItem) {
            return this.activeItem === menuItem
        },
        setActive: function (menuItem) {
            this.activeItem = menuItem 
        },
        switchComponent: function (comp) {
            this.dados = (comp == 'lista-repos') ? this.repos : this.starred
            // this.currentComp = comp 
        },
    },
    mounted: function () {
        let meuThis = this
        $.ajax({
            type: "GET",
            url: "http://localhost:3000/dados",
            dataType: "json",
            async: true,
            success: function (retorno) {
               meuThis.repos = retorno.repos
               meuThis.starred = retorno.starred
               meuThis.switchComponent('lista-repos')
            }
        })
    },
    components: {
        'listaRepos': ListaRepos
    }
}
</script>
<style lang="scss">
    @import "../scss/variaveis";
    .repositorio {
        color: $slate-grey-two;
        .menu.list-inline {
            border-bottom: 2px solid $white-two;
            margin-top: 30px;
            li {
                margin: 20px;
                cursor: pointer;
                &:nth-child(2) {
                    &:after {
                        content: "";
                        transition: all .2s ease;
                        border-bottom: 4px solid $rusty-orange;
                        width: 120px;
                        position: absolute;
                        top: 93px;
                        left: 0;
                    }
                }
                div {
                    display: flex;
                    .bolinha {
                        background-color: #d8d8d8;
                        color: $slate-grey-two;
                        border-radius: 23px;
                        width: 23px;
                        height: 23px;
                        align-items: center;
                        justify-content: center;
                        font-size: 10pt;
                        font-weight: initial;
                        margin-left: 10px;
                    }
                }
            }
            li.active {
                font-weight: bold;                
                &:nth-child(2) {
                    &:after {
                        width: 130px;
                        left: 119px;
                    }
                }
            }
        }
    }
</style>