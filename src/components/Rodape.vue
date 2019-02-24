<template>
    <div class="row footer col-12">
        <div class="col-md-9 col-xs-12">
            <button>
                <i class="fas fa-download"></i>
                Download Gamers Club Anti-Cheat
            </button>
        </div>
        <div class="col-md-3 col-xs-12">
            <div class="row">
                <div class="col-6 status">
                    <div class="jogadores jogadores-online">{{online}}</div>
                    <div class="texto-info">
                        Jogadores
                        <span>Online</span>
                    </div>
                </div>
                <div class="col-6 status">
                    <div class="jogadores jogadores-banidos">{{banidos}}</div>
                    <div class="texto-info texto-info--banidos">
                        Cheaters Banidos
                        <span>Nos Últimos 7 Dias</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    props: ['online', 'banidos'],
}
</script>
<style lang="scss">
    .footer {
        padding: 5px 0;
        border-top: 1px solid #333548;
        button {
            font-size: 11pt;
            padding: 3;
            background-color: rgba(255, 255, 255, 0.06);
            color: #b6b8c6;
            border: none;
            font-family: 'Poppins', sans-serif;
        }
        .status {
            display: flex;
            .jogadores {            
                font-size: 16pt;
                line-height: 23px;
            }
            .texto-info {
                width: 46px;
                color: white;
                font-size: 7pt;
                line-height: 10px;
                margin: 1px 3px;
                span {
                    color: #2c97de;
                }
            }
            .jogadores-online {
                color: #2c97de;
            }           
            .jogadores-banidos {
                color: #eb2f2f;
            }
            .texto-info--banidos {
                width: 55px;
                span {
                    color: #eb2f2f;
                }
            }
        }
    }
</style>
