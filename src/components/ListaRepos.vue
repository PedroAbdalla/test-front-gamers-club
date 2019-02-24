<template>
    <div class="lista-repos">
        <div class="input-group mb-2 p-0 col-sm-6 col-8 filter">
            <div class="input-group-prepend">
                <span class="input-group-text">
                    <i class="fas fa-search"></i>
                </span>
            </div>
            <input type="text" class="form-control" placeholder="Filter by name" v-model="search">
        </div>
        
        <div class="dados p-0 pt-3 pb-3"
            v-for="d in filteredItems"
            :key="d">
            <div class="col-md-6 col-sm-12 p-0">
                <h4><a href="#">{{d.titulo}}</a></h4>
                <h5>{{d.descricao}}</h5>
                <h5><i class="fas fa-star"></i> {{d.star}} <i class="fas fa-code-branch ml-3"></i> {{d.share}}</h5>
            </div>
        </div>
    </div>
    
</template>

<script>
export default {
    props: ['dado'],
    data() {
        return {
            search: ''
        }
    },
    computed: {
        filteredItems() {
            return this.dado.filter(d => {
                return d.titulo.toLowerCase().indexOf(this.search.toLowerCase()) > -1
            })
        }
    }
}
</script>

<style lang="scss">
@import "../scss/variaveis";
.lista-repos {
    @media screen and (max-width: $break-small) {
        padding: 0 20px;
    }
    .input-group-text {
        color: $warm-grey;
        background: white;
        border-right: none;
    }
    .form-control {
        border-left: none;
        &:focus{
            box-shadow: none;
            border-color: #CCC;
            border-left-color: rgb(204, 204, 204);
        }
    }
    .dados {
        border-bottom: 1px solid $pale-grey;
        h4 {
            font-size: 13pt;
            padding: 0;
        }
        h5 {
            font-size: 11pt;
            padding: 0;
        }
    }
}
</style>
