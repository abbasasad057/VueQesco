<template>
    <v-card class="modal-dialog" id="adminmodule">
        <v-flex class="modal-header" id="addfeederhead">
            Admin Module
        </v-flex>
        <v-divider/>
        <v-layout class="modal">
            <v-flex class='tile-col'>
                <v-btn tile class='tile-medium'>
                    <img
                    height="30px" 
                    width="30px" 
                    src='../../../assets/icon-admin-blue.svg'/>
                    <label>Admin Module</label>
                </v-btn>
            </v-flex>
            <v-flex class='tile-col'>
                <v-btn tile class='tile-medium'>
                    <img
                    height="30px" 
                    width="30px" 
                    src='../../../assets/icon-user-blue.svg'/>
                    <label>Users</label>
                </v-btn>
            </v-flex>
            <v-flex class='tile-col'>
                <v-btn tile class='tile-medium'>
                    <img
                    height="30px" 
                    width="30px" 
                    src='../../../assets/icon-feeder-blue.svg'/>
                    <label>Feeders</label>
                </v-btn>
            </v-flex>
        </v-layout>
    </v-card>
</template>
<script>

export default {
    name:'addFeeder',
    components:{
    },
    data:()=>({

    }),
    methods:{
        
    },
    mounted() {

    },
}
</script>
<style scoped>
#adminmodule{
    width: 900px;
    z-index:1000 ;
    position: fixed;
    top: 50%;
    left: 50%;
    -webkit-transform: translate(-40%,-40%);
    transform: translate(-40%, -40%);
}
#adminmodule .modal .tile-col{
    padding: 0px 15px;
    height: 150px;
}
#adminmodule .modal .tile-col .tile-medium{
    width:154px ;
    height: 133px;
    padding:40px 5px;
    margin-left: 50px !important;
    margin: 0px  8px;
    background-color: #FFFF;
    display: block;
}

</style>