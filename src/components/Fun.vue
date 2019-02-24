<template>
    <div>
        <div class="titulo row" style="display: flex">
            <div class="col-3 pl-0">
                <svg-fun></svg-fun> <span class="ml-1 mt-1 t-fun">4 FUN</span>
            </div>
            <div class="col-9 lista-server p-0">
                <div class="menu-fun"                     
                    v-for="index in numeroGrupo" :key="index" 
                    :data-grupo="index" 
                    :class="{actived: verificaAtivo(index)}"
                    @click="ativo = index"
                    ></div>
            </div>
        </div>
        <div class="row lista-mapas">
            <div class="mapas m-1"
                v-for="(sv, index) in fun.servers" 
                :key="index" 
                :class="'grupo-'+Math.ceil((index+1)/3)"
                v-show="Math.ceil((index+1)/3) == ativo" >
                <div class="topo-mapa">
                    <button class="file m-1 mt-2 ml-2" @click.stop.prevent="copyTestingCode(index)">
                        <i class="far fa-copy"></i>
                        <input type="hidden" :id="'testing-code-'+index" :value="sv.copy">
                    </button>
                    <a :href="sv.join">
                        <button class="sign m-1 mt-2">
                        <i class="fas fa-sign-in-alt"></i>
                        </button>
                    </a>
                </div>
                <div class="ml-2 nome-mapa">#{{sv.id}} - {{sv.title.substring(0,35)}}<span v-if="sv.title.length >35" :title="sv.title">...</span></div>
                <div class="ml-2 mode-mapa">#{{sv.mode}}</div>
                <div class="online-map m-1 ml-2 mr-2">
                    <div class="map-info row">
                        <div class="col-9 p-0 titulo-mapa">{{sv.map}}</div>
                        <div class="col-3 p-0 text-right">{{sv.current}}/{{sv.max}}</div>
                    </div>
                    <div class="progress" style="height: 14px;">
                        <div class="progress-bar" role="progressbar" :style="{ width: (sv.current*100/sv.max) +'%' }" aria-valuenow="25" aria-valuemin="0" aria-valuemax="100"></div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import SvgFun from './svgs/4Fun.vue'
export default {
    props: ['fun'],
    data() {
        return {
            grupo: 1,
            ativo: 1,
            boi: true
        }
    },
    components: {
        svgFun: SvgFun
    },
    methods: {
        verificaAtivo(index) {
            return index == this.ativo ?  true :false
        },
        copyTestingCode(id) {
            let testingCodeToCopy = document.querySelector('#testing-code-'+id)
            testingCodeToCopy.setAttribute('type', 'text')
            testingCodeToCopy.select()

            try {
                var successful = document.execCommand('copy');
                var msg = successful ? 'Sucesso' : 'unsuccessful';
                alert('Testing code was copied ' + msg);
                testingCodeToCopy.setAttribute('type', 'hidden')
            } catch (err) {
                alert('Oops, unable to copy');
            }
        }
    },
    computed: {
        numeroGrupo() {
            return Math.ceil(this.fun.servers.length/3)
        }
    }
}
</script>
<style lang="scss">
    .titulo {
        .t-fun {
            position: relative;
            top: 5px;
        }
        .lista-server {
            display: flex;
            justify-content: flex-end;
            align-items: flex-end;
            .menu-fun {
                background-color: rgba(255, 255, 255, 0.1);
                height: 3px;
                width: 27px;
                margin-bottom: 14px;
                margin-left: 10px;
                cursor: pointer;
            }
            .menu-fun.actived{
                background-color: rgb(255, 255, 255);
            }
        }
    }
    .lista-mapas {
        display: flex;
        .mapas {
            display: flex;
            flex-direction: column;
            flex: 1;
            background: url('../assets/mapa.png') no-repeat 60% top/cover;
            height: 151px;
            border: 1px solid #333548;
            box-shadow: 0 8px 16px -4px rgba(0, 0, 0, 0.5);
            color:white;
            .topo-mapa {
                button {
                    font-size: 10pt;
                    padding: 3px 5px 0;
                    border-radius: 2px;
                    border: none;
                    color: white;
                }
                .file {
                    box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1), inset 0 0 0 1px rgba(255, 255, 255, 0.05), inset 0 1px 0 rgba(255, 255, 255, 0.1);
                    background-color: rgba(255, 255, 255, 0.05);
                }
                .sign {
                    background-color: #95b200;
                    box-shadow: 0 1px 2px rgba(0, 0, 0, 0.5), inset 0 0 0 1px rgba(255, 255, 255, 0.1), inset 0 1px 0 rgba(255, 255, 255, 0.25);
                }
            }
            .nome-mapa {
                font-family: 'Poppins', sans-serif;
                font-size: 9pt;
                min-height: 40px;
            }
            .mode-mapa {
                font-family: 'Poppins', sans-serif;
                text-transform: uppercase;
                font-size: 10pt
            }
            .online-map {
                height: 100%;
                .titulo-mapa {
                    overflow: hidden;
                    text-overflow: ellipsis;
                }
                .progress {
                    border-radius: 4px;
                    background: transparent;
                    border: 1px solid rgba(255, 255, 255, 0.25);
                    .progress-bar {
                        background-image: linear-gradient(270deg, rgba(255, 255, 255, 0.25) 0%, rgba(255, 255, 255, 0) 100%);
                        background-color: #2c97de;

                    }
                }
            }
        }
    }
</style>
