<template>
    <v-card class="modal-dialog" id="print">
        <v-flex class="modal-header" id="printhead">
            Print
        </v-flex>
        <v-divider/>
        <v-flex class="modal">
            <v-container class='modal-body'>
                <div class='row'>
                    <div class="label">Page Size</div>
                    <v-combobox
                        :items="pageSize"
                        label="Select Page Size"
                        outlined
                        dense
                        class="modal-control"
                    ></v-combobox>
                </div>
                <div class='row'>
                    <v-radio-group row>
                        <v-radio
                            color=#0885fb
                            label="Landscape"
                        ></v-radio>
                        <v-radio
                            color=#0885fb
                            label="Potrait"
                        ></v-radio>
                    </v-radio-group>
                </div>
                <div class='row'>
                    <div class="label">Title</div>
                    <v-text-field
                        label="Title.."
                        outlined
                        dense
                        class="modal-control"
                    ></v-text-field>
                </div>
                <v-layout justify-center>
                <v-btn class='modal-button primary'>
                    Print
                </v-btn>
                </v-layout>
            </v-container>  
        </v-flex>
    </v-card>
</template>
<script>
import {pageSize} from './print.json';
export default {
    name:'print',
    components:{
    },
    data:()=>({
        pageSize,
    })
}
</script>
<style>
#print{
    width: 400px;
    z-index:1000 ;
    position: fixed;
    top: 50%;
    left: 50%;
    -webkit-transform: translate(-40%,-40%);
    transform: translate(-40%, -40%);
}

#print .modal .modal-control{
    border-radius: 0%;
}
</style>