<template>
    <form class="form-inline ml-3">
        <div class="input-group input-group-sm">
            <input class="form-control form-control-navbar" @keyup="searchit" v-model="search" type="search" placeholder="Search"
            aria-label="Search">
            <div class="input-group-append">
                <button class="btn btn-navbar" @click="searchit">
                    <i class="fa fa-search"></i>
                </button>
            </div>
        </div>
    </form>
</template>

<script>

export default{
    neme: 'Search',
    // data: function(){
    //     search: ''
    // },
    methods:{
        searchit(){
            console.log("searching. .");
        }
    }
}
</script>
